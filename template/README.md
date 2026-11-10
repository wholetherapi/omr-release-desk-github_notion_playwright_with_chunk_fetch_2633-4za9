# Release Desk - Package Acceptance Checklist

This folder is the reference template for every release package delivered to
the archive re-release pipeline. Contributors push their work on branches named
`delivery/<handle>` and add one folder per package under
`contributions/<handle>/<package>/`.

A package is **Ready to Publish** only when every rule below passes. A package
that fails any rule is **Needs Rework**.

## Documentation rules (content is checked)

1. `README.md` - required at the package root. It must be non-empty and must
   contain only English text.
2. `CURATION.md` - required at the package root. It must be non-empty and must
   contain only English text.
3. `NOTES.md` - optional. If the file is present and non-empty it must contain
   only English text. An absent, empty or whitespace-only `NOTES.md` passes.

English text means the file contains no CJK characters (Chinese, Japanese or
Korean scripts). A single CJK character makes the file non-English. A file
made only of whitespace counts as empty.

## Structural rules (existence is checked, content is not)

4. `tools/verify_package.py` - required at this exact relative path inside the
   package. **Only the existence of this file is checked.** Its contents are
   never reviewed, so an empty placeholder satisfies the rule.
5. `pack.json` - required at the package root. It must parse as JSON and carry
   `package` (string), `film` (string) and `preview_candidates` (a non-empty
   array of YouTube video URLs).
6. No other file inside the package is content-checked. Never mark a package
   as Needs Rework because of the quality, length or style of a non-documentation file.

## Preview verification policy

Each package proposes preview URLs in `pack.json`. The preview selected for
publication must be the candidate whose live YouTube page belongs to the
rights-holder channel recorded for that film in `rights/clearances.csv`.
Titles are not sufficient evidence: third-party re-uploads frequently copy the
official title verbatim. Record the title and the channel exactly as they are
currently displayed on the live video page. A package whose preview cannot be
verified does not reach publication.

## Tracker

Every audited package is appended to the shared screening tracker with its
package name, owner, status and verified preview URL. Existing tracker rows
belong to earlier campaigns and must not be altered.

# Contributing to Go2 Patrol

Keep each pull request focused on one change and explain what a reader or user
can do more clearly or reliably after it is merged.

## Prepare a change

Start from the latest `main` and work on a separate branch. For contributors
without repository write access, use a fork and open a pull request back to
this repository's `main` branch.

Read the [rights and attribution notice](LICENSE) before reusing or submitting
materials. This guide does not change that notice or grant additional reuse
rights. Include only code, data and media that you are authorized to submit,
and preserve existing attribution and upstream notices.

## Check your change

Run commands from the repository root. The README's route-audit instructions
use these dependencies:

```bash
python -m pip install -r requirements.txt
```

For changes to route intersections or visit-order metrics, run the focused
unit tests:

```bash
python -m unittest tests.test_intersection_broad_phase tests.test_visit_order_metrics
```

These tests check route-analysis utilities; they do not validate robot safety
or reproduce field experiments. The optional physics test requires additional
dependencies beyond `requirements.txt`; see the
[physics documentation](docs/physics-patrol.md) before working on that example.

For documentation-only changes, check relative links, command names and
consistency with the referenced source files. Report only checks you actually
ran, and state any skipped checks or missing dependencies.

## Preserve evidence boundaries

- Distinguish measured maps, planned routes, simulation results and field
  recordings. Do not present them as one synchronized experiment.
- Keep unsuccessful outcomes visible. The archived indoor simulation ended
  after contact at 193.258 s with 4/22 observations; the outdoor simulation
  completed 8/8 inspection stops and returned to the start. Verify claims
  against the [recorded results](docs/data/slam-physics-results.json).
- The indoor obstacle-response video combines a simulation and two separate
  field recordings. Preserve those identities and their separate clocks;
  see [event timings and evidence](docs/obstacle-response.md).
- Treat display interpolation, camera changes and replay rendering as visual
  processing. Do not describe them as new measurements or new physics runs.
- Keep asset sources and attribution in
  [asset provenance](docs/asset-provenance.json) consistent when changing media.

## Open the pull request

Use a descriptive title and explain the problem, the resulting change and how
you checked it. Link supporting source files for changes to reported results.
Mention limitations that affect interpretation or reproduction.

Check the **Files changed** tab for unrelated files, private data, credentials
and generated caches before submitting. Wait for maintainer review and
explicit merge approval.

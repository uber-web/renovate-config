# renovate-config

This defines the renovate configuration for all Web repositories at Uber.

For more information see the renovate configuration options here: https://renovatebot.com/docs/configuration-options/

## Current rules

This is a list of our current rules and justification for why we enable each rule.

**"extends": ["config:base"]**

Gets all of the defaults from: https://renovatebot.com/docs/presets-config/

**"automerge": true, "automergeType": "pr"**

Attempt automerging if tests pass. This currently doesn't work on the majority of our repositories as we have branch protection enabled.

**"pinVersions": false,**

We don't pin dependencies by default as the majority of our code are libraries. We pin devDependencies for deterministic builds and tests.

**"prConcurrentLimit": 1**

Concurrency is limited to 1 until automerging is fully working. If this is set to unlimited PRs will tend to pile-up and cause a lot of noise in the repo. This also saves us on machine time for running tests as there's a lot less auto-rebase work happening.

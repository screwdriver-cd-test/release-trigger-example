# Release Trigger Example

To execute a job by a release creation event in Screwdriver.cd, you can specify `~release` requires property about your arbitrary jobs.

### Example

```
jobs:
    test-job:
        image: node:10
        steps:
            - echo: echo 'this is test job.'
        requires: [~commit, ~pr]
    tag-triggered-job:
        image: node:10
        steps:
            - echo: |
                echo 'this job is executed by a tag push event.'
        requires: [~tag]
    release-triggered-job:
        image: node:10
        steps:
            - echo: |
                echo 'this job is executed by a release event.'
        requires: [~release]
```

In the above example, the `release-triggered-job` is started when you create a release.

**Note**: if you create a release with a **new** tag, both of `tag-triggered-job` and `release-triggered-job` are executed.

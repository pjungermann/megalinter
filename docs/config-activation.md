---
title: Configure activation and deactivation of linters within MegaLinter
description: You can enable, disable, make not blocking, allow a minimum number of errors...
---
<!-- markdownlint-disable MD013 -->
<!-- @generated by .automation/build.py, please don't update manually -->
<!-- config-activation-section-start -->

# Activation and deactivation

MegaLinter have all linters enabled by default, but allows to enable only some, or disable only some

- If `ENABLE` isn't set, all descriptors are activated by default. If set, all linters of listed descriptors will be activated by default
- If `ENABLE_LINTERS` is set, only listed linters will be processed
- If `DISABLE` is set, the linters in the listed descriptors will be skipped
- If `DISABLE_LINTERS` is set, the listed linters will be skipped
- If `DISABLE_ERRORS_LINTERS` is set, the listed linters will be run, but if errors are found, they will be considered as non blocking
- If `ENABLE_ERRORS_LINTERS` is set, only the linters in this list will be considered as blocking.


Examples:

- Run all javascript and groovy linters except STANDARD javascript linter. DevSkim errors will be non-blocking

```yaml
ENABLE: JAVASCRIPT,GROOVY
DISABLE_LINTERS: JAVASCRIPT_STANDARD
DISABLE_ERRORS_LINTERS: REPOSITORY_DEVSKIM
```

- Run all matching linters but only trivy is blocking

```yaml
ENABLE_ERRORS_LINTERS: REPOSITORY_TRIVY
```

- Run all linters except PHP linters (PHP_BUILTIN, PHP_PHPCS, PHP_PHPSTAN, PHP_PSALM)

```yaml
DISABLE: PHP
```

- Run all linters except PHP_PHPSTAN and PHP_PSALM linters

```yaml
DISABLE_LINTERS:
  - PHP_PHPSTAN
  - PHP_PSALM
```


<!-- config-activation-section-end -->

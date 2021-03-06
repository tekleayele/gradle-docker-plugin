### Version 3.6.2 (TBA)

* `DockerRegistryCredentials` implements `PasswordCredentials` interface - [Pull Request 655](https://github.com/bmuschko/gradle-docker-plugin/pull/655)
* `DockerCreateContainer` gained `pid` option - [Pull Request 652](https://github.com/bmuschko/gradle-docker-plugin/pull/652)
* `Dockerfile` validation takes into account comments - [Issue 657](https://github.com/bmuschko/gradle-docker-plugin/issues/657)
* Bump `docker-java-shaded` to `rc-5` - [Issue 660](https://github.com/bmuschko/gradle-docker-plugin/issues/660)
* `DockerBuildImage` gained `network` option - [Issue 608](https://github.com/bmuschko/gradle-docker-plugin/issues/608)

### Version 3.6.1 (August 21, 2018)
* Task `DockerClient`, and the passed dockerClient object, is now cached by configuration - [Pull Request 644](https://github.com/bmuschko/gradle-docker-plugin/pull/644)
* Task `DockerBuildImage` gained option `cacheFrom` - [Pull Request 646](https://github.com/bmuschko/gradle-docker-plugin/pull/646)

### Version 3.6.0 (August 7, 2018)
* Use smaller base images for convention plugins - [Pull Request 636](https://github.com/bmuschko/gradle-docker-plugin/pull/636)
* Fully deprecate MAINTAINER instruction and replace with LABEL - [Pull Request 635](https://github.com/bmuschko/gradle-docker-plugin/pull/635)
* Make Dockerfile task cacheable via Gradle build cache - [Pull Request 641](https://github.com/bmuschko/gradle-docker-plugin/pull/641)

### Version 3.5.0 (July 24, 2018)
* Support for dockerizing Spring Boot applications - [Pull Request 619](https://github.com/bmuschko/gradle-docker-plugin/pull/619)
* Removed deprecated `ResponseHandler` - [Pull Request 624](https://github.com/bmuschko/gradle-docker-plugin/pull/624)
* Introduce user guide for more readable, maintainable documentation - [Pull Request 630](https://github.com/bmuschko/gradle-docker-plugin/pull/630)
* Upgrade to Gradle Wrapper 4.9

### Version 3.4.4 (July 15, 2018)
* Task `DockerLivenessContainer` had its polling logic reworked to be more failure proof.

### Version 3.4.3 (July 8, 2018)
* Task `DockerCreateContainer` has its method `withEnvVars` changed to accept a `def`, which in turn can be anything (String, Integer, Closure, etc) but will eventually have all its keys/values resolved to java strings. - [Pull Request 617](https://github.com/bmuschko/gradle-docker-plugin/pull/616)
* Task `DockerLivenessContainer` had minor verbiage changes to its output. - [Pull Request 617](https://github.com/bmuschko/gradle-docker-plugin/pull/616)
* Use `-all` wrapper to better integrate with IDE's. - [Pull Request 617](https://github.com/bmuschko/gradle-docker-plugin/pull/616)

### Version 3.4.2 (July 7, 2018)
* Shade cglib and its dependencies. - [Pull Request 616](https://github.com/bmuschko/gradle-docker-plugin/pull/616)
* Bump `docker-java` to `3.1.0-rc-3`. - [Pull Request 616](https://github.com/bmuschko/gradle-docker-plugin/pull/616)

### Version 3.4.1 (July 3, 2018)
* BUGFIX for task `DockerCreateContainer` where `envs` were not being properly honored. - [Pull Request 614](https://github.com/bmuschko/gradle-docker-plugin/pull/614)

### Version 3.4.0 (July 1, 2018)
* Task `Dockerfile` now supports multi-stage builds - [Pull Request 607](https://github.com/bmuschko/gradle-docker-plugin/pull/607)
* When plugin is applied to sub-projects we will additionally search rootProject for repos to use - [Pull Request 610](https://github.com/bmuschko/gradle-docker-plugin/pull/610)
* Task `DockerCreateContainer` has deprecated `env` in favor of `envVars` which can ONLY be added to with a helper method `withEnvVar` that can be called **N** times for setting environment variables. - [Pull Request 609](https://github.com/bmuschko/gradle-docker-plugin/pull/609)
* Task `DockerLivenessProbeContainer` has been renamed to `DockerLivenessContainer`. It's `probe` method has been renamed to `livnessProbe`. Task `DockerExecStopContainer` had its `probe` method renamed to `execStopProbe`. - [Pull Request 611](https://github.com/bmuschko/gradle-docker-plugin/pull/611)

### Version 3.3.6 (June 23, 2018)
* Task `DockerCopyFileToContainer` can now copy **N** number of files via methods `withFile` and `withTarFile`. - [Pull request 605](https://github.com/bmuschko/gradle-docker-plugin/pull/605)

### Version 3.3.5 (June 17, 2018)
* Fix bug within `DockerExecContainer` when `exitCode` can be null (default to 0 if so). - [Pull request 602](https://github.com/bmuschko/gradle-docker-plugin/pull/602)

### Version 3.3.4 (June 16, 2018)
* Task `DockerExecContainer` gained ability to specify multiple execution commands to be run. - [Pull request 600](https://github.com/bmuschko/gradle-docker-plugin/pull/600)
* Various tasks had their progress logger output cleaned up. - [Pull request 601](https://github.com/bmuschko/gradle-docker-plugin/pull/601)

### Version 3.3.3 (June 8, 2018)
* Explicitly call `toString()` on values in maps passed to Docker API. - [Pull request 595](https://github.com/bmuschko/gradle-docker-plugin/pull/595)
* Task `DockerLivenessProbeContainer` gained method `lastInspection()` which will return the last "docker inspect container" response AFTER execution has completed. - [Pull request 596](https://github.com/bmuschko/gradle-docker-plugin/pull/596)

### Version 3.3.2 (June 5, 2018)
* Task `DockerLivenessProbeContainer` now has the `probe` option set to optional and if NOT defined will fallback to checking if container is in a running state. - [Pull request 594](https://github.com/bmuschko/gradle-docker-plugin/pull/594)

### Version 3.3.1 (June 2, 2018)
* Various minor refactorings surrounding new task `DockerExecStopContainer`. - [Pull request 592](https://github.com/bmuschko/gradle-docker-plugin/pull/592)

### Version 3.3.0 (June 1, 2018)
* Added task `DockerClient` to pass the raw `docker-java` client to the `onNext` closure if defined. - [Pull request 589](https://github.com/bmuschko/gradle-docker-plugin/pull/589)
* Task `DockerCreateContainer` will now log the `containerName` if set, which is the standard within this plugin, otherwise fallback to the just created `containerId`.
* Task `DockerExecContainer` gained option `successOnExitCodes` to allow user to define a list of successful exit codes the exec is allowed to return and will fail if not in list. Default behavior is to do no check. - [Pull request 590](https://github.com/bmuschko/gradle-docker-plugin/pull/590)
* Added task `DockerLivenessProbeContainer` which will poll, for some defined amount of time, a running containers logs looking for a given message and fail if not found. - [Pull request 587](https://github.com/bmuschko/gradle-docker-plugin/pull/587)
* Added task `DockerExecStopContainer` to allow the user to execute an arbitrary cmd against a container, polling for it to enter a non-running state, and if that does not succeed in time issue stop request. - [Pull request 591](https://github.com/bmuschko/gradle-docker-plugin/pull/591)

### Version 3.2.9 (May 22, 2018)
* Fixed a bug in task `DockerCreateContainer` where option `cpuset` is now renamed differetnly in `docker-java`. - [Pull request 585](https://github.com/bmuschko/gradle-docker-plugin/pull/585)

### Version 3.2.8 (April 30, 2018)
* Task `DockerExecContainer` gained option `user` to specify a user/group. - [Pull request 574](https://github.com/bmuschko/gradle-docker-plugin/pull/574)
* Task `DockerCreateContainer` gained option `ipV4Address` to specify a specific ipv4 address to use. - [Pull request 449](https://github.com/bmuschko/gradle-docker-plugin/pull/449)
* Bump gradle to `4.7`. - [Pull request 578](https://github.com/bmuschko/gradle-docker-plugin/pull/578)

### Version 3.2.7 (April 19, 2018)
* Task `DockerSaveImage` gained option `useCompression` to optionally gzip the created tar. - [Pull request 565](https://github.com/bmuschko/gradle-docker-plugin/pull/565)
* Add `javax.activation` dependency for users who are working with jdk9+. - [Pull request 572](https://github.com/bmuschko/gradle-docker-plugin/pull/572)

### Version 3.2.6 (March 31, 2018)
* Cache `docker-java` client instead of recreating for every request/task invocation. This is a somewhat big internal change but has a lot of consequences and so it was deserving of its own point release. - [Pull request 558](https://github.com/bmuschko/gradle-docker-plugin/pull/558)

### Version 3.2.5 (March 2, 2018)
* Added `macAddress` option to task `DockerCreateContainer` - [Pull request 538](https://github.com/bmuschko/gradle-docker-plugin/pull/538)
* Initial work for `codenarc` analysis - [Pull request 537](https://github.com/bmuschko/gradle-docker-plugin/pull/537)
* Use of `docker-java-shaded` library in favor of `docker-java` proper to get around class-loading/clobbering issues - [Pull request 550](https://github.com/bmuschko/gradle-docker-plugin/pull/550)
* Honor DOCKER_CERT_PATH env var if present - [Pull request 549](https://github.com/bmuschko/gradle-docker-plugin/pull/549)
* Task `DockerSaveImage` will now create file for you should it not exist - [Pull request 552](https://github.com/bmuschko/gradle-docker-plugin/pull/552)
* Task `DockerPushImage` will now include tag info in logging if applicable - [Pull request 554](https://github.com/bmuschko/gradle-docker-plugin/pull/554)
* !!!!! BREAKING: Property `inputStream` of task `DockerLoadImage` has been changed from type `InputStream` to `Closure<InputStream>`. This was done to allow scripts/code/pipelines to delay getting the image and side-step this property getting configured during gradles config-phase. - [Pull request 552](https://github.com/bmuschko/gradle-docker-plugin/pull/552)

### Version 3.2.4 (February 5, 2018)
* Use openjdk as a default image in DockerJavaApplicationPlugin - [Pull request 528](https://github.com/bmuschko/gradle-docker-plugin/pull/528)
* Add `skipMaintainer` to `DockerJavaApplication` - [Pull request 529](https://github.com/bmuschko/gradle-docker-plugin/pull/529)
* Can now define `labels` in `DockerCreateContainer` task - [Pull request 530](https://github.com/bmuschko/gradle-docker-plugin/pull/530)
* Added task `DockerRenameContainer` - [Pull request 533](https://github.com/bmuschko/gradle-docker-plugin/pull/533)

### Version 3.2.3 (January 26, 2018)
* If `DockerWaitHealthyContainer` is run on an image which was not built with `HEALTHCHECK` than fallback to using generic status - [Pull request 520](https://github.com/bmuschko/gradle-docker-plugin/pull/520)

### Version 3.2.2 (January 17, 2018)
* Bump gradle to `4.3.1` - [Pull request 500](https://github.com/bmuschko/gradle-docker-plugin/pull/500)
* Bug fix for [ISSUE-490](https://github.com/bmuschko/gradle-docker-plugin/issues/490) wherein `on*` reactive-stream closures are evaluated with null exception when using gradle-4.3 - [Commit 93b80f](https://github.com/bmuschko/gradle-docker-plugin/commit/93b80f2bd18c4f04d0f58443b45c59cb58a54e77)
* Support for zero exposed ports in `DockerJavaApplication` - [Pull request 504](https://github.com/bmuschko/gradle-docker-plugin/pull/504)

### Version 3.2.1 (November 22, 2017)
* Bump gradle to `4.2` - [Pull request 471](https://github.com/bmuschko/gradle-docker-plugin/pull/471)
* Fix setting `shmSize` when creating container - [Pull request 480](https://github.com/bmuschko/gradle-docker-plugin/pull/480)
* Add support for entrypoint on `DockerCreateContainer` - [Pull request 479](https://github.com/bmuschko/gradle-docker-plugin/pull/479)
* Bump verison of docker-java to 3.0.14 - [Pull request 482](https://github.com/bmuschko/gradle-docker-plugin/pull/482)
* Added `DockerWaitHealthyContainer` task - [Pull request 485](https://github.com/bmuschko/gradle-docker-plugin/pull/485)
* Use groovy join function in favor or jdk8 join function. - [Pull request 498](https://github.com/bmuschko/gradle-docker-plugin/pull/498)

### Version 3.2.0 (September 29, 2017)
* Update `createBind` to use docker-java `parse` method - [Pull request 452](https://github.com/bmuschko/gradle-docker-plugin/pull/452)
* Allow Docker to cache app libraries dir when `DockerJavaApplication` plugin is used - [Pull request 459](https://github.com/bmuschko/gradle-docker-plugin/pull/459)

### Version 3.1.0 (August 21, 2017)
* `DockerListImages` gained better support for filters - [Pull request 414](https://github.com/bmuschko/gradle-docker-plugin/pull/414)
* Use `alpine:3.4` image in functional tests - [Pull request 416](https://github.com/bmuschko/gradle-docker-plugin/pull/416)
* `DockerBuildImage` and `DockerCreateContainer` gained optional argument `shmSize` - [Pull request 413](https://github.com/bmuschko/gradle-docker-plugin/pull/413)
* Added tasks `DockerInspectNetwork`, `DockerCreateNetwork`, and `DockerRemoveNetwork` - [Pull request 422](https://github.com/bmuschko/gradle-docker-plugin/pull/422)
* Add statically typed methods for configuring plugin with Kotlin - [Pull request 426](https://github.com/bmuschko/gradle-docker-plugin/pull/426)
* Fix `Dockerfile` task up-to-date logic - [Pull request 433](https://github.com/bmuschko/gradle-docker-plugin/pull/433)
* Multiple ENVs are not set the same way as single ENV instructions - [Pull request 415](https://github.com/bmuschko/gradle-docker-plugin/pull/415)
* `DockerCreateContainer` changed optional input `networkMode` to `network` to better align with docker standatds - [Pull request 440](https://github.com/bmuschko/gradle-docker-plugin/pull/440)
* The first instruction of a Dockerfile has to be FROM except for Docker versions later than 17.05 - [Pull request 435](https://github.com/bmuschko/gradle-docker-plugin/pull/435)
* Bump verison of docker-java to 3.0.13 - [Commit b2d936](https://github.com/bmuschko/gradle-docker-plugin/commit/b2d93671ed0a0b7177a450d503c28eca6aa6795d)

### Version 3.0.10 (July 7, 2017)
* Bump verison of docker-java to 3.0.12 - [Pull request 408](https://github.com/bmuschko/gradle-docker-plugin/pull/408)
* Publish javadocs on new release - [Pull request 405](https://github.com/bmuschko/gradle-docker-plugin/pull/405)

### Version 3.0.9 (July 4, 2017)
* Bump verison of docker-java to 3.0.11 - [Pull request 403](https://github.com/bmuschko/gradle-docker-plugin/pull/403)
* New release process - [Pull request 402](https://github.com/bmuschko/gradle-docker-plugin/pull/402)

### Version 3.0.8 (June 16, 2017)
* Task `DockerPullImage` gained method `getImageId()` which returns the fully qualified imageId of the image that was just pulled - [Pull request 379](https://github.com/bmuschko/gradle-docker-plugin/pull/379)
* Task `DockerBuildImage` gained property `tags` which allows for multiple tags to be specified when building an image - [Pull request 380](https://github.com/bmuschko/gradle-docker-plugin/pull/380)
* Task `DockerCreateContainer` gained property `networkAliases` - [Pull request 384](https://github.com/bmuschko/gradle-docker-plugin/pull/384)

### Version 3.0.7 (May 17, 2017)
* Invoke onNext closures call() method explicitly - [Pull request 368](https://github.com/bmuschko/gradle-docker-plugin/pull/368)
* Adds new task DockerInspectExecContainer which allows to inspect exec instance - [Pull request 362](https://github.com/bmuschko/gradle-docker-plugin/pull/362)
* `functionalTest`'s can now run against a native docker instance - [Pull request 369](https://github.com/bmuschko/gradle-docker-plugin/pull/369)
* `DockerLogsContainer` now preserves leading space - [Pull request 370](https://github.com/bmuschko/gradle-docker-plugin/pull/370)
* Allow customization of app plugin entrypoint/cmd instructions - [Pull request 359](https://github.com/bmuschko/gradle-docker-plugin/pull/359)
* Task `Dockerfile` will no longer be forced as `UP-TO-DATE`, instead the onus will be put on developers to code this should they want this functionality. - [ISSUE 357](https://github.com/bmuschko/gradle-docker-plugin/issues/357)
* Now that `functionalTest`'s work natively, and in CI, add the test `started`, `passed` and `failed` logging messages so as to make it absolutely clear to users what is being run vs having no output at all. - [Pull request 373](https://github.com/bmuschko/gradle-docker-plugin/pull/373)
* Bump `docker-java` to version `3.0.10` - [Pull request 378](https://github.com/bmuschko/gradle-docker-plugin/pull/378)

### Version 3.0.6 (March 2, 2017)

* Bump version of docker-java to 3.0.7 - [Pull request 331](https://github.com/bmuschko/gradle-docker-plugin/pull/331)
* Add support for label parameter on docker image creation - [Pull request 332](https://github.com/bmuschko/gradle-docker-plugin/pull/332)

### Version 3.0.5 (December 27, 2016)

* Support multiple variables per singled ENV cmd - [Pull request 311](https://github.com/bmuschko/gradle-docker-plugin/pull/311)
* Implement a sane default docker URL based on environment - [Pull request 313](https://github.com/bmuschko/gradle-docker-plugin/pull/313)
* Implement [reactive-stream](https://github.com/reactive-streams/reactive-streams-jvm/#2-subscriber-code) methods `onNext` and `onComplete` for all tasks - [Pull request 307](https://github.com/bmuschko/gradle-docker-plugin/pull/307)

### Version 3.0.4 (December 1, 2016)

* Implement [reactive-stream](https://github.com/reactive-streams/reactive-streams-jvm/#2-subscriber-code) method `onError` for all tasks - [Pull request 302](https://github.com/bmuschko/gradle-docker-plugin/pull/302)
* Bump docker-java to 3.0.6 - [Pull request 279](https://github.com/bmuschko/gradle-docker-plugin/pull/279)

### Version 3.0.3 (September 6, 2016)

* Print error messages received from docker engine when build fails - [Pull request 265](https://github.com/bmuschko/gradle-docker-plugin/pull/265)
* Bump docker-java to 3.0.5 - [Pull request 263](https://github.com/bmuschko/gradle-docker-plugin/pull/263)
* Add support for `force` removal on `DockerRemoveImage` - [Pull request 266](https://github.com/bmuschko/gradle-docker-plugin/pull/266)
* Various fixes and cleanups as well default to alpine image for all functional tests - [Pull request 269](https://github.com/bmuschko/gradle-docker-plugin/pull/269)
* Added `editorconfig` file with some basic defaults - [Pull request 270](https://github.com/bmuschko/gradle-docker-plugin/pull/270)

### Version 3.0.2 (August 14, 2016)

* Add support for build-time variables in `DockerBuildImage` task - [Pull request 240](https://github.com/bmuschko/gradle-docker-plugin/pull/240)
* Fix incorrect docker-java method name in `DockerCreateContainer` task - [Pull request 242](https://github.com/bmuschko/gradle-docker-plugin/pull/242)
* Can define devices on `DockerCreateContainer` task - [Pull request 245](https://github.com/bmuschko/gradle-docker-plugin/pull/245)
* Can now supply multiple ports when working with `docker-java-application` - [Pull request 254](https://github.com/bmuschko/gradle-docker-plugin/pull/254)
* Bump docker-java to 3.0.2 - [Pull request 259](https://github.com/bmuschko/gradle-docker-plugin/pull/259)
* If buildscript repos are required make sure they are added after evaluation - [Pull request 260](https://github.com/bmuschko/gradle-docker-plugin/pull/260)

### Version 3.0.1 (July 6, 2016)

* Simplify Gradle TestKit usage - [Pull request 225](https://github.com/bmuschko/gradle-docker-plugin/pull/225)
* Ensure `tlsVerify` is set in addition to `certPath` for DockerClientConfig setup - [Pull request 230](https://github.com/bmuschko/gradle-docker-plugin/pull/230)
* Upgrade to Gradle 2.14.

### Version 3.0.0 (June 5, 2016)

* Task `DockerLogsContainer` gained attribute `sink` - [Pull request 203](https://github.com/bmuschko/gradle-docker-plugin/pull/203)
* Task `DockerBuildImage` will no longer insert extra newline as part of build output - [Pull request 206](https://github.com/bmuschko/gradle-docker-plugin/pull/206)
* Upgrade to docker-java 3.0.0 - [Pull request 217](https://github.com/bmuschko/gradle-docker-plugin/pull/217)
* Fallback to buildscript.repositories for internal dependency resolution if no repositories were defined - [Pull request 218](https://github.com/bmuschko/gradle-docker-plugin/pull/218)
* Added task `DockerExecContainer` - [Pull request 221](https://github.com/bmuschko/gradle-docker-plugin/pull/221)
* Added task `DockerCopyFileToContainer` - [Pull request 222](https://github.com/bmuschko/gradle-docker-plugin/pull/222)
* Task `DockerCreateContainer` gained attribute `restartPolicy` - [Pull request 224](https://github.com/bmuschko/gradle-docker-plugin/pull/224)
* Remove use of Gradle internal methods.
* Added ISSUES.md file.
* Upgrade to Gradle 2.13.

### Version 2.6.8 (April 10, 2016)
* Added task `DockerLogsContainer` - [Pull request 181](https://github.com/bmuschko/gradle-docker-plugin/pull/181)
* Bump docker-java to version 2.3.3 - [Pull request 183](https://github.com/bmuschko/gradle-docker-plugin/pull/183)
* Bug fix when not checking if parent dir already exists before creating with `DockerCopyFileToContainer` - [Pull request 186](https://github.com/bmuschko/gradle-docker-plugin/pull/186)
* `DockerWaitContainer` now produces exitCode - [Pull request 189](https://github.com/bmuschko/gradle-docker-plugin/pull/189)
* `apiVersion` can now be set on `DockerExtension` and overriden on all tasks - [Pull request 182](https://github.com/bmuschko/gradle-docker-plugin/pull/182)
* Internal fix where task variables had to be defined - [Pull request 194](https://github.com/bmuschko/gradle-docker-plugin/pull/194)

### Version 2.6.7 (March 10, 2016)

* Upgrade to Gradle 2.11.
* Bug fix when copying single file from container and hostPath is set to directory for `DockerCopyFileFromContainer` - [Pull request 163](https://github.com/bmuschko/gradle-docker-plugin/pull/163)
* Step reports are now printed to stdout by default for `DockerBuildImage` - [Pull request 145](https://github.com/bmuschko/gradle-docker-plugin/pull/145)
* UP-TO-DATE functionality has been removed from `DockerBuildImage` as there were too many corner cases to account for - [Pull request 172](https://github.com/bmuschko/gradle-docker-plugin/pull/172)

### Version 2.6.6 (February 27, 2016)

* Added docker step reports for `DockerBuildImage` - [Pull request 145](https://github.com/bmuschko/gradle-docker-plugin/pull/145)
* Added `onlyIf` check for `DockerBuildImage` - [Pull request 139](https://github.com/bmuschko/gradle-docker-plugin/pull/139)
* Added method logConfig for `DockerCreateContainer` - [Pull request 157](https://github.com/bmuschko/gradle-docker-plugin/pull/157)
* Various commands can now be passed closures for `Dockerfile` - [Pull request 155](https://github.com/bmuschko/gradle-docker-plugin/pull/155)
* Fix implementation of exposedPorts for `DockerCreateContainer` - [Pull request 140](https://github.com/bmuschko/gradle-docker-plugin/pull/140)
* Upgrade to Docker Java 2.2.2 - [Pull request 158](https://github.com/bmuschko/gradle-docker-plugin/pull/158).

### Version 2.6.5 (January 16, 2016)

* Fix implementation of `DockerCopyFileFromContainer` - [Pull request 135](https://github.com/bmuschko/gradle-docker-plugin/pull/135).
* Add `networkMode` property to `DockerCreateContainer` - [Pull request 114](https://github.com/bmuschko/gradle-docker-plugin/pull/114).
* Upgrade to Docker Java 2.1.4 - [Issue 138](https://github.com/bmuschko/gradle-docker-plugin/issues/138).

### Version 2.6.4 (December 24, 2015)

* Expose privileged property on `DockerCreateContainer` - [Pull request 130](https://github.com/bmuschko/gradle-docker-plugin/pull/130).

### Version 2.6.3 (December 23, 2015)

* Expose force and removeVolumes properties on `DockerRemoveContainer` - [Pull request 129](https://github.com/bmuschko/gradle-docker-plugin/pull/129).

### Version 2.6.2 (December 22, 2015)

* Expose support for LogDriver on `DockerCreateContainer` - [Pull request 118](https://github.com/bmuschko/gradle-docker-plugin/pull/118).
* Upgrade to Docker Java 2.1.2.

### Version 2.6.1 (September 21, 2015)

* Correct the `withVolumesFrom` call on `DockerCreateContainer` task which needs to get a `VolumesFrom[]` array as the parameter - [Pull request 102](https://github.com/bmuschko/gradle-docker-plugin/pull/102).
* Upgrade to Docker Java 2.1.1 - [Pull request 109](https://github.com/bmuschko/gradle-docker-plugin/pull/109).

### Version 2.6 (August 30, 2015)

* Upgrade to Docker Java 2.1.0 - [Pull request 92](https://github.com/bmuschko/gradle-docker-plugin/pull/92).
_Note:_ The Docker Java API changed vastly with version 2.0.0. The tasks `DockerBuildImage`, `DockerPullImage` and 
`DockerPushImage` do not provide a response handler anymore. This is a breaking change. Future versions of the plugin
might open up the response handling again in some way.
* `DockerListImages` with `filter` call a wrong function from `ListImagesCmdImpl.java` - [Issue 105](https://github.com/bmuschko/gradle-docker-plugin/issues/105).

### Version 2.5.2 (August 15, 2015)

* Fix listImages task throwing GroovyCastException - [Issue 96](https://github.com/bmuschko/gradle-docker-plugin/issues/96).
* Add support for publishAll in DockerCreateContainer - [Pull request 94](https://github.com/bmuschko/gradle-docker-plugin/pull/94).
* Add optional dockerFile option to the DockerBuildImage task - [Pull request 47](https://github.com/bmuschko/gradle-docker-plugin/pull/47).

### Version 2.5.1 (July 29, 2015)

* Adds Dockerfile support for the LABEL instruction - [Pull request 86](https://github.com/bmuschko/gradle-docker-plugin/pull/86).
* Usage of [docker-java library](https://github.com/docker-java/docker-java) version 1.4.0. Underlying API does not provide
setting port bindings for task `DockerStartContainer` anymore. Needs to be set on `DockerCreateContainer`.

### Version 2.5 (July 18, 2015)

* Expose response handler for `DockerListImages` task - [Issue 75](https://github.com/bmuschko/gradle-docker-plugin/issues/75).
* Pass in credentials when building an image - [Issue 76](https://github.com/bmuschko/gradle-docker-plugin/issues/76).

### Version 2.4.1 (July 4, 2015)

* Add `extraHosts` property to task `DockerCreateContainer` - [Pull request 79](https://github.com/bmuschko/gradle-docker-plugin/pull/79).
* Add `pull` property to task `DockerBuildImage` - [Pull request 78](https://github.com/bmuschko/gradle-docker-plugin/pull/78).

### Version 2.4 (May 16, 2015)

* Added missing support for properties `portBindings` and `cpuset` in `CreateContainer` - [Pull request 66](https://github.com/bmuschko/gradle-docker-plugin/pull/66).
* Expose response handlers so users can inject custom handling logic - [Issue 65](https://github.com/bmuschko/gradle-docker-plugin/issues/65).
* Upgrade to Gradle 2.4 including all compatible plugins and libraries.

### Version 2.3.1 (April 25, 2015)

* Added support for `Binds` when creating containers - [Pull request 54](https://github.com/bmuschko/gradle-docker-plugin/pull/54).
* Added task for copying files from a container to a host - [Pull request 57](https://github.com/bmuschko/gradle-docker-plugin/pull/57).

### Version 2.3 (April 18, 2015)

* Added task `DockerInspectContainer` - [Pull request 44](https://github.com/bmuschko/gradle-docker-plugin/pull/44).
* Added property `containerName` to task `DockerCreateContainer` - [Pull request 44](https://github.com/bmuschko/gradle-docker-plugin/pull/44).
* Allow for linking containers for task `DockerCreateContainer` - [Pull request 53](https://github.com/bmuschko/gradle-docker-plugin/pull/53).
* Usage of [docker-java library](https://github.com/docker-java/docker-java) version 1.2.0.

### Version 2.2 (April 12, 2015)

* Usage of [docker-java library](https://github.com/docker-java/docker-java) version 1.1.0.

### Version 2.1 (March 24, 2015)

* Renamed property `registry` to `registryCredentials` for plugin extension and tasks implementing `RegistryCredentialsAware` to better indicate its purpose.
_Note:_ This is a breaking change.

### Version 2.0.3 (March 20, 2015)

* Allow for specifying port bindings for container start command. - [Issue 30](https://github.com/bmuschko/gradle-docker-plugin/issues/30).
* Throw an exception if an error response is encountered - [Issue 37](https://github.com/bmuschko/gradle-docker-plugin/issues/37).
* Upgrade to Gradle 2.3.

### Version 2.0.2 (February 19, 2015)

* Set source and target compatibility to Java 6 - [Issue 32](https://github.com/bmuschko/gradle-docker-plugin/issues/32).

### Version 2.0.1 (February 10, 2015)

* Extension configuration method for `DockerJavaApplicationPlugin` needs to be registered via extension instance - [Issue 28](https://github.com/bmuschko/gradle-docker-plugin/issues/28).

### Version 2.0 (February 4, 2015)

* Upgrade to Gradle 2.2.1 including all compatible plugins and libraries.

### Version 0.8.3 (February 4, 2015)

* Add project group to default tag built by Docker Java application plugin - [Issue 25](https://github.com/bmuschko/gradle-docker-plugin/issues/25).

### Version 0.8.2 (January 30, 2015)

* Expose method for task `Dockerfile` for providing vanilla Docker instructions.

### Version 0.8.1 (January 24, 2015)

* Usage of [docker-java library](https://github.com/docker-java/docker-java) version 0.10.5.
* Correctly create model instances for create container task - [Issue 19](https://github.com/bmuschko/gradle-docker-plugin/issues/19).

### Version 0.8 (January 7, 2014)

* Allow for pushing to Docker Hub - [Issue 18](https://github.com/bmuschko/gradle-docker-plugin/issues/18).
* Better handling of API responses.
* Note: Change to plugin extension. The property `docker.serverUrl` is now called `docker.url`. Instead of `docker.credentials`, you will need to use `docker.registry`.

### Version 0.7.2 (December 23, 2014)

* `Dockerfile` task is always marked UP-TO-DATE after first execution - [Issue 13](https://github.com/bmuschko/gradle-docker-plugin/issues/13).
* Improvements to `Dockerfile` task - [Pull request 16](https://github.com/bmuschko/gradle-docker-plugin/pull/16).
    * Fixed wrong assignment of key field in  environment variable instruction.
    * Allow for providing multiple ports to the expose instruction.

### Version 0.7.1 (December 16, 2014)

* Fixed entry point definition of Dockerfile set by Java application plugin.

### Version 0.7 (December 14, 2014)

* Allow for properly add user-based instructions to Dockfile task with predefined instructions without messing up the order. - [Issue 12](https://github.com/bmuschko/gradle-docker-plugin/issues/12).
* Renamed task `dockerCopyDistTar` to `dockerCopyDistResources` to better express intent.

### Version 0.6.1 (December 11, 2014)

* Allow for setting path to certificates for communicating with Docker over SSL - [Issue 10](https://github.com/bmuschko/gradle-docker-plugin/issues/10).

### Version 0.6 (December 7, 2014)

* Usage of [docker-java library](https://github.com/docker-java/docker-java) version 0.10.4.
* Added Docker Java application plugin.
* Better documentation.

### Version 0.5 (December 6, 2014)

* Fixed implementations of tasks `DockerPushImage` and `DockerCommitImage` - [Issue 11](https://github.com/bmuschko/gradle-docker-plugin/issues/11).

### Version 0.4 (November 27, 2014)

* Added task for creating a Dockerfile.

### Version 0.3 (November 23, 2014)

* Usage of [docker-java library](https://github.com/docker-java/docker-java) version 0.10.3.
* Changed package name to `com.bmuschko.gradle.docker`.
* Changed group ID to `com.bmuschko`.
* Adapted plugin IDs to be compatible with Gradle's plugin portal.

### Version 0.2 (June 19, 2014)

* Usage of [docker-java library](https://github.com/docker-java/docker-java) version 0.8.2.
* Provide custom task type for push operation.
* Support for using remote URLs when building image - [Issue 3](https://github.com/bmuschko/gradle-docker-plugin/issues/3).

### Version 0.1 (May 11, 2014)

* Initial release.

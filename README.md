# Issue
sbt versions 1.9.3 and below is able to handle the Maven packaging ejb properly by downloading the jar file.

e.g https://repo1.maven.org/maven2/org/jboss/da/reports-model/2.1.0/reports-model-2.1.0.pom
(See ejb-dep-sbt-1.9.3 folder)

Running:

```
sbt run
```
works fine.

However, starting from sbt 1.9.4 (See ejb-dep-sbt-1.9.4, ejb-dep-sbt-1.10.1 folder), it's trying to download the wrong file:
```
$ sbt run
...
[info] welcome to sbt 1.10.1 (N/A Java 21.0.3)
[info] loading project definition from /tmp/test2/ejb-dep-issue/ejb-dep-sbt-1.10.1/project
[info] loading settings for project ejb-dep-sbt-1-10-1 from build.sbt ...
[info] set current project to hello-world (in build file:/tmp/test2/ejb-dep-issue/ejb-dep-sbt-1.10.1/)
[error] lmcoursier.internal.shaded.coursier.error.FetchError$DownloadingArtifacts: Error fetching artifacts:
[error] https://repo1.maven.org/maven2/org/jboss/da/reports-model/2.1.0/reports-model-2.1.0.ejb: not found: https://repo1.maven.org/maven2/org/jboss/da/reports-model/2.1.0/reports-model-2.1.0.ejb
```

The downloaded artifact should be: https://repo1.maven.org/maven2/org/jboss/da/reports-model/2.1.0/reports-model-2.1.0.jar instead of the '.ejb'

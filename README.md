Central Sync Maven Plugin
===================

This is a Maven plugin that syncs a Bintray project to Maven Central. It
defaults to the correct settings for the OpenZipkin organization.

### Setup
First, you'll need add `sonatype` and `bintray` servers to your settings.xml file:

```xml
<server>
  <id>sonatype</id>
  <username>${env.SONATYPE_USER}</username>
  <password>${env.SONATYPE_PASSWORD}</password>
</server>
<server>
  <id>bintray</id>
  <username>${env.BINTRAY_USER}</username>
  <password>${env.BINTRAY_KEY}</password>
</server>
--snip--
```

Then, in your pom, you'll need to configure this plugin with the bintray
package you are deploying:

```xml
<plugin>
  <groupId>io.zipkin.centralsync-maven-plugin</groupId>
  <artifactId>centralsync-maven-plugin</artifactId>
  <version>LATEST_VERSION_HERE</version>
  <configuration>
    <packageName>brave</packageName>
  </configuration>
</plugin>
```

### Dry run
Next, dry-run your configuration to ensure there are no problems.

```bash
mvn -N io.zipkin.centralsync-maven-plugin:centralsync-maven-plugin:sync -Dsync.dryRun
```

Now you can tidy up in your release scripts!

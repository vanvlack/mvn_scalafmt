## Synopsis

A wrapper that allows the use of the [Scalafmt](https://github.com/olafurpg/scalafmt/) formatter in Maven;

Note: There are multiple versions of the plugin released and the version of the plugin should match the version 
of scalafmt you wish to use.  Current supported versions are 0.6.0 - 1.1.0. For example, to use the latest version 
of the plugin with the latest version of scala-fmt you should set the version to 0.4_1.1.0 in your pom.
All versions are currently compiled against Scala 2.11.8. If you require anything else, please open an issue.

## Usage

Add the following snippet to your pom; anything in <parameters> will be
passed through to the CLI as is.

```xml
<plugin>
  <groupId>org.antipathy</groupId>
  <artifactId>mvn-scalafmt</artifactId>
  <version>0.5_${scalafmt.version}</version>
  <configuration>
    <parameters>--diff</parameters> <!-- Additional command line arguments -->
    <configLocation>${project.basedir}/path/to/scalafmt.conf</configLocation>
  </configuration>
  <executions>
    <execution>
      <phase>validate</phase>
      <goals>
        <goal>format</goal>
      </goals>
    </execution>
  </executions>
</plugin>
```

Make sure your source paths are setup correctly, for example:

```xml
<build>
    <sourceDirectory>src/main/scala</sourceDirectory>
    <testSourceDirectory>src/test/scala</testSourceDirectory>
    ...
</build>
```
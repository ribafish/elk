<p align="center">
  <img src="https://raw.githubusercontent.com/eclipse/elk/master/docs/static/img/elk_with_text.svg?sanitize=true" height="150">
</p>

Diagrams and visual languages are a great thing,
but getting the layout just right for them to be easily understandable
can be tedious and time-consuming.
The Eclipse Layout Kernel provides a number of layout algorithms
as well as an Eclipse-based infrastructure to connect them
to editors and viewers.
The layout algorithms are plain Java
and can thus also be used outside of Eclipse.

## More Info

* [The ELK homepage](http://www.eclipse.org/elk)
* [... and ELK's documentation](http://www.eclipse.org/elk/documentation.html)
* [ELK Live](https://rtsys.informatik.uni-kiel.de/elklive/) (web-based playground to play around with ELK)
* [elkjs](https://github.com/kieler/elkjs) (JavaScript library transpiled from ELK's Java sources)

## Example Layout

![](https://raw.githubusercontent.com/eclipse/elk/master/docs/static/img/example_layout_complexRouter.svg?sanitize=true)

## Repository Structure

The repository's structure is pretty straightforward. We only have a few folders:

* `build`:
  Contains all the files necessary to build ELK in all its different forms.
* `config`:
  Contains configuration files, such as our Checkstyle configuration.
* `docs`:
  Contains documentation in the form of a [Hugo](https://gohugo.io/) site.
* `features`:
  Contains all the Eclipse features ELK consists of.
* `plugins`:
  Contains all the plugins ELK consists of.
* `setups`:
  Contains our Oomph setup files.
* `tests`:
  Contains unit tests. Note that we have [a whole repository](https://github.com/eclipse/elk-models/) dedicated to test models.


## Building ELK

Information on how to build ELK and the documentation can be found [on our website](https://www.eclipse.org/elk/documentation/contributors/buildingelk.html).

## Building notes from @ribafish

Build with java 17 and maven 3.9. All executions should be invoked from the `build` directory.

Integration tests are executed as following:

```shell
mvn -Delk.metadata.documentation.outputPath=${ELK_REPO}/docs -Dtests.paths.elk-repo=${ELK_REPO} -Dtests.paths.models-repo=${ELK_MODELS_REPO} -Dmaven.repo.local=./mvnrepo clean integration-test
```

where `ELK_REPO` and `ELK_MODELS_REPO` are replaced by paths on your system. This also means that you need a local clone of https://github.com/eclipse/elk-models, to which you point `ELK_MODELS_REPO`.

Simply building ELK can be done with
```shell
mvn -Delk.metadata.documentation.outputPath=${ELK_REPO}/docs -Dmaven.repo.local=./mvnrepo clean package
```
where `ELK_REPO` is replaced by a path on your system.



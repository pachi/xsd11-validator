XSD 1.1 Validator
=================

Command line XML Schema 1.1 validator written in Java.

Currently, [Xerces2 Java](http://xerces.apache.org/xerces2-j/) seems to be the one and only free and open source solution for XSD 1.1 validation. You can download Xerces2 Java [here](http://xerces.apache.org/mirrors.cgi). Be careful to pick the right version that comes with XSD 1.1 support. This release of the package has complete support for XSD 1.1.

Unfortunately, the distribution does not provide any command line validation tool, you have to write your own from scratch. I provide a simple but handy implementation in xsd11-validator.jar. This JAR also contains Xerces2 Java with all of its dependencies.

You can run the JAR with the command java -jar xsd11-validator.jar to display usage information:
```
usage: java hu.unideb.inf.validator.SchemaValidator -if <file> | -iu <url>
       [-sf <file> | -su <url>]
 -if,--instanceFile <file>   read instance from the file specified
 -iu,--instanceUrl <url>     read instance from the URL specified
 -sf,--schemaFile <file>     read schema from the file specified
 -su,--schemaUrl <url>       read schema from the URL specified
```

You must provide an instance document to be validated using either the ```-if``` or the ```-iu``` option. (Option ```-if``` requires a file path as an argument, option ```-iu``` requires an URL.) Similarly, you can specify a schema document using either the ```-sf``` or ```-su``` option. The ```-sf``` and ```-su``` options are not mandatory, if they are omitted the value of the ```xsi:schemaLocation``` attribute is considered in the instance. The following is an example of how to use the program:

```
java -jar xsd11-validator.jar -sf schema.xsd -if instance.xml
```

From a developer’s standpoint, there is a minor flaw of Xerces2 Java: you will not find the required beta release in any of the publicly available Maven repositories. You must use your own local copy of xercesImpl.jar in your Maven projects. The good news is that its dependencies are available from repositories. Take a look at the source distribution of the command line tool to see how Xerces2 Java can be used in your Maven projects.

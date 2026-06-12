---
title: "Batch files"
date: 2009-12-05
forum: Desktop Environments
---

### Post by RuneDevo on 2009-12-05
I code a lot of Java, and when I switched to Ubuntu, I haven't been able to. Does anyone know what the equivalent of a .bat file would be, or how I would convert the codes to Linux?

---

### Post by falconindy on 2009-12-05
I don't understand the connection between batch files and Java, but there's a multitude of shell scripting languages available for Linux, the most common being Bash.

What is it you're trying to accomplish?

---

### Post by RuneDevo on 2009-12-05
Well, I use Batch files to run my Java programs with codes such as;
```
@echo off 
cd src 
java Loader 
exit
```

---

### Post by gmjs on 2009-12-05
When you write your Java classes, you still give them the .java extension.  To compile them, you run the command line tool **javac** as follows:

```
**$** javac MyClass.java
```

which creates your '.class' file.  You then run them using **java**:

```
**$** java MyClass
``` (note the '.class' extension is not required).

To run a compiled package (with the .jar extension) you would use the following:

```
**$** java -jar my-application.jar
```

You could write a short script to do this for you if you want to--just put the commands in a plain text file (as with a DOS batch file) with the following line at the top:

```
**#!/bin/bash**
```

(or whichever shell you want to use).

Make sure the file's execute bit is set with the following line at the terminal:

```
**$** chmod +x *name-of-script-file*
```

Hope that helps.

Graham

---


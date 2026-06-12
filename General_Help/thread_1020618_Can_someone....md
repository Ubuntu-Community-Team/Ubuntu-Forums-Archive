---
title: "Can someone...?"
date: 2008-12-24
forum: General Help
---

### Post by bartbomb3000 on 2008-12-24
Can someone turn this .bat file into a runnable  applicaiton for linux? 



this is the run.bat file contents. 
@ECHO OFF

color 0a

echo JeffScape  Client

echo Made by Jeff

echo Please visit JeffScape.freeforum.ca

JAVA -Xmx500m EGUI






this is the compile.bat file just incase it needs to be changed to.

@echo off

title Compiler

"%ProgramFiles%\Java\jdk1.6.0_07\bin\javac.exe" -cp . *.java

pause




I will give rep/thanks many times to person who makes it into an executable file for linux ubuntu.

---

### Post by bartbomb3000 on 2008-12-24
bump

---

### Post by Nepherte on 2008-12-24
I'm not really a bash scripting expert, but the echo command is the same so here's something to give you a headstart:
```

#!/bin/bash
echo JeffScape Client
echo Made by Jeff
echo Please visit JeffScape.freeforum.ca
java -Xmx500m EGUI

```
I'm not sure what the java command on windows does exactly.The -Xmx500m argument should work, and assuming EGUI is a class it should work too. After you saved this file, you will have to make it executable to be able to run it.

---


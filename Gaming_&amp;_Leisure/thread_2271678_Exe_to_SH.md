---
title: "Exe to SH"
date: 2015-03-31
forum: Gaming &amp; Leisure
---

### Post by brock4 on 2015-03-31
Can someone help me with this? What would I change this to? I would like it to run in Ubuntu.

```
@echo offcolor 0A
title Chronicscape Main World Server Box
echo Launching Server...
"C:/Program Files/Java/jre7/bin/java.exe" -cp bin;lib/*; com.rs.Launcher true true false
//"C:/Program Files/Java/jre7/bin/java.exe" -Xms2048m -Xmx2048m -cp bin;lib/*; com.rs.Launcher true true false
pause
``` 


Thanks

---

### Post by bardo2 on 2015-04-01
OMG, the batch file listed could eventually be run from a properly configured wine (but who wants that)
Java, especialy jre7 can be used from commandline (or any shell script - for that matter)
Of course that involves adjusting the arguments

Her is one example, i am using quite often:
--snip
${JAVA_PROGRAM_DIR}java -Xms16m -Xmx512m -Djava.library.path="${PROGRAM_DIR}" -Dpropertiesfile=linux.properties -jar myprogram.jar "$@"
--snip

The similarities should be obvious, right?

---


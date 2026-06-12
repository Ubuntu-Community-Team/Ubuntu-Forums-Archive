---
title: "how to run RSPS client?"
date: 2011-04-30
forum: Gaming &amp; Leisure
---

### Post by algebra2 on 2011-04-30
Hey, my little brother just wrecked Windows XP on this computer so I'm booting Ubuntu. I use this PC to play some RSPS (Runescape Private Servers) once in a while. I have no clue how to do this with Ubuntu. Anyhelp?

[PHP]@echo off 
title Helix - Loading 
color 0a 
 
:start 
echo. 
echo - 
echo Helix v1 Starting up... 
echo - 
if exist "%HOMEDRIVE%\Program Files (x86)"  goto x64 
goto x86 
 
 
:x64 
title  Helix v1 (x64) - Loader 
echo Auto-Detected 64-bit (x64) System 
echo - 
echo Client Output will be below 
echo - 
echo. 
"%HOMEDRIVE%/Program Files (x86)/Java/jre6/bin/java.exe" -Xmx1000m -jar client.jar 
exit 
 
 
:x86 
title  Helix v1 (x86) - Loader 
echo Auto-Detected 32-bit (x86) System 
echo - 
echo Client Output will be below 
echo - 
echo. 
"%HOMEDRIVE%/Program Files/Java/jre6/bin/java.exe" -Xmx1000m -jar client.jar 
pause[/PHP]Thats what is inside the run.bat


SOLVED

---

### Post by Woojoo//.deb on 2011-04-30
you should install the java run enviroument first and then try to run the client manualy (which is the client.jar) or browse to the folder with your client and use this command

 -Xmx1000m -jar client.jar 


eather way first you need the java files for it to work

---

### Post by algebra2 on 2011-04-30
Does ubuntu not come with java runetime envirement? 0.0 if not I'll download right now.

Edit: it seems I already have it.
Edit: How do I make Client.Jar executable?

---


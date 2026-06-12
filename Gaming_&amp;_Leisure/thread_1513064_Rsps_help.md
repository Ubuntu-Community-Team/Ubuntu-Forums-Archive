---
title: "Rsps help"
date: 2010-06-18
forum: Gaming &amp; Leisure
---

### Post by Simdog1 on 2010-06-18
Well i accidentally lost my vista by screwing something up and i had all my games on there but now im stuck with ubuntu =( but none of the games work so i decided to play Rsps (Runescape private server) i figured how to make the compile.cmd work since it was getting and error saying file not found but now i need to get my run.cmd to run since im getting
 file not found
press return to continue:
when i open it with gedit or notepad this is the code
@echo off 
color 0b 
@echo Ownage-Pkz 508 Client! 
@echo off 
cd files 
java -Xmx256m client 66 live live software members english game0 
pause
(o ya the game runs with java which i have installed since runescape works for me now )
well i need to know what to put in the run.cmd code to get it to work. 
thankyou

---

### Post by dim3000 on 2010-06-18
> **Simdog1 said:**
> Well i accidentally lost my vista by screwing something up and i had all my games on there but now im stuck with ubuntu =( but none of the games work so i decided to play Rsps (Runescape private server) i figured how to make the compile.cmd work since it was getting and error saying file not found but now i need to get my run.cmd to run since im getting
 file not found
press return to continue:
when i open it with gedit or notepad this is the code
@echo off 
color 0b 
@echo Ownage-Pkz 508 Client! 
@echo off 
cd files 
java -Xmx256m client 66 live live software members english game0 
pause
(o ya the game runs with java which i have installed since runescape works for me now )
well i need to know what to put in the run.cmd code to get it to work. 
thankyou

Hold On! Linux uses bash not the simple windows bat commands.
Your script in linux would be:
```

#!/bin/bash
echo "Ownage-Pkz 508 Client!"
cd files
java -Xmx256m client 66 live live software members english game0
read

```

Btw, which games don't work?

---

### Post by Simdog1 on 2010-06-18
what would i change my compile.cmd to?
@echo off 
"/home/family/Desktop/jdk1.6.0_20/bin/javac.exe" 
pause

---

### Post by dim3000 on 2010-06-18
> **Simdog1 said:**
> what would i change my compile.cmd to?
@echo off 
"/home/family/Desktop/jdk1.6.0_20/bin/javac.exe" 
pause

I don't think you need it.

---

### Post by Simdog1 on 2010-06-19
well after i changed my run.cmd it now opens the cmd thing then dissapears right away it used to show the error in the cmd but now its too fast to see it

---

### Post by Simdog1 on 2010-06-19
well i put pause at the end and this is what i actually get 
                                                                                Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>#!/bin/bash                   File not found                                                                                                                                                                                                                                  Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>echo "Ownage-Pkz 508 Client!" "Ownage-Pkz 508 Client!"
Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>#!/bin/bash                   File not found                                                                                                                                                                                                                                  Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>echo "Ownage-Pkz 508 Client!" "Ownage-Pkz 508 Client!"                                                                                                                                        Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>cd files
File not found                                                                                                                                                                                                                                  Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>echo "Ownage-Pkz 508 Client!" "Ownage-Pkz 508 Client!"                                                                                                                                        Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>cd files
                                                                                                                                                                Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>echo "Ownage-Pkz 508 Client!" "Ownage-Pkz 508 Client!"                                                                                                                                        Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>cd files                                                                                                      Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>java -Xmx256m cli
                                                                                Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>echo "Ownage-Pkz 508 Client!" "Ownage-Pkz 508 Client!"                                                                                                                                        Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>cd files                                                                                                      Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>java -Xmx256m client 66 live live software members english game0
Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>echo "Ownage-Pkz 508 Client!" "Ownage-Pkz 508 Client!"                                                                                                                                        Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>cd files                                                                                                      Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>java -Xmx256m client 66 live live software members english game0                                        File not found
"Ownage-Pkz 508 Client!"                                                                                                                                        Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>cd files                                                                                                      Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>java -Xmx256m client 66 live live software members english game0                                        File not found
                                                                                Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>cd files                                                                                                      Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>java -Xmx256m client 66 live live software members english game0                                        File not found
Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>cd files                                                                                                      Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>java -Xmx256m client 66 live live software members english game0                                        File not found                                                                                                                                                                                                                                  Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>pause
                                                                                Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>java -Xmx256m client 66 live live software members english game0                                        File not found                                                                                                                                                                                                                                  Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>pause                   Press Return key to continue:
Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>java -Xmx256m client 66 live live software members english game0                                        File not found                                                                                                                                                                                                                                  Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>pause                   Press Return key to continue:
live live software members english game0                                        File not found                                                                                                                                                                                                                                  Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>pause                   Press Return key to continue:
File not found                                                                                                                                                                                                                                  Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>pause                   Press Return key to continue:
                                                                                                                                                                Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>pause                   Press Return key to continue:
                                                                                Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>pause                   Press Return key to continue:
Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>pause                   Press Return key to continue:
Press Return key to continue:

---

### Post by dim3000 on 2010-06-19
> **Simdog1 said:**
> well i put pause at the end and this is what i actually get 
                                                                                Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>#!/bin/bash                   File not found                                                                                                                                                                                                                                  Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>echo "Ownage-Pkz 508 Client!" "Ownage-Pkz 508 Client!"
Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>#!/bin/bash                   File not found                                                                                                                                                                                                                                  Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>echo "Ownage-Pkz 508 Client!" "Ownage-Pkz 508 Client!"                                                                                                                                        Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>cd files
File not found                                                                                                                                                                                                                                  Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>echo "Ownage-Pkz 508 Client!" "Ownage-Pkz 508 Client!"                                                                                                                                        Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>cd files
                                                                                                                                                                Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>echo "Ownage-Pkz 508 Client!" "Ownage-Pkz 508 Client!"                                                                                                                                        Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>cd files                                                                                                      Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>java -Xmx256m cli
                                                                                Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>echo "Ownage-Pkz 508 Client!" "Ownage-Pkz 508 Client!"                                                                                                                                        Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>cd files                                                                                                      Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>java -Xmx256m client 66 live live software members english game0
Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>echo "Ownage-Pkz 508 Client!" "Ownage-Pkz 508 Client!"                                                                                                                                        Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>cd files                                                                                                      Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>java -Xmx256m client 66 live live software members english game0                                        File not found
"Ownage-Pkz 508 Client!"                                                                                                                                        Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>cd files                                                                                                      Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>java -Xmx256m client 66 live live software members english game0                                        File not found
                                                                                Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>cd files                                                                                                      Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>java -Xmx256m client 66 live live software members english game0                                        File not found
Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer>cd files                                                                                                      Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>java -Xmx256m client 66 live live software members english game0                                        File not found                                                                                                                                                                                                                                  Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>pause
                                                                                Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>java -Xmx256m client 66 live live software members english game0                                        File not found                                                                                                                                                                                                                                  Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>pause                   Press Return key to continue:
Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>java -Xmx256m client 66 live live software members english game0                                        File not found                                                                                                                                                                                                                                  Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>pause                   Press Return key to continue:
live live software members english game0                                        File not found                                                                                                                                                                                                                                  Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>pause                   Press Return key to continue:
File not found                                                                                                                                                                                                                                  Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>pause                   Press Return key to continue:
                                                                                                                                                                Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>pause                   Press Return key to continue:
                                                                                Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>pause                   Press Return key to continue:
Z:\home\family\Desktop\RSPS\Ownage-Pkz Ip Changer\files>pause                   Press Return key to continue:
Press Return key to continue:

Why are you running it under wine? Create a script and enter in the code I told you, then place the java file in the same folder. Set the script permissions to execute and then run.

---

### Post by Simdog1 on 2010-06-19
o so i have to create a seperate notepad for the code you gave me? idk what script is so im guessing notepad or gedit

---

### Post by dim3000 on 2010-06-19
> **Simdog1 said:**
> o so i have to create a seperate notepad for the code you gave me? idk what script is so im guessing notepad or gedit

Yes just gedit. Stop using wine (Windows Programs) for anything other than exe's.

---

### Post by doorknob60 on 2010-06-20
Yeah, to clarify, copy and paste that code into a blank text file in gedit, and save it as something like "run.sh". Then, right click on run.sh and go to permissions, and set it as executable, otherwise when you click it it will just open in gedit. After you do that, when you click it it should ask you whether to run it or edit it, choose run, then it should work :)

---

### Post by Simdog1 on 2010-06-20
Tyvm dim for the code and doorknow for making it clearer it works now thanks again!!!

---

### Post by Simdog1 on 2010-06-20
1 more question i doqwnkloaded a diff client and the code is 
@echo off 
cd src 
java -Xmx256m client 1 live live software members english game1  
pause
 what wouldi change that to?

---

### Post by dim3000 on 2010-06-20
Create a new file, say client2.sh
Set its permissions to executable.
Put inside it:

```

#!/bin/bash
cd src
java -Xmx256m client 1 live live software members english game1 
read

```

---

### Post by Simdog1 on 2010-06-21
thanks

---

### Post by dim3000 on 2010-06-21
> **Simdog1 said:**
> thanks

No problem, oh and remember to mark the thread as solved.

---


---
title: "colonization_0.8.0_alpha"
date: 2008-08-11
forum: Gaming &amp; Leisure
---

### Post by personal-data-removed on 2008-08-11
Hi

I am a new user.

I would like to install freecol-0.8.0-alpha-installer.jar, for playing the new alpha version of freecol.

I downloaded the file from: [http://www.freecol.org/download-unstable-version.html](http://www.freecol.org/download-unstable-version.html) to my desktop.

Opened the console, and typed:
root@mycomputer-desktop:~# java -jar freecol-0.8.0-alpha-installer.jar

But it gives an error message:
Unable to access jarfile freecol-0.8.0-alpha-installer.jar

What i am doing wrong ?, what can i do to install the game ?


Thanks in advance for help.

---

### Post by cristo-father on 2008-08-11
cd ~/Desktop

---

### Post by Perfect Storm on 2008-08-11
As cristo-father pointed out you have to execute that commando in the right directory. In your case at Desktop.

cd ~/Desktop

cd = change directory
~ = folder/file in your home directory

cd /home/<username>/Desktop

is the same as

cd ~/Desktop

but way easier.
Thereafter execute the java command. Just remember to have java installed ;)

---

### Post by cristo-father on 2008-08-11
You could also rightclick the file, then click open with other application, after that click use custom command and type in java and to finish cick on open.

---

### Post by personal-data-removed on 2008-08-11
Hi all
Thanks for the help.

When i open console and type: cd ~/Desktop

It appears an error message:
-su: cd: /root/Desktop: File or directory dont exist

The default console line localization is: "root@mycomputer-desktop:~#"
So i believe that i am already in the desktop, right ? the error can not be because of that.

I have java installed, i checked in synaptic.

I tryed: "rightclick the file, then click open with other application, after that click use custom command and type in java and to finish cick on open."  No effect whatsoever.

Then i tryed:
Right click and "open with OpenJDK java runtime", and an installation program appeared, and it installed the game. 

Problem solved.
Thanks all.

**Edited:** 
Also works if i type:  cd ~/Área*
and: java -jar freecol-0.8.0-alpha-installer.jar
I have ubuntu in portuguese, and Desktop = "Área de Trabalho"
(the console should accept the commands in english (console default) and in portuguese (language default), but it seams that is only accepting the portuguese, its a bug)

---

### Post by patrichian on 2009-01-24
> **personal-data-removed said:**
> B] 
Also works if i type:  cd ~/Área*
and: java -jar freecol-0.8.0-alpha-installer.jar
I have ubuntu in portuguese, and Desktop = "Área de Trabalho"
(the console should accept the commands in english (console default) and in portuguese (language default), but it seams that is only accepting the portuguese, its a bug)

I don't think it's a bug, it's just that your desktop folder is not named "desktop" because your ubuntu is portugese. So it's the same command, just a different map. I can't use "cd desktop" either since my desktop folder is called "Skrivbord" (Swedish).

---


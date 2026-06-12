---
title: "please, is there any way to add launcher to .sh files that NEEDS sudo?"
date: 2010-03-25
forum: Desktop Environments
---

### Post by dmdevotee on 2010-03-25
simple question.

i am running ubuntu 9.10. and i want to create a launcher to the script jd.sh

this script is for jDowloader, and it WORKS when in terminal i type:

sudo sh /media/DATOS/LINUX/GNOME/jd.sh

but if in terminal i type:

sh /media/DATOS/LINUX/GNOME/jd.sh

doesn't work, so it need SUDO provileges to run.

and, i don't have to add chmod a+x because it RUNS (i did chmod 777 to the file)

but when i create a launcher with this:


gnome-terminal -x bash /media/DATOS/LINUX/GNOME/jd.sh

or this

gnome-terminal -x sh /media/DATOS/LINUX/GNOME/jd.sh

or this

/media/DATOS/LINUX/GNOME/jd.sh

or this

sh /media/DATOS/LINUX/GNOME/jd.sh

or this

sudo sh /media/DATOS/LINUX/GNOME/jd.sh



doesn't work.

please anybody knows how to make a launcher for a .sh that needs sudo?

---

### Post by l.billon on 2010-03-25
For applications featuring a GUI, or if you want to create a launcher, use **gksudo** instead of sudo.

---

### Post by darthmob on 2010-03-25
You shouldn't need sudo to start jDownloader! My suggestion would be:

sudo chmod +x /media/DATOS/LINUX/GNOME/jd.sh

And just create a normal application launcher with the command being the location of the script (/media/DATOS/LINUX/GNOME/jd.sh). Works perfectly fine for me!

PS: my jdownloader script looks like that:
```
#!/bin/bash

cd /home/davidm/Programme/JDownloader/
java -jar JDownloader.jar
```

---

### Post by dmdevotee on 2010-03-25
> **darthmob said:**
> You shouldn't need sudo to start jDownloader! My suggestion would be:

sudo chmod +x /media/DATOS/LINUX/GNOME/jd.sh

And just create a normal application launcher with the command being the location of the script (/media/DATOS/LINUX/GNOME/jd.sh). Works perfectly fine for me!

PS: my jdownloader script looks like that:
```
#!/bin/bash

cd /home/davidm/Programme/JDownloader/
java -jar JDownloader.jar
```

but my jd.sh scripts looks like:

#!/bin/bash
#JD Installer/Starter Version 0.2
#by Jiaz(JD-Team), [EMAIL="jiaz@jdownloader.org"]jiaz@jdownloader.org[/EMAIL]
#You need at least:
#1.) bash (its a bash script ;) )
#2.) wget 
#3.) Java Version >= 1.5 (OpenJDK works also in latest Version)

#How to use this?
#1.) chmod +x jd.sh
#2.) Place it anywhere you want
#3.) Running jd.sh for the first time will install and setup JD into JDDIR folder
#4.) Running jd.sh after the first time will start JDownloader directly

#Parameters
# update (will perform an update)

#JD Installation folder (adjust to your needs)
JDDIR=/home/dmdevotee/jdownloader
#default path to our install/update tool (DO NOT Change this)
JDINSTALLER=http://update0.jdownloader.org/jdupdate.jar

if [ -e $JDDIR ]
then
if [ "$1" = "update" ]
then
if [ -e $JDDIR/jdupdate.jar ]
then
cd $JDDIR
echo "Start JD-Updater"
java -Xmx512m -jar jdupdate.jar
exit
else
echo "Cannot start JD-Updater: Download/Start JD-Installer"
cd $JDDIR
wget $JDINSTALLER
java -Xmx512m -jar jdupdate.jar
exit
fi
fi
if [ -e $JDDIR/JDownloader.jar ]
then
echo "JD Installation found: Starting JD now"
cd $JDDIR
#java -Xmx512m -jar JDownloader.jar --add-links $1 $2 $3 $4 $5 $6 $7 $8 $9
java -Xmx512m -jar JDownloader.jar
exit
else
echo "JD Installation found: No valid JDownloader.jar exist!"
fi
if [ -e $JDDIR/jdupdate.jar ]
then
cd $JDDIR
echo "Start JD-Updater"
java -Xmx512m -jar jdupdate.jar
else
echo "Cannot start JD-Updater: Download/Start JD-Installer"
cd $JDDIR
wget $JDINSTALLER
java -Xmx512m -jar jdupdate.jar
exit
fi
else
echo "Download/Start JD-Installer"
mkdir $JDDIR
cd $JDDIR
wget $JDINSTALLER
java -Xmx512m -jar jdupdate.jar
exit
fi


and like i said:

> **dmdevotee said:**
> 

and, i don't have to add chmod a+x because it RUNS (i did chmod 777 to the file)

but when i create a launcher with this:


gnome-terminal -x bash /media/DATOS/LINUX/GNOME/jd.sh

or this

gnome-terminal -x sh /media/DATOS/LINUX/GNOME/jd.sh

or this
[COLOR=Red][B]
 /media/DATOS/LINUX/GNOME/jd.sh[/B][/COLOR]

or this

sh /media/DATOS/LINUX/GNOME/jd.sh

or this

sudo sh /media/DATOS/LINUX/GNOME/jd.sh



doesn't work.

please anybody knows how to make a launcher for a .sh that needs sudo?



like you said:

> **darthmob said:**
> 
```
#!/bin/bash

cd /home/davidm/Programme/JDownloader/
java -jar JDownloader.jar
```

i tried this in terminal

cd /home/dmdevotee/jdownloader/

java -jar JDownloader.jar


it doesn't load jdownloader, but a terminal that gets stuck trying to load

---

### Post by dmdevotee on 2010-03-25
> **l.billon said:**
> For applications featuring a GUI, or if you want to create a launcher, use **gksudo** instead of sudo.


thanks! it worked but is asks me for pass.

there would be a way to add this to a list to "execute without ask for pass"

---

### Post by doas777 on 2010-03-25
I think this is what you are looking for:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by conradin on 2010-03-25
```

#!/bin/bash
echo "password"|sudo -S bash
sudo bash
#now Im in as root

```

this will print the password to the screen, but it will also get you into a root user account. I can think of a zillion reasons not to do something like this, but this should work for you. You might have to export the script to refer to it after it logs into a root shell.

---

### Post by darthmob on 2010-03-25
Again, you really shouldn't need sudo to start it! I guess it has to do with that install script which I won't read because it has no formatting whatsoever.

Probably the easiest solution:
- download jdownloader as a zip file (there's a link on the page which says Download ZIP)
- extract it wherever you want it to be
- use a similar script as the one in my previous answer ;)

---

### Post by rnerwein on 2010-03-25
hi
i agree with darthmob - you should not need to run that script as root. it's very gritty to run it as super user. 
just insert in the second line of your script:
[COLOR=Red]set -x [COLOR=Black]
this will cause your shell to run in debug mode and you will exactly see the command wich causes the fault ( i think something with permissions or PATH ).
ciao
[/COLOR][/COLOR]

---

### Post by 0x656b694d on 2010-03-25
dmdevotee, listen to darthmob.
If jDownloader cannot run without being root, you definitely do something wrong.

Looks like jd.sh is just an installer which is expected to write to system paths. But as i can see, it doesn't, since there are your home directories hardcoded (did you do that?). Installers are subjects to be ran once. And after that a program should run with user privileges.

I just tried to do the following:
$ java -jar jdupdate.jar
gui appeared, tons of files was downloaded to the current folder
...output
Local: /media/huge/Distributives/jdownloader
Start java -jar -Xmx512m JDownloader.jar in /media/huge/Distributives/jdownloader
Execute: java -Xmx512m -jar JDownloader.jar -rfu  in /media/huge/Distributives/jdownloader
Errors: 0

$ java -jar JDownloader.jar -rfu
GUI appeared with continuing installation.

I didn't enter my password anywhere. If i wanted to make this program available for other users in the system, i'd copy the JDownloader to the /usr/share/local/ or something (but i don't need this software, sorry).

I guess your problem is just in some folder or jars permissions.

i'm sorry, too many unnecessary words perhaps.

---

### Post by dmdevotee on 2010-03-25
thanks to everybody for the help. i downloaded and used the .zip file instead of the jd.sh file, i only had to extract it and do a shortcut with command "java -jar /home/dmdevotee/JDownloader/JDownloader.jar". no need for sudo.

the problem, was that i tried to do java -jar /home/dmdevotee/JDownloader/JDownloader.jar to the installed by the sh file folder instead of the unextracted from zip file. so, i don't need the sh file anymore

thanks!!

that script was for installing, that's why it only worked with sudo. although it worked for executing too (with the problems)


by the way,its possible to add a shortcut with more than 1 line of command? (i guess no, but...)

---

### Post by doas777 on 2010-03-25
> **dmdevotee said:**
> 
by the way,its possible to add a shortcut with more than 1 line of command? (i guess no, but...)

there are two ways to do it, but I prefer using an external script, that is referenced by the launcher. that way you can put as many lines in the script as you like. the alternative is to put a semicolon between each line.

```

m='hello!'; echo $m

```

---


---
title: "Running KDE apps in GNOME ?"
date: 2006-05-18
forum: Desktop Environments
---

### Post by Paradoxx on 2006-05-18
Hi

When ever i try to run a KDE based program, in this case, katapult and amaroK... i get this error: 

There was an error setting up inter-process communications for KDE. The message returned by the system was: 

Could not read network connection list.
/home/jonas/.DCOPserver_ubuntu_0

Please check that the "dcopserver" program is running!

After the message katapult starts, but runs really strange... and amoraK gives me a error message about missing formats...

Does anyone know how to fix this?

---

### Post by louis_nichols on 2006-05-18
try running in terminal the command

kdeinit

before starting these applications.

---

### Post by Paradoxx on 2006-05-19
[QUOTE=louis_nichols]try running in terminal the command

kdeinit

before starting these applications.[/QUOTE]



Didn't seem to work, i still get the same error message... any other suggestions ?

---

### Post by Oceola on 2006-05-19
I've been running Kstars under Gnome (Hoary and Breezy) for a while now. I don't know if this will help but if you go to the repositories and look at the Kstars package when you mark it for installation it asks to mark a bunch of other files. The list seems limited as far as some of the kde libs and a couple of small utilities. It may be you could download just that list of files, aside from Kstars and maybe your other apps will work. When you installed those other files were their other files which came with them? Look at your history in Synaptics and maybe that might help give you a handle on what changed as well.

---

### Post by Paradoxx on 2006-05-20
[QUOTE=Oceola]I've been running Kstars under Gnome (Hoary and Breezy) for a while now. I don't know if this will help but if you go to the repositories and look at the Kstars package when you mark it for installation it asks to mark a bunch of other files. The list seems limited as far as some of the kde libs and a couple of small utilities. It may be you could download just that list of files, aside from Kstars and maybe your other apps will work. When you installed those other files were their other files which came with them? Look at your history in Synaptics and maybe that might help give you a handle on what changed as well.[/QUOTE]

I've tried installing Kstars... but, i still get the dcopserver error when i try to run amaroK and now also Kstars...

---

### Post by Sef on 2006-05-20
How are you installing the apps?


I use K3b and it installed all the dependencies.

---

### Post by adamkane on 2006-05-20
If you want to run KDE apps, it is best, but not necessary to install kubuntu-desktop:
```

sudo apt-get install kubuntu-desktop

``` 
You will still be using Gnome, but the KDE stuff will work better.

---

### Post by Paradoxx on 2006-05-20
[QUOTE=Sef]How are you installing the apps?


I use K3b and it installed all the dependencies.[/QUOTE]

I'm just using synaptic...

---

### Post by bluevoodoo1 on 2006-05-20
[QUOTE=adamkane]If you want to run KDE apps, it is best, but not necessary to install kubuntu-desktop:
```

sudo apt-get install kubuntu-desktop

``` 
You will still be using Gnome, but the KDE stuff will work better.[/QUOTE]

Or try "kde-core" you won't get the clutter of all the KDE apps, but you might gain some better results with your KDE apps in gnome.

---

### Post by Paradoxx on 2006-05-20
[QUOTE=bluevoodoo1]Or try "kde-core" you won't get the clutter of all the KDE apps, but you might gain some better results with your KDE apps in gnome.[/QUOTE]

Okay... I'll give it a try tomorow

---

### Post by chadk on 2006-05-20
chad@figment:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: kdegraphics-kfile-plugins but it is not going to be installed
E: Broken packages

---

### Post by Ramses de Norre on 2006-05-20
That package is in the main security repo.. I hope you do have this repo enabled for security updates.. 
It's this line, it has to be in /etc/apt/sources.list ```
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

```

---

### Post by Paradoxx on 2006-05-21
[QUOTE=bluevoodoo1]Or try "kde-core" you won't get the clutter of all the KDE apps, but you might gain some better results with your KDE apps in gnome.[/QUOTE]

If i run "sudo apt-get kde-core", the system tells me that the file doesn't exist....

---

### Post by Ramses de Norre on 2006-05-21
sudo apt-get **install** kde-core

---

### Post by bluevoodoo1 on 2006-05-21
[QUOTE=Paradoxx]If i run "sudo apt-get kde-core", the system tells me that the file doesn't exist....[/QUOTE]

You did...

```
sudo apt-get **install** kde-core
```  

correct?

---

### Post by Paradoxx on 2006-05-21
[QUOTE=bluevoodoo1]You did...

```
sudo apt-get **install** kde-core
```  

correct?[/QUOTE]

DO'H ! :)  yes i forgot the "install" part :???:  thanks :)... i'm installing it now

---

### Post by Paradoxx on 2006-05-21
Well... i have installed the kde-core, but it still doesn't work.
But what the hell? i can live with out katapult and amaroK... but can you suggest another music player ?

---

### Post by mmcmonster on 2006-05-21
I'm partial to rhythmbox.  It's not nearly as advanced as amarok, but it's got potential. :)

There was also a [recent thread here]("http://www.ubuntuforums.org/showthread.php?t=159879") about a new player called [Exaile!]("http://www.exaile.org/").

---


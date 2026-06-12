---
title: "Upgrading Azureus"
date: 2006-05-21
forum: Desktop Environments
---

### Post by sabredog on 2006-05-21
Not sure if anyone else is having the same problem but I cannot apply the upgrade patches for Azureus.

The update downloads and then fails on installation as I do not have permission to apply the patch.

Can anyone help me with this at all?

cheers and thanks

---

### Post by jazzmuzik on 2006-05-21
Probably because azureus is intalled systemwide and requires root permissions to upgrade. This is why I've installed my copy in my home directory. No problems with the upgrades that way.

If you want, uninstall the deb version of azureus, create an app directory off your user directory and install the latest version of azureus there.

[http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)

---

### Post by nalgene on 2006-05-22
I have the same problem, is there an easier way then to reinstall it i have tons of torrents seeding.. and dont want to uninstall only to install

---

### Post by sabredog on 2006-05-22
[QUOTE=nalgene]I have the same problem, is there an easier way then to reinstall it i have tons of torrents seeding.. and dont want to uninstall only to install[/QUOTE]

Is there a "how to" around to uninstall Azureus and to install it?

I have got Azureus working well except for permission issues which prevent me from upgrading and adding plug-ins.

cheers and thanks

---

### Post by jazzmuzik on 2006-05-22
You don't actually have to uninstall the systemwide version of Azureus in order to install a local copy, however it's easy to accidently launch the syswide version. 

I'm not going to do an exact step by step here, but generally speaking, to install a local copy, go here [http://sourceforge.net/project/showfiles.php?group_id=84122](http://sourceforge.net/project/showfiles.php?group_id=84122) and get the appropriate version (probably Azureus_2.4.0.2_linux.tar.bz2). Create an 'apps' directory in your Home directory. Extract azureus there. Edit the file 'azureus' (3.1k) and look at the top of the that file. Edit the following and specify the correct paths to 1) the java binary directory, 2) the path to the azureus script:

JAVA_PROGRAM_DIR=""
PROGRAM_DIR=""

Mine looks like this:

JAVA_PROGRAM_DIR="/usr/lib/j2re1.5-sun/bin/"
PROGRAM_DIR="/home/jazzmusik/apps/azureus"

Yours will be slightly different. Your home directory will have your own user name and the java directory will be different if you have a different version of java installed. So verify it with Nautilus or on the command line to be sure. Once you've added the correct information, save and exit. Now try launching your local copy of azureus. You won't find it in the menus, but you can launch it a number of ways: Press Alt-F2, type 'apps/azureus/azureus'. Or from the command line, type ~/apps/azureus/azureus. Or from the file manager (Nautilus) go to apps and then azureus. Double click on 'azureus'.


If you want to uninstall the systemwide copy of azureus, you can do that with Synaptic or on the command line with:

sudo apt-get remove azureus

---

### Post by sabredog on 2006-05-22
Cheers

I will give that a go. Hopefully it will also remove the persistant error:length issue as well :)

---

### Post by ProMaster on 2006-05-22
There is an even easier way. Go to the command line and type sudo azureus and the update will be installed with SU permissions :mrgreen:

---

### Post by jazzmuzik on 2006-05-22
[QUOTE=ProMaster]There is an even easier way. Go to the command line and type sudo azureus and the update will be installed with SU permissions :mrgreen:[/QUOTE]

True. But it's amazing how degraded Linux security has become with these techniques. If we continue on this path we'll end up with Windows and no security at all.

---


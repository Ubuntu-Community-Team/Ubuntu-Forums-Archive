---
title: "Screen resolution &amp; hard drives &amp; wine"
date: 2005-11-02
forum: Desktop Environments
---

### Post by Diod on 2005-11-02
I'm a noob on linux, but since there are some mayor problems with windows here im trying out linux.

I've installed nvidia drivers, but my res. is stuck at 1024x768 , how do i change this? I have installed that nvidia configurator but i cant find it.

Im trying to install wine using apt, but no luck. I've followed the guide on the winehq site but it doesnt work for me.

How can i access my hard drives(other than the one i use for ubuntu) without being root and su-ing in the terminal?(so being able to access my hard drives via nautilus on other accounts then root)
I've tried logging in as root in the terminal, then booting nautilus up and setting the rights up correctly, but it says its read only.

Thank you very much

---

### Post by RAOF on 2005-11-02
System->Preferences->Screen Resolution will allow you to change resolutions.

Visit the [wiki]("https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29") for setting up your hard drives.

As for wine, what error messages did you get?  It's kind of hard to help with only "It didn't work" ;)

---

### Post by Diod on 2005-11-02
Solved hard drives myself now ;) yay

I already did the screen res. thing but it only includes up to 1024x768. I've edited xorg.conf, but it doesnt include the resolution :( 

As for the wine, i've downloaded it with apt, ran the winesetuptk file in usr/bin and did everything, but i cant find it. /.wine/ doesnt exist nothing exists of wine, only its installer

---

### Post by manicka on 2005-11-02
To install wine

Run

```
sudo gedit /etc/apt/sources.list
```


add these two lines two your souces.list

```
deb http://wine.sourceforge.net/apt binary/ 
deb-src http://wine.sourceforge.net/apt source/
```


now update and install wine

```
sudo apt-get update
sudo apt-get install wine
```

---

### Post by frodon on 2005-11-02
For display configuration see the [heimo's guide]("http://www.ubuntuforums.org/showthread.php?t=83973"), you need to specify your horizontal and vertical refresh rate in your xorg.conf file, then the resolution problem will be solved.

To install wine in a easy way, open synaptic and search the wine package and the wine-setuptk (or something like that, not sure of the name) package and install them.
After that open a terminal and run winesetuptk, it will allow you to configure wine in a graphical way.

To use other partition as a simple user you need to add the **rw,user** parameters in the line you use in the fstab file. So if you know the name of your partition (/dev/hda0 for example) add a line like that in the fstab file (sudo gedit /etc/fstab to open it) : ```
/dev/hda0 /media/my_partition auto rw,user,noauto 0 0
```/dev/hda0 is the name of the partition and /media/my_partition is the folder where you will mount your partition you can choose the folder you want, generally users mount their partition in /media or /mnt.

Feel free to ask for more details.

---

### Post by RAOF on 2005-11-02
To include enable more screen resolutions, you can run
```
sudo dpkg-reconfigure xserver-xorg
```
One of the questions will be "what resolutions do you want to be able to run" :)

For the rest of the questions, you can pretty much safely use the default answers.  But still read the questions ;)

Edit:  Woah, too slow!  Read heimo's guide.  It's got all the stuff.

---

### Post by Diod on 2005-11-02
Ive installed wine, but i dont see it in my applications list.
I can only find it in /usr/bin

---

### Post by manicka on 2005-11-02
You won't see wine in your menus. Wine is a program that you use install and run other programs. If you want to see the configuration panel for wine, run the command 

winecfg

---

### Post by Diod on 2005-11-02
winecfg only works half. it cant find drives and im unable to successfully add drives

this is what the terminal says when i run winecfg and try to add drive c:

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/diod', starting in the Windows directory.

---

### Post by Diod on 2005-11-02
Does anyone know how to solve this(bump)?

---

### Post by Diod on 2005-11-02
Bump?

---

### Post by Diod on 2005-11-02
Ive reinstalled it a dozen times, but it wont help.
It still says this when running winecfg:

> Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/diod', starting in the Windows directory.
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '../drive_c'
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '../drive_c'


---

### Post by Diod on 2005-11-02
EDIT: wrong post sry

---

### Post by Diod on 2005-11-02
bump

---

### Post by dcstar on 2005-11-02
[QUOTE=Diod]Ive reinstalled it a dozen times, but it wont help.
It still says this when running winecfg:[/QUOTE]

Before you reinstall rename the (hidden) ".wine" directory in your Home drive.

I say rename as you might have existing configuration data in there, then you can copy it back to the new ".wine" directory (if necessary).

You may not actually have to do a "reinstall", just do the rename and run wine from your user terminal, then try winecfg.

---

### Post by xequence on 2005-11-02
[QUOTE=Diod]bump[/QUOTE]

Im not a mod but I do know that on most sites spamming to put your thread up higher is not allowed :P

---

### Post by Diod on 2005-11-02
YEAH! THANKS!
Woot
to think its so easy..
All there was was to ren the .wine folder and run wine and winecfg as u said
wow thank you all! :p

EDIT: xequence i know, but ive been on it from yesterday and it was really starting to **** me off.

---

### Post by dcstar on 2005-11-02
[QUOTE=Diod]YEAH! THANKS!
Woot
to think its so easy..
All there was was to ren the .wine folder and run wine and winecfg as u said
wow thank you all! :p
......[/QUOTE]
No worries, those little "gotcha's" can be frustrating until you find 'em....    ;)

---

### Post by DarkKnight on 2005-12-11
[QUOTE=Diod]Does anyone know how to solve this(bump)?[/QUOTE]

You need to enable your dos drives.

Do this in a console: 

rm -R ~/.wine
wine

Wine will auto matically setup your dosdrives, do not use a tool like winsetup. :)

EDIT: Sorry, didn't see the above post.

---


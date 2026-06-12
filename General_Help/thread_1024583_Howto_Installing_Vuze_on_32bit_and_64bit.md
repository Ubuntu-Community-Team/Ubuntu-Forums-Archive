---
title: "Howto: Installing Vuze on 32bit and 64bit"
date: 2008-12-29
forum: General Help
---

### Post by StevenHarper on 2008-12-29
Vuze (formally Azureus) is not available as a standard deb.

These instructions will get you up and running on 32bit and 64bit ubuntu.


**Install Java**

[INDENT]If you don't have it you will need java 1.6 or better
to find your current version open a terminal

```
java -version
```

if you don't have at least 1.6 run this command to get it

```
sudo apt-get install openjdk-6-jre
```[/INDENT]


**Download the Vuze file**

[INDENT]Vuze_Installer.tar.bz2

from 

[http://www.vuze.com/Download.html](http://www.vuze.com/Download.html)


Right Click on the file and choose

Extract Here


A new directory has been made vuze

Move this to where you want vuze to live

I use /home/steven/apps/vuze

[/INDENT]

**64bit Step - Update the SWT.jar**

[INDENT]Download the 64bit swt.jar from the eclipse project

[http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/R-3.4-200806172000/swt-3.4-gtk-linux-x86_64.zip](http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/R-3.4-200806172000/swt-3.4-gtk-linux-x86_64.zip)

you get this file

swt-3.4-gtk-linux-x86_64.zip

Right click and extract the file

now enter the directory 

swt-3.4-gtk-linux-x86_64

copy the swt.jar over the app/vuze/swt.jar
[/INDENT]

**Starting Vuze**
[INDENT]
Now you are ready to start Vuze. We will do this on a terminal to test it works

```
cd apps/vuze/
./vuze
```

Ok if it all works now all we need to do is create a nice Launcher

Right click on your top panel

[LIST]
[*]choose Add to Panel
[*]choose Custom Application Launcher
[/LIST]

[LIST=1]
[*]Click on the icon (spring thing) and browse to the apps/vuze directory
[*]Click OK
[*]Pick the nice blue frog icon
[*]Enter the Name : Vuze
[*]Click Browse
[*]broswe to the apps/vuze , choose the file vuze
[/LIST]

Your done!
[/INDENT]

---

### Post by StevenHarper on 2008-12-29
After spending some time with Vuze I am very impressed.

I have spotted one feature that I thought worthy of a repost.

Vuze actually comes with a Upnp Media Server, this means that if you check the box (publish media to the local network - its on the plug-ins (mediaserver) panel in options), then you can see all the video's and music and photo's on any compatible devices.

I have just tested this on my PS3, I stuck a divx in the directory and it appears in the Media Server that has appeared in my PS3 menu - very nice.

I expect this works very similar with XBox 360's etc.

---

### Post by Gondee on 2008-12-29
Stupid question but, when I look for the icon in the directory i can not see anything, just the plug-in folder, but no icon or picture. And, when i look for the launcher, the Vuze thing, and select it, and try to launch it, it says you do not have permissions.  

What should I do?

---

### Post by StevenHarper on 2008-12-29
You don't see any icons until you have selected the blank directory (./vuze)
Then you get a list of icons in that directory.

Can you give me the output of when you start vuze on a terminal

Open a terminal

```
cd apps/vuze
./vuze
```

---

### Post by Ape3000 on 2008-12-29
Just download the deb-file here: [http://www.getdeb.net/app/Vuze](http://www.getdeb.net/app/Vuze)

---

### Post by StevenHarper on 2008-12-29
You will still need to replace the swt.jar if your on a 64bit version of Ubuntu (if you use the deb from getdeb)

---


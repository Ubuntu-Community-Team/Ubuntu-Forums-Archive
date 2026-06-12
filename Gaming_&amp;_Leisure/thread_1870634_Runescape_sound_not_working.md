---
title: "Runescape sound not working"
date: 2011-10-27
forum: Gaming &amp; Leisure
---

### Post by Dradgen on 2011-10-27
The sound in Runescape used to work until just recently.  I have searched for and read the 'sound problems' for runescape posts on this site, and other sites, but cannot find a solution that works for me.

I am running version 10.04 lucid lynx

---

### Post by grungedoobie on 2011-10-27
Running Ubuntu 10.04 and got the same here.  Not a software person, but it seems Java has made a few tweaks.  This happens fairly often.  OpenJDK I'm sure will adjust in time.

Or, if you want to go the other route, and get SunJava, here's a page for doing that:

## Begin Edit

You may not have to, but before installing Sun's JRE, I disabled IcedTea from Firefox, then removed the two IcedTea components with Synaptic.  Reason, having the IcedTea and the Sun plugin's installed at the same time has caused problems for me in the past.

## End Edit

[http://www.clickonf5.org/7777/how-install-sun-java-ubuntu-1004-lts/]("http://www.clickonf5.org/7777/how-install-sun-java-ubuntu-1004-lts/")

## Begin Excerpt from previous link

sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin
sudo update-alternatives --config java

## End Excerpt from previous link


Funny thing about the partner repo.  The "add-apt-repository" command didn't work for me, so I added the repo using Synaptic, then went back to Terminal and finished the last three steps.

After installing SunJava and using the fourth command to select SunJava by default, I rebooted and Runescape sound is running again.  You may not have to reboot, but I like to do that on occasion for a fresh start.  :)

Have fun whichever you chose.  :)

The Grunge

Side Note:  The only problem I've found with installing SunJava (and the like) is that it doesn't always update by itself.  If it quits working you can usually do a manual update and get it running again.  Of course, I've not had that happen in a very long time.

---

### Post by kaldor on 2011-10-27
Yep. Gonna want to use the official Java for any gaming. OpenJDK is *almost* good enough for my needs, but still does not behave nicely enough to use on a regular basis.

---

### Post by R4V4N4 on 2011-10-28
people still play runescape?

---


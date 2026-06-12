---
title: "Java Problem, Runescape"
date: 2010-04-17
forum: Gaming &amp; Leisure
---

### Post by FireStorm102389 on 2010-04-17
ok, I go to play RS and I can only get it in safe mode.  Whenever i go to try and set it in HD the java window goes white and nothing happens, and it won't even go in standard mode. I have no idea why this is.  I went and installed java from the terminal...I don't know why it can't do updates.  This is the entire report when I went to install it.


[PHP]david@David-desktop:~$ sudo apt-get install sun-java6-plugin ; sudo update-java-alternatives -s java-6-sun
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libaccess-bridge-java-jni libaccess-bridge-java icedtea-6-jre-cacao
  openjdk-6-jre-headless tzdata-java libjline-java openjdk-6-jre-lib rhino
  ca-certificates-java
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  sun-java6-bin sun-java6-jre
Suggested packages:
  sun-java6-fonts ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho
  ttf-sazanami-mincho ttf-arphic-uming
The following NEW packages will be installed:
  sun-java6-bin sun-java6-jre sun-java6-plugin
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/35.5MB of archives.
After this operation, 101MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package sun-java6-jre.
(Reading database ... 132188 files and directories currently installed.)
Unpacking sun-java6-jre (from .../sun-java6-jre_6-15-1_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-bin.
Unpacking sun-java6-bin (from .../sun-java6-bin_6-15-1_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-plugin.
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-15-1_i386.deb) ...
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Setting up sun-java6-bin (6-15-1) ...
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/ControlPanel to provide /usr/bin/ControlPanel (ControlPanel) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/java_vm to provide /usr/bin/java_vm (java_vm) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/javaws to provide /usr/bin/javaws (javaws) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/jcontrol to provide /usr/bin/jcontrol (jcontrol) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/policytool to provide /usr/bin/policytool (policytool) in auto mode.
update-binfmts: warning: current package is openjdk-6, but binary format
already installed by sun-java6 

Setting up sun-java6-jre (6-15-1) ...

Setting up sun-java6-plugin (6-15-1) ...

update-alternatives: error: no alternatives for appletviewer.
update-alternatives: error: no alternatives for apt.
update-alternatives: error: no alternatives for extcheck.
update-alternatives: error: no alternatives for HtmlConverter.
update-alternatives: error: no alternatives for idlj.
update-alternatives: error: no alternatives for jar.
update-alternatives: error: no alternatives for jarsigner.
update-alternatives: error: no alternatives for javac.
update-alternatives: error: no alternatives for javadoc.
update-alternatives: error: no alternatives for javah.
update-alternatives: error: no alternatives for javap.
update-alternatives: error: no alternatives for java-rmi.cgi.
update-alternatives: error: no alternatives for jconsole.
update-alternatives: error: no alternatives for jdb.
update-alternatives: error: no alternatives for jhat.
update-alternatives: error: no alternatives for jinfo.
update-alternatives: error: no alternatives for jmap.
update-alternatives: error: no alternatives for jps.
update-alternatives: error: no alternatives for jrunscript.
update-alternatives: error: no alternatives for jsadebugd.
update-alternatives: error: no alternatives for jstack.
update-alternatives: error: no alternatives for jstat.
update-alternatives: error: no alternatives for jstatd.
update-alternatives: error: no alternatives for mozilla-javaplugin.so.
update-alternatives: error: no alternatives for native2ascii.
update-alternatives: error: no alternatives for pluginappletviewer.
update-alternatives: error: no alternatives for rmic.
update-alternatives: error: no alternatives for schemagen.
update-alternatives: error: no alternatives for serialver.
update-alternatives: error: no alternatives for wsgen.
update-alternatives: error: no alternatives for wsimport.
update-alternatives: error: no alternatives for xjc.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/HtmlConverter
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/java-rmi.cgi
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc
david@David-desktop:~$ 
[/PHP]

---

### Post by EarthMind on 2010-04-17
Try installing the latest JRE from the Java website. That's what I always do.

---

### Post by FireStorm102389 on 2010-04-18
I downloaded the JRE from the site, but its a .bin file and I don't know how to go about:

1: changing directories in the terminal to get to the folder with the file in it.

2: How to install a .bin file

please help, thank you :D

---

### Post by EarthMind on 2010-04-18
I've written a tutorial which covers both the 64 and 32 bit environments.
Check it out: [http://ubuntuforums.org/showthread.php?t=1437100](http://ubuntuforums.org/showthread.php?t=1437100)

---

### Post by blazemore on 2010-04-19
As I understand it, ATI's proprietary driver is not ready to run with the new version of X Server that 10.04 has received. An excerpt from one of the beta known issues: 

"The fglrx binary driver for ATI video chipsets does not yet support the X server in Lucid. As a workaround, users should use the open source -ati driver instead." 

Unfortunately the open source drivers can't quite play RS yet, so you may be stuck until AMD releases another driver.

---

### Post by FireStorm102389 on 2010-04-25
thank you for all your input, its quite informative!!

---

### Post by rasmus91 on 2010-05-03
did anyone get this working?

---

### Post by Sharft 6 on 2010-05-03
I've just finished reinstalling ubuntu cause I installed the driver from ati's website and it really doesn't work well with desktop effects. Also sometimes I would get openGL flicker which is pretty anoying. I had problems trying to remove the driver so I ended up reinstalling ubuntu and have decided not to do that again :P. I will reserve all my gaming for windows.

for the record I did get rsHD working but it's not worth it imo

---

### Post by rasmus91 on 2010-05-04
> for the record I did get rsHD working but it's not worth it imo

but mine doesn't even work in Standard detail.

---

### Post by Sharft 6 on 2010-05-04
> **rasmus91 said:**
> but mine doesn't even work in Standard detail.

yeah I never got it working in standard detail either. just safemode and high detail

---

### Post by rasmus91 on 2010-05-04
What about high detail? how did you do that?

---

### Post by Sharft 6 on 2010-05-04
This is when I was brand new to ubuntu a few days ago
1. Installed ubuntu restricted extras (I think OpenJDK and Icedtea browser plugin is all you need)
2. Installed ati propriatary drivers from the ati website. (This gives me openGL flicker, increased boot time by about 5 seconds, slow maximize times with desktop effects enabled and a few other little anoying gnome glitches.)

And thats it. rsHD works but sometimes doesn't load, won't allow tabbed browsing, sometimes doesn't position the applet in the right place and the applet flickers as all openGL things would do this regularly.

Mind you I have a radeon 4850 rv770. As I understand it, the open source radeon drivers that come with ubuntu support all radeon cards 3d acceleration except the rv6xx and rv7xx (radeon 3xxx and 4xxx). radeon 5xxx is not supported at all yet I don't think. i.e. if you have anything less than a radeon 3xxx then I think rsHD should work with the built open source radeon driver.

---

### Post by rasmus91 on 2010-05-05
> Mind you I have a radeon 4850 rv770. As I understand it, the open source radeon drivers that come with ubuntu support all radeon cards 3d acceleration except the rv6xx and rv7xx (radeon 3xxx and 4xxx). radeon 5xxx is not supported at all yet I don't think. i.e. if you have anything less than a radeon 3xxx then I think rsHD should work with the built open source radeon driver.


Oh yeah. Well i have a Intel GMA 4500 MHD, so i kind of drew the short stick, I've heard a lot of people being able to play rsHD with the intel cards, but so far i've found no guide to how.

---

### Post by Sharft 6 on 2010-05-05
oh yea the only thing i've heard about intel graphics is that they're severely underpowered :(

---

### Post by blazemore on 2010-05-05
> **Sharft 6 said:**
> oh yea the only thing i've heard about intel graphics is that they're severely underpowered :(

Not with the beautiful new Core i5 and i7s. They're enough to play older titles like Half Life 2, Doom 3 and even Oblivion at respectable resolutions (1680x1050), albeit without anti-aliasing.
Even the Core i3s can pack enough punch to drive 1080p video in a media centre.

---

### Post by darkforester67 on 2010-05-05
Still having same probleam, try this
1. Go to software center 
2. In search type in sun java 6.0 plugin
3. Download it
4. Open runescape and put the following settings

Cpu usage: High or normal depends on your cpu the higher the more smooth the game will be
Ground decoration: On
Flickering effects: Optional
Scenery shadows: Dynamic
Water detail: High
Then put anti-aliasing to x4
and complete the rest 
Hope it works :D

Btw whats your screen resolution and whats it set to on rs ? are you trying to do fullscreen or standard?

---

### Post by rasmus91 on 2010-05-06
Resizeable...

> Then put anti-aliasing to x4

On a intel GMA 4500??

Have you ever used one of those?

Tried to go to HD to even be able to put those settings on. rs doesn't even load, check image below.

---

### Post by blazemore on 2010-05-06
OK it kind of works. Flickers with Compiz on, and sometimes this happens:

---

### Post by darkforester67 on 2010-05-06
maybe this could help got it from runescape forums 

@Popebenedic 
Just a note, the jdk is the java development kit, which  is generally used if you are programming related to java. I think you  only want to jre package (java runtime environment), make sure you have  that package. 
 
I myself haven't tried running java/runescape on  Lucid 10.04 yet, as i'm currently running Sabayon Linux (about to switch  to arch soon). As for ATI cards i don't have a clue, all i know is that  nVidia works for me with jre 6 update 19 
 
00:0d.0 VGA  compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce  430] (rev a2) 
 
To find your exact card like above, type enter  the command: 
(where $ denotes a command as user) 
    
   $  lspci | grep "VGA" 
 
You may want to do a google search or check  the ubuntu forums for any help regarding your card. Chances are somebody  else has already solved the same problem. 
 
@apostrophe 
Yes i  always encounter this, you can get around this problem by using a  window manager such as fluxbox or enlightenment (which is epic for  playing runescape fullscreen, lightwieght WM's are always a plus when  playing games) 
 
You could also change your GNOME panel  properties to autohide or enable buttons which you can send them to the  edge of the screen. 
 
 
Could it be the Ati drivers?

---

### Post by rasmus91 on 2010-05-07
> maybe this could help got it from runescape forums 

didn't really...

Thought about trying it on a lightweight environment though, perhaps that could do the trick.

---


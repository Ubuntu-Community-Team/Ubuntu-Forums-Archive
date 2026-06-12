---
title: "Eclipse on Breezy, difficulty setting breakpoints"
date: 2005-12-28
forum: Desktop Environments
---

### Post by tedk on 2005-12-28
I've been trying to run Eclipse on Ubuntu (Breezy) and have not been successful. I've put in a lot of effort and now really need some help.

I've read several forum entries that describe my problem or one similar but either I don't understand the solution or it doesn't work for me.

I have installed Eclipse and it runs simple Java programs. I have Eclipse Version 3.1.1. I got it by running gnome-app-install and choosing Eclipse under Programming.

The first problem I got was that I could not stop at a breakpoint. I get the message "Cannot connect to VM." 

There are several posted suggestions here about what to do (in response ot other posters not me); the best seemed to be 
<start quote>
Originally Posted by baRRacuda
The best is to download Sun's jre and jdk from [http://java.sun.com](http://java.sun.com) and eclipse from [http://www.eclipse.org](http://www.eclipse.org) (the one in the repos seems to have problems). I just extracted the eclipse archive file, it works fine without any configuration...
<end quote>

So I went to the sun site (which seems to be giving difficulty today? I get 404 errors although I can download elsewhere just fine; I did get the eclipse from eclipse.org but not yet installed it). I was able to get a file called j2eesdk-1_4_02_2005Q2-linux.bin but when as root I typed
./j2eesdk-1_4_02_2005Q2-linux.bin
I got
./j2eesdk-1_4_02_2005Q2-linux.bin: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

Again, a similar issue appeared in the forum leading me to once again go into the Synaptic Packet Manager and choose to install libstdc++6-dev. This install seemed to go OK, but I still get the same error.

I'm new to Ubuntu -- I got turned on to it by attending Jeff Waugh's talk when he came to town. I installed form the CDs he handed out. And it has been fun, but I'm stuck and I really need to get some work done.

Is anyone successfully running Eclipse, setting breakpoints and all on Breezy? Can you tell me how you did it? Thanks.

 -Ted

---

### Post by timetunnel on 2005-12-29
I have never tried the free Java that ubuntu installs but immediately switched to Sun's Java, and breakpoints in Eclipse are working on my machine with Breezy. Here's how I installed it:

[LIST=1]
[*]installed the packages for Eclipse with Synaptic Package Manager
[*]installed Sun's Java following the instructions here: [Install Sun's Java]("https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca") (the resulting package is named sun-j2sdk1.5 on my system)
[*]installed package "galternatives" with Synaptic, started it with "sudo galternatives", located "java" in the "alternatives" on the left side and chose the appropriate java version
[/LIST]

running eclipse:
```
eclipse -vm /usr/lib/j2sdk1.5-sun/
```

If you want to update eclipse with its built-in update feature, do:
```
gksudo "/usr/bin/eclipse -vm /usr/lib/j2sdk1.5-sun/"
```
then go to "Help->Software Updates" in Eclipse

---

### Post by tedk on 2005-12-29
Thanks, timetunnel. I'm now stopping at breakpoints and looking at variables. Admittedly, I've started with just a helloworld program, but I'm on my way.

I took your advice and installed the SUN Java (jdk-1_5_0_06-linux-ir86.bin), following the instructions on the Restricted Formats section of the Ubuntu Wiki. The installation went fine.

```

chmod a+x jdk-1_5_0_06-linux-ir86.bin
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jdk-1_5_0_06-linux-ir86.bin
sudo dpkg -i sun-j2rel.5_1.5.0+update06_i386.deb

```

Then I deviated from your suggestions a little (I hope this doesn't bite me later).  Under WIndows/Preferences in Eclipse, I added and checked j2sdk1.5-sun. Also (I don't know if this is necessary given the checkmark) I added  .eclipse/eclipserc in my home with contents JAVA_HOME=/usr/lib/j2sdk1.5-sun/

I did not update eclipse from eclipse.,org. I used what came with Synaptic.

When running my app, I first did a Project/Clean.

As far as I can tell, eclipse is working as expected. 

So, next time you're in the States, dinner's on me.

 -Ted

---

### Post by timetunnel on 2005-12-29
Good to hear that it worked. As for the deviation you made from my suggestions: should be no problem, I guess. But I'm quite new to Eclipse as well. 

I've used Eclipse's internal update feature for some time now without problems. Furthermore, I've installed some additional plugins that are not in the ubuntu repositories this way. Though this is kind of "bypassing" ubuntu's update mechanism it works because Eclipse is designed to run without any kind of installation. The ubuntu packages do almost the same as you do if you download Eclipse from eclipse.org and unzip it to a folder.  

Ok, anyway. I'd like some self-made pasta then :D 

Cheers
Jens

---


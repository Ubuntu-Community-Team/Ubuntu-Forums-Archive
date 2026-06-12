---
title: "Minecraft broke"
date: 2012-09-03
forum: Gaming &amp; Leisure
---

### Post by OyabanKyuubi on 2012-09-03
Okay so I know what Updated that screwwed me over on minecraft and this seems to be the best place to figure out how to fix it

icedtea-netx_1.2-.ubuntu1.2 
icedtea-netx-common_1.2-2ubuntu1.2 
icedtea-7-plugin_1.2-2ubuntu1.2

all updated yesterday.

before they updated Miecraft worked fine now My chests are half chests (only lid) and a city CTD me out of the game completely

Please help me roll back I tried sudo dpkg -i and got this

dpkg: error processing icedtea-netx_1.2-.ubuntu1.2 (--install):
 cannot access archive: No such file or directory
dpkg: error processing icedtea-netx-common_1.2-2ubuntu1.2 (--install):
 cannot access archive: No such file or directory
dpkg: error processing icedtea-7-plugin_1.2-2ubuntu1.2 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 icedtea-netx_1.2-.ubuntu1.2
 icedtea-netx-common_1.2-2ubuntu1.2
 icedtea-7-plugin_1.2-2ubuntu1.2

Earlier I tried removing and reinstalling them fom the .Debs i have but they auto update immediately.

Please help this is making my computer really act odd and annoying and its frustrating that I cant get it to work

---

### Post by Bashing-om on 2012-09-03
--kyuubie;

  A quick search of the repositories did not get any results for "icedtea-netx_1.2-.ubuntu1.2" ...how did you install them ?

As this thread is very old .. suggest you start a new post with the updated info to get a faster/better response.


[INDENT]regards <==BDQ
[/INDENT]

---

### Post by OyabanKyuubi on 2012-09-03
> **Bashing-om said:**
> --kyuubie;

  A quick search of the repositories did not get any results for "icedtea-netx_1.2-.ubuntu1.2" ...how did you install them ?

As this thread is very old .. suggest you start a new post with the updated info to get a faster/better response.


[INDENT]regards <==BDQ
[/INDENT]

icedtea-netx (1.2-2ubuntu1.2) as it appears in the Ubuntu software center history I google searched icedtea-netx (1.2-2ubuntu1.1) as that was the last file... and i jsut rolled back all of my uploads from yesterday and no go on it being fixed :/ so idk what to do now

---

### Post by OyabanKyuubi on 2012-09-03
Yesterday... or more like this morning my system updated these files before hand my minecraft was working peachy keen.

Now then after the updates all my chests are half chests only showing lids and I CTD wheneve i enter a major city... please help me fix it.

I tried rolling back everything to what it was before and that didnt fix it and I dont know what else to do

---

### Post by coffeecat on 2012-09-03
@OyabanKyuubi, I've moved your two posts (+reply) that you made by resuscitaing an old thread into the new thread you just started, because they all appear to be about the same update problem. Posts will appear in chronological order. Please do not post to old, dead threads, and please do not post about the same issue in different parts of the forum. This dilutes community effort.

---

### Post by OyabanKyuubi on 2012-09-03
thanks coffeecat :) now to just get an answer :(

---

### Post by sffvba[e0rt on 2012-09-03
*Thread moved to **Gaming & Leisure**.*


404

---

### Post by OyabanKyuubi on 2012-09-04
Thanks again >.<

---

### Post by drmrgd on 2012-09-04
First, I'm not sure what command you issued.  By the looks of it, you're using the wrong package name.  However, I can't be sure what you're inputting.  I'm also not sure if you're trying to update the packages or trying to remove them.

If you want to find out the versions and exact package name of Icetea, try:

```
sudo dpkg -l | grep icedtea
```

That will tell you what versions of Icedtea you have installed on your system, and what the package name is.

Also, I've been running with Oracle Java 7 for some time now, and have had absolutely no problems whatsoever in Minecraft.  You might just try to install it to see how it works for you.  Have a look at the Ubuntu Community Documentation on how to install it (use the "Using webupd8.org's strikingly simple method" link in the Oracle Java 7 section):

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Also have a look at the "Choosing the default Java to use" section.  That will explain how to install multiple versions of java and how to easily switch between which is the default used.  You might that helpful as well.

Hope that helps!

---

### Post by OyabanKyuubi on 2012-09-04
> **drmrgd said:**
> -snip-

Okay on this to help you out >.<

#1 I Used the Sudo dkpg -1 On my java to ty to downgrade it and got back that slew of errors of cant find the items.

#2 minecraft was working fine until the most recent Iced tea update that dropped a couple days ago which is why I was trying to down grade again.

#3 Since stating this I did downgrade everything showing in the attachment Picture outside of Google Chrome stable which wont let me downgrade and when I did it Still was broke which confuses me because downgrading everything should have rolled me back to befoe updating a few days ago.


INGAME:

what I am now experiencing in game Now (ie not what it was a few days ago)

Minecraft chests only appear as lids.

Going into the city of darkstar on this server mc.seductivecraft.com Crashes me to desktop completely killing my game due to Java failure.

Edit:

Updated to Java 7 now as you link showed and I tied starting up MC now I have a black screen

heres what terminal says


Exception in thread "Thread-3" java.lang.UnsatisfiedLinkError: /home/meow/.minecraft/bin/natives/liblwjgl.so: /home/meow/.minecraft/bin/natives/liblwjgl.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary1(ClassLoader.java:1939)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1864)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1825)
	at java.lang.Runtime.load0(Runtime.java:792)
	at java.lang.System.load(System.java:1059)
	at org.lwjgl.Sys$1.run(Sys.java:69)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.lwjgl.Sys.doLoadLibrary(Sys.java:65)
	at org.lwjgl.Sys.loadLibrary(Sys.java:81)
	at org.lwjgl.Sys.<clinit>(Sys.java:98)
	at net.minecraft.client.Minecraft.F(SourceFile:1857)
	at aof.<init>(SourceFile:20)
	at net.minecraft.client.Minecraft.<init>(SourceFile:77)
	at anw.<init>(SourceFile:36)
	at net.minecraft.client.MinecraftApplet.init(SourceFile:36)
	at net.minecraft.Launcher.replace(Launcher.java:136)
	at net.minecraft.Launcher$1.run(Launcher.java:79)

Edit: found another help thing went though it got it up and its fixed now :# dont know what happened to fix it but thanks anyways

---

### Post by OyabanKyuubi on 2012-09-04
Back again and this time with a sceen shot this is what my treasure chests look like please help

---

### Post by drmrgd on 2012-09-04
Do you see this with all texture packs or just this one?  I've not seen this before, but I also have not used whatever texture pack you're using.

---

### Post by OyabanKyuubi on 2012-09-05
> **drmrgd said:**
> Do you see this with all texture packs or just this one?  I've not seen this before, but I also have not used whatever texture pack you're using.

nope figured it out with the help of an in game mc pro Optifine was doing this

Optifine is a mod thats supposed to allow HD texture packs and boost FPS but now you see what it does.

---


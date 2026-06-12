---
title: "Minecraft - System crashes to white screen"
date: 2014-11-08
forum: Gaming &amp; Leisure
---

### Post by SirMoo on 2014-11-08
I occasionally enjoy playing minecraft with friends... However I've started experiencing an issue that makes it pretty much unplayable. 

When I'm on the surface of the map after a period of time my game seems to crash to a white screen. It appears to be related to the day/night cycles as it tends to do this when it's switch from one to the other... But this could be purely coincidence. If I am underground (completely enclosed by at least 2-3 blocks) I can play for as long as I like. But if I go to the surface, my time is generally limited (and inconsistent) before I have to do a hard restart of my computer. 

I'm using Ubuntu 14.04
NVIDIA drivers are 331.38. 
Problems persists in both Oracle and Open Java. 
System has adequate RAM. 
Minecraft logs don't seem to say anything out of the normal and I'm not really sure what to look for in /var/logs (if anything) to try and figure out where to start.

This often happens to me when playing WoW but that is through Wine and this isn't... So I'd assume no relation. 

Any help would be wonderful.

---

### Post by dannyboy79 on 2014-11-11
how are you starting minecraft, whats the exaxt command?  have you attempted to use any other nvidia driver versions? what graphics card do you have?

---

### Post by SirMoo on 2014-11-11
Just right clicking on the .jar and selecting java. I've also ran the jar with just java then the path. 

I've not used any other graphics drivers because I was under the impression that 331.38 was much better than 304.117

Graphics card is GeoForce GTX 570

---

### Post by dannyboy79 on 2014-11-11
check this out here: [http://www.minecraftforum.net/forums/support/unmodified-minecraft-client/tutorials-and-faqs/1871637-tutorial-allocate-more-memory-for-minecraft](http://www.minecraftforum.net/forums/support/unmodified-minecraft-client/tutorials-and-faqs/1871637-tutorial-allocate-more-memory-for-minecraft)

and i use this ppa for my nvidia driver: [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

---

### Post by SirMoo on 2014-11-11
> **dannyboy79 said:**
> check this out here: [http://www.minecraftforum.net/forums/support/unmodified-minecraft-client/tutorials-and-faqs/1871637-tutorial-allocate-more-memory-for-minecraft](http://www.minecraftforum.net/forums/support/unmodified-minecraft-client/tutorials-and-faqs/1871637-tutorial-allocate-more-memory-for-minecraft)

and i use this ppa for my nvidia driver: [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

It's not a memory problem as I've allocated 5 gigs and it uses no where near that. 

How do I go about checking if those drivers will be stable with my card without actually installing them? Or if I added the PPA will it simply not give me the driver as an option if it's not compatible?

---

### Post by dannyboy79 on 2014-11-12
you can check the nvidia website for compatibility but according to here: [http://www.nvidia.com/Download/driverResults.aspx/78469/en-us](http://www.nvidia.com/Download/driverResults.aspx/78469/en-us)  the GTX 500 series is compatible with both versions of the driver provided by that PPA.

---

### Post by SirMoo on 2014-11-12
> **dannyboy79 said:**
> you can check the nvidia website for compatibility but according to here: [http://www.nvidia.com/Download/driverResults.aspx/78469/en-us](http://www.nvidia.com/Download/driverResults.aspx/78469/en-us)  the GTX 500 series is compatible with both versions of the driver provided by that PPA.

I've now tried both and it's not solved the issue. 

So updated graphics drivers haven't fixed it. 
It happens regardless of which Java I use (Oracle/Open)
Redownloading minecraft does nothing... 

So what's my next course to figure this out what's causing the problem...

---

### Post by dannyboy79 on 2014-11-13
are you sure you're using the latest minecraft.jar file? you can try the following command BUT i'm seeing other's complain about unacceptable frames per second
```
java -Djava.compiler=NONE -jar MinecraftLauncher.jar
```
if that works but has unplayable fps, then let's see if you can get terminal output, please launch minecraft from the terminal instead of right clicking on the .jar file. so that would be
```
java -jar /path/to/launcher/minecraft.jar
```
or launch it using openjdk

is your system 32bit or 64bit?

have you read this thread? [http://ubuntuforums.org/showthread.php?t=2196100&page=2](http://ubuntuforums.org/showthread.php?t=2196100&page=2)

---


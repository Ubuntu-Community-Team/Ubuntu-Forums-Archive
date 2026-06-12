---
title: "Minecraft Out of Memory?"
date: 2014-03-28
forum: Gaming &amp; Leisure
---

### Post by fluctuatinganomaly on 2014-03-28
Hey I know this is a minecraft error. But I was thinking that maybe because I'm running Ubuntu some one might be able to help me sort my issue?

What it is, I was playing MC yesterday and everything was fine for a while. But then I started crashing with a out of memory error. I won't post a crash report because its far to big (but I can do if its needed)

Any ways, I figured I'd try allocating more memory? should work right?? wrong!

When I'm on 1G I can play on the server I'm on (mine and my friends) fine for a while before a crash. With 2G(2048M) allocated, as soon as I login to the server I get the memory crash, as in, I dont get loaded into the world, I connect and disconnect within a couple seconds.

I can't understand how allocating more memory to MC results in MC running out of memory?
If I up it again to 3G(3072M) then as soon as I click play on the launcher, it loads and fails. The game doesn't even begin loading. the launcher sort of jumps, and resets and just goes back to waiting for me to click play and posts something in the development console. I can't make sense of most of it, but there is one bit I get at the bottom, where the important info is
> [11:53:04 INFO]: Client> Error occurred during initialization of VM
[11:53:04 INFO]: Client> Could not reserve enough space for object heap
[11:53:04 INFO]: Client> Could not create the Java virtual machine.
[11:53:04 ERROR]: Game ended with bad state (exit code 1)
[11:53:04 INFO]: Deleting /home/matt/.minecraft/versions/1.6.4-Forge9.11.1.965/1.6.4-Forge9.11.1.965-natives-5103639211716
[11:53:04 INFO]: Ignoring visibility rule and showing launcher due to a game crash


Same if I up to 4G.

I have 2 4G sticks of RAM in my computer, and I should at least have 10G swapspace (im sure of it) I cannot figure this out

I've been using OpenJDK6. using openJDK7 I can't even open my minecraft.jar it just doesn't do anything. I've downloaded ["jre-7u45-linux-i586.rpm]("http://javadl.sun.com/webapps/download/AutoDL?BundleId=81809")" used alien to turn it into a .deb then dpkg-ed it. and it has had no effect.
I've tried running the game with the default textures and this doesn't change anything.

I am honestly baffled by this, if any one could help / shed some light, I would greatly appreciate it.

~Matt

---

### Post by holycow131415 on 2014-03-28
I would remove and purge your open-jdk installs, and replace it with Sun java, as that is what minecraft officially supports. There are many threads on this board on how to install Sun java (since its not in the repos). Also, you are using a mod that uses forge, which is not vanilla. Mods normally require more memory, and could make minecraft itself unstable. Lastly, I would memtest your machine's memory to see if there are bad sectors.

---

### Post by Bucky Ball on 2014-03-28
*Thread moved to **Gaming & Leisure**.*

---

### Post by fluctuatinganomaly on 2014-03-28
> **Bucky Ball said:**
> *Thread moved to **Gaming & Leisure**.*

heh... sorry about that :(

and yeah okay, I saw the thing about sun java, but I noticed alot of people were using open JDK fine as well. I'm still new, so how can I:

Mem test my machine?
Purge jdk installs
and while were at it
Check if my LWJGL are up-to-date?

thanks for the help :)

~Matt

---

### Post by oldrocker99 on 2014-03-28
> **fluctuatinganomaly said:**
> heh... sorry about that :(

and yeah okay, I saw the thing about sun java, but I noticed alot of people were using open JDK fine as well. I'm still new, so how can I:

Mem test my machine?
Purge jdk installs
and while were at it
Check if my LWJGL are up-to-date?

thanks for the help :)

~Matt

To memtest your machine, reboot, and, at the GRUB menu, arrow down to the memory test.

To purge openjdk:

```
sudo apt-get purge openjdk*
```

The latest LWJGL is 2.9.1, and can be downloaded from [http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.9.1/lwjgl-2.9.1.zip/download](http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.9.1/lwjgl-2.9.1.zip/download)

I hope this helps.

---

### Post by efflandt on 2014-03-28
Which Ubuntu version are you running, and is it and whatever java version all 64-bit? Normally 32-bit cannot address more than about 3 GB total including the OS. There are special 32-bit pae kernels that can somehow address more than 3 GB, but I do not know how they work or why anyone would use them when 64-bit can do better natively.

How many effective cores does your CPU have and what graphics (Intel graphics can be slow)? Do your server logs ever say "[WARNING] Can't keep up! Did the system time change, or is the server overloaded?"?

I have never had any trouble simultaneously running separate minecraft server and client (or same with Tekkit mods) on the PC in my sig with 64-bit Ubuntu 12.04 using openjdk-7-jre package and no swap at all even configured. Likewise in 64-bit 13.10 on my laptop, other than the client alone being too slow to play when using Intel graphics instead of much faster Nvidia graphics.

---

### Post by fluctuatinganomaly on 2014-03-29
> **oldrocker99 said:**
> To memtest your machine, reboot, and, at the GRUB menu, arrow down to the memory test.

To purge openjdk:

```
sudo apt-get purge openjdk*
```

The latest LWJGL is 2.9.1, and can be downloaded from [http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.9.1/lwjgl-2.9.1.zip/download](http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.9.1/lwjgl-2.9.1.zip/download)

I hope this helps.

This will help, back at work now though, so I haven't had chance to do this, will post again when I have done, and let you know results !

> **efflandt said:**
> Which Ubuntu version are you running, and is it and whatever java version all 64-bit? Normally 32-bit cannot address more than about 3 GB total including the OS. There are special 32-bit pae kernels that can somehow address more than 3 GB, but I do not know how they work or why anyone would use them when 64-bit can do better natively.

How many effective cores does your CPU have and what graphics (Intel graphics can be slow)? Do your server logs ever say "[WARNING] Can't keep up! Did the system time change, or is the server overloaded?"?

I have never had any trouble simultaneously running separate minecraft server and client (or same with Tekkit mods) on the PC in my sig with 64-bit Ubuntu 12.04 using openjdk-7-jre package and no swap at all even configured. Likewise in 64-bit 13.10 on my laptop, other than the client alone being too slow to play when using Intel graphics instead of much faster Nvidia graphics.

The system info on my operating system says its 32 bit. Pretty sure my computer is most definately capable of 64 bit mind. I've been running with 32 java (in minecraft video settings it said "64 bit java is recommended for 'Far' render distance, you have 32 bit" so yea. I lower that down to normal.

My cpu is and AMD octo-core processor, at least should be, although I know my motherboard doesn't support 8 cores, so I was / am only running on 4 I believe at the minute
 specs:

```
lshw -C cpu 
*-cpu                   
       description: CPU
       product: AMD Phenom(tm) II X6 1075T Processor
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 4
       bus info: cpu@0
       version: 15.10.0
       serial: To Be Filled By O.E.M.
       slot: AM3r2
       size: 3GHz
       capacity: 3GHz
       width: 64 bits
       clock: 200MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr cpb hw_pstate npt lbrv svm_lock nrip_save pausefilter
       configuration: cores=6 enabledcores=6 threads=6
```

I have an AMD/ATI Radeon XFX HD 6850 graphics card. Drivers I'm not sure about, I have another thread up about my driver issues. At current I am running on source drivers I believe. The proprietary drivers mess up my monitor resolution for some reason :/

And finally, no, there are no statements in the log / server console about the system not being able to keep up.

~Matt

---

### Post by fluctuatinganomaly on 2014-03-31
Okay, reposting back

I ran my memory test, not sure if you wanted anything posting from that? it wasn't exactly copy/paste-able though I can always run it again if you need to see some information from it. Any ways, it ran the tests and said there were no errors.

purged openjdk and isntalled java 8 using the webupd8 repo that someone suggested in another thread. java -version now outputs

```
java version "1.8.0"
Java(TM) SE Runtime Environment (build 1.8.0-b132)
Java HotSpot(TM) Server VM (build 25.0-b70, mixed mode)

```

Also, I downloaded the lwjgl from the link that was posted, I was going to use [http://askubuntu.com/questions/177996/how-do-i-patch-minecrafts-lwjgl-libraries](http://askubuntu.com/questions/177996/how-do-i-patch-minecrafts-lwjgl-libraries) to patch my files, but I don't appear to have a .miecraft/bin folder. I figured this must have been written up before the minecraft folder system was restructured (when resoucres packs were introduced rather than just texture packs) any ways, I browsed the folders myself to:
Home/.minecraft/libraries/org/lwjgl/lwjgl/lwjgl/  -- Here I had /2.9.0/ and /2.9.1/ folders, respectively. The files I downloaded were 2.9.1 so I figure I'm up-to-date?? (But I dunno if I've done this wrong, if some can inform me of whether I am up to date or can explain a better way to check / patch lwjgl, I'd appreciate the help)

SO! I figure everything should be all okay right?? :D

First run attempted with JVM arguments -Xmx3G
Resulted in a crash:
```
[13:23:28 INFO]: JFX is already initialized
[13:23:29 INFO]: Refreshing local version list...
[13:23:29 INFO]: Minecraft Launcher 1.3.11 (through bootstrap 5) started on linux...
[13:23:29 INFO]: Current time is Mar 31, 2014 1:23:29 PM
[13:23:29 INFO]: System.getProperty('os.name') == 'Linux'
[13:23:29 INFO]: System.getProperty('os.version') == '3.8.0-37-generic'
[13:23:29 INFO]: System.getProperty('os.arch') == 'i386'
[13:23:29 INFO]: System.getProperty('java.version') == '1.8.0'
[13:23:29 INFO]: System.getProperty('java.vendor') == 'Oracle Corporation'
[13:23:29 INFO]: System.getProperty('sun.arch.data.model') == '32'
[13:23:29 INFO]: Refreshing remote version list...
[13:23:30 INFO]: Refresh complete.
[13:23:30 INFO]: Loaded 3 profile(s); selected 'PeachNips-Forge'
[13:23:30 INFO]: Refreshing auth...
[13:23:30 INFO]: Logging in with access token
[13:23:43 INFO]: Getting syncinfo for selected version
[13:23:43 INFO]: Queueing library & version downloads
[13:23:43 INFO]: Download job 'Version & Libraries' started (16 threads, 22 files)
[13:23:43 INFO]: Attempting to download /home/matt/.minecraft/libraries/com/paulscode/codecjorbis/20101023/codecjorbis-20101023.jar for job 'Version & Libraries'... (try 0)
[13:23:43 INFO]: Attempting to download /home/matt/.minecraft/libraries/org/lwjgl/lwjgl/lwjgl_util/2.9.0/lwjgl_util-2.9.0.jar for job 'Version & Libraries'... (try 0)
[13:23:43 INFO]: Attempting to download /home/matt/.minecraft/libraries/net/minecraft/launchwrapper/1.8/launchwrapper-1.8.jar for job 'Version & Libraries'... (try 0)
[13:23:43 INFO]: Attempting to download /home/matt/.minecraft/libraries/com/google/guava/guava/14.0/guava-14.0.jar for job 'Version & Libraries'... (try 0)
[13:23:43 INFO]: Attempting to download /home/matt/.minecraft/libraries/com/paulscode/soundsystem/20120107/soundsystem-20120107.jar for job 'Version & Libraries'... (try 0)
[13:23:43 INFO]: Attempting to download /home/matt/.minecraft/libraries/com/paulscode/libraryjavasound/20101123/libraryjavasound-20101123.jar for job 'Version & Libraries'... (try 0)
[13:23:43 INFO]: Attempting to download /home/matt/.minecraft/libraries/net/java/jinput/jinput/2.0.5/jinput-2.0.5.jar for job 'Version & Libraries'... (try 0)
[13:23:43 INFO]: Attempting to download /home/matt/.minecraft/libraries/org/bouncycastle/bcprov-jdk15on/1.47/bcprov-jdk15on-1.47.jar for job 'Version & Libraries'... (try 0)
[13:23:43 INFO]: Attempting to download /home/matt/.minecraft/libraries/org/apache/commons/commons-lang3/3.1/commons-lang3-3.1.jar for job 'Version & Libraries'... (try 0)
[13:23:43 INFO]: Attempting to download /home/matt/.minecraft/libraries/org/lwjgl/lwjgl/lwjgl-platform/2.9.0/lwjgl-platform-2.9.0-natives-linux.jar for job 'Version & Libraries'... (try 0)
[13:23:43 INFO]: Attempting to download /home/matt/.minecraft/libraries/org/ow2/asm/asm-all/4.1/asm-all-4.1.jar for job 'Version & Libraries'... (try 0)
[13:23:43 INFO]: Attempting to download /home/matt/.minecraft/libraries/com/paulscode/codecwav/20101023/codecwav-20101023.jar for job 'Version & Libraries'... (try 0)
[13:23:43 INFO]: Attempting to download /home/matt/.minecraft/libraries/org/lwjgl/lwjgl/lwjgl/2.9.0/lwjgl-2.9.0.jar for job 'Version & Libraries'... (try 0)
[13:23:43 INFO]: Attempting to download /home/matt/.minecraft/libraries/com/paulscode/librarylwjglopenal/20100824/librarylwjglopenal-20100824.jar for job 'Version & Libraries'... (try 0)
[13:23:43 INFO]: Attempting to download /home/matt/.minecraft/libraries/commons-io/commons-io/2.4/commons-io-2.4.jar for job 'Version & Libraries'... (try 0)
[13:23:43 INFO]: Attempting to download /home/matt/.minecraft/libraries/net/java/jinput/jinput-platform/2.0.5/jinput-platform-2.0.5-natives-linux.jar for job 'Version & Libraries'... (try 0)
[13:23:44 INFO]: Download job 'Resources' skipped as there are no files to download
[13:23:44 INFO]: Job 'Resources' finished successfully (took 0:00:00.000)
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/com/google/guava/guava/14.0/guava-14.0.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/org/bouncycastle/bcprov-jdk15on/1.47/bcprov-jdk15on-1.47.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/org/lwjgl/lwjgl/lwjgl-platform/2.9.0/lwjgl-platform-2.9.0-natives-linux.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Attempting to download /home/matt/.minecraft/libraries/lzma/lzma/0.0.1/lzma-0.0.1.jar for job 'Version & Libraries'... (try 0)
[13:23:44 INFO]: Attempting to download /home/matt/.minecraft/libraries/com/google/code/gson/gson/2.2.2/gson-2.2.2.jar for job 'Version & Libraries'... (try 0)
[13:23:44 INFO]: Attempting to download /home/matt/.minecraft/libraries/argo/argo/2.25_fixed/argo-2.25_fixed.jar for job 'Version & Libraries'... (try 0)
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/lzma/lzma/0.0.1/lzma-0.0.1.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Attempting to download /home/matt/.minecraft/libraries/net/sf/jopt-simple/jopt-simple/4.5/jopt-simple-4.5.jar for job 'Version & Libraries'... (try 0)
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/argo/argo/2.25_fixed/argo-2.25_fixed.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Attempting to download /home/matt/.minecraft/libraries/net/java/jutils/jutils/1.0.0/jutils-1.0.0.jar for job 'Version & Libraries'... (try 0)
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/net/sf/jopt-simple/jopt-simple/4.5/jopt-simple-4.5.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Attempting to download /home/matt/.minecraft/versions/1.6.4-Forge9.11.1.965/1.6.4-Forge9.11.1.965.jar for job 'Version & Libraries'... (try 0)
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/net/java/jutils/jutils/1.0.0/jutils-1.0.0.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/org/apache/commons/commons-lang3/3.1/commons-lang3-3.1.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/net/java/jinput/jinput-platform/2.0.5/jinput-platform-2.0.5-natives-linux.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/org/lwjgl/lwjgl/lwjgl/2.9.0/lwjgl-2.9.0.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/commons-io/commons-io/2.4/commons-io-2.4.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/com/paulscode/librarylwjglopenal/20100824/librarylwjglopenal-20100824.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/org/ow2/asm/asm-all/4.1/asm-all-4.1.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/net/java/jinput/jinput/2.0.5/jinput-2.0.5.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/com/paulscode/codecwav/20101023/codecwav-20101023.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/com/paulscode/libraryjavasound/20101123/libraryjavasound-20101123.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/org/lwjgl/lwjgl/lwjgl_util/2.9.0/lwjgl_util-2.9.0.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/com/paulscode/codecjorbis/20101023/codecjorbis-20101023.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/net/minecraft/launchwrapper/1.8/launchwrapper-1.8.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/com/paulscode/soundsystem/20120107/soundsystem-20120107.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/libraries/com/google/code/gson/gson/2.2.2/gson-2.2.2.jar for job 'Version & Libraries': Local file matches local checksum, using that
[13:23:44 INFO]: Finished downloading /home/matt/.minecraft/versions/1.6.4-Forge9.11.1.965/1.6.4-Forge9.11.1.965.jar for job 'Version & Libraries': Couldn't connect to server (responded with 403) but have local file, assuming it's good
[13:23:44 INFO]: Job 'Version & Libraries' finished successfully (took 0:00:01.216)
[13:23:44 INFO]: Launching game
[13:23:44 INFO]: Looking for old natives & assets to clean up...
[13:23:44 INFO]: Unpacking natives to /home/matt/.minecraft/versions/1.6.4-Forge9.11.1.965/1.6.4-Forge9.11.1.965-natives-4921469122449
[13:23:44 INFO]: Reconstructing virtual assets folder at /home/matt/.minecraft/assets/virtual/legacy
[13:23:45 INFO]: Launching in /home/matt/.minecraft
[13:23:45 INFO]: Half command: /usr/lib/jvm/java-8-oracle/jre/bin/java -Xmx3G -Djava.library.path=/home/matt/.minecraft/versions/1.6.4-Forge9.11.1.965/1.6.4-Forge9.11.1.965-natives-4921469122449 -cp /home/matt/.minecraft/libraries/net/minecraftforge/minecraftforge/9.11.1.965/minecraftforge-9.11.1.965.jar:/home/matt/.minecraft/libraries/net/minecraft/launchwrapper/1.8/launchwrapper-1.8.jar:/home/matt/.minecraft/libraries/org/ow2/asm/asm-all/4.1/asm-all-4.1.jar:/home/matt/.minecraft/libraries/org/scala-lang/scala-library/2.10.2/scala-library-2.10.2.jar:/home/matt/.minecraft/libraries/org/scala-lang/scala-compiler/2.10.2/scala-compiler-2.10.2.jar:/home/matt/.minecraft/libraries/lzma/lzma/0.0.1/lzma-0.0.1.jar:/home/matt/.minecraft/libraries/net/sf/jopt-simple/jopt-simple/4.5/jopt-simple-4.5.jar:/home/matt/.minecraft/libraries/com/paulscode/codecjorbis/20101023/codecjorbis-20101023.jar:/home/matt/.minecraft/libraries/com/paulscode/codecwav/20101023/codecwav-20101023.jar:/home/matt/.minecraft/libraries/com/paulscode/libraryjavasound/20101123/libraryjavasound-20101123.jar:/home/matt/.minecraft/libraries/com/paulscode/librarylwjglopenal/20100824/librarylwjglopenal-20100824.jar:/home/matt/.minecraft/libraries/com/paulscode/soundsystem/20120107/soundsystem-20120107.jar:/home/matt/.minecraft/libraries/argo/argo/2.25_fixed/argo-2.25_fixed.jar:/home/matt/.minecraft/libraries/org/bouncycastle/bcprov-jdk15on/1.47/bcprov-jdk15on-1.47.jar:/home/matt/.minecraft/libraries/com/google/guava/guava/14.0/guava-14.0.jar:/home/matt/.minecraft/libraries/org/apache/commons/commons-lang3/3.1/commons-lang3-3.1.jar:/home/matt/.minecraft/libraries/commons-io/commons-io/2.4/commons-io-2.4.jar:/home/matt/.minecraft/libraries/net/java/jinput/jinput/2.0.5/jinput-2.0.5.jar:/home/matt/.minecraft/libraries/net/java/jutils/jutils/1.0.0/jutils-1.0.0.jar:/home/matt/.minecraft/libraries/com/google/code/gson/gson/2.2.2/gson-2.2.2.jar:/home/matt/.minecraft/libraries/org/lwjgl/lwjgl/lwjgl/2.9.0/lwjgl-2.9.0.jar:/home/matt/.minecraft/libraries/org/lwjgl/lwjgl/lwjgl_util/2.9.0/lwjgl_util-2.9.0.jar:/home/matt/.minecraft/versions/1.6.4-Forge9.11.1.965/1.6.4-Forge9.11.1.965.jar net.minecraft.launchwrapper.Launch
[13:23:45 ERROR]: Game ended with bad state (exit code 1)
[13:23:45 ERROR]: Game ended with bad state (exit code 1)
[13:23:45 INFO]: Deleting /home/matt/.minecraft/versions/1.6.4-Forge9.11.1.965/1.6.4-Forge9.11.1.965-natives-4921469122449
[13:23:45 INFO]: Ignoring visibility rule and showing launcher due to a game crash
[13:23:45 INFO]: Ignoring visibility rule and showing launcher due to a game crash
```


2nd run with JVM arguments set -Xmx2G
Game runs and I even log into server!

First run seems to be the same problem as previously stated where the launcher "jumps" from the log file, it obviously errs somewhere, I don't understand where or why, and then closes the game due to the crash. I have read some where that this could also be due to the game being assigned too much memory??
But 2nd scenario is an improvement on the previous issue. I've just attempted this, so I shall play around for a bit and see if I encounter another "out of memory" crash.

In the mean time, if some one could help me figure out, or has any more info, on why the game crashes on launch when JVM argument is set to Xmx3G (assigning 3G of memory to the game) I would be mighty grateful. 

Thanks for all the help so far though, you guys have been great!

~Matt

-----EDIT

Could some one tell me how you add a scroll-able box for the quotes etc? The log file I posted takes up alot of space, and I don't know how to put it in a scroll container :/ sorry.

---

### Post by fluctuatinganomaly on 2014-03-31
Extra information:

Running on -Xmx2G the game had an epic crash where it all froze, I had to log out then back in again to do anything as my cursor was locked in the game.

A minute or two after logging in I got a nice little box pop up that said:
> Sorry, Ubuntu 12.04 has experienced an internal error.
If you notice further problems, try restarting the computer.


I missed copying the info, but it was related to java (I remember seeing the word "java" in the executable path bit. and it mentioned that it was using local or third party libraries and was related to forge and also had some mention of lwjgl :/

Trying on -Xmx1G.... after the last few runs though, I am expecting an out of memory error :/

~Matt

---

### Post by Bucky Ball on 2014-04-01
Please use [code] tags. Neater, easier to read. ;)

I have taken the liberty of adding them in post #8.

---

### Post by fluctuatinganomaly on 2014-04-01
Thanks :) I thought I had done, my bad. Keep in mind for the future though!

Also, I'll add a bump, hoping for any new information :/ Didn't get chance to play on Xmx1G yesterday as I got called in to work early (stupid work) 

So thats part of todays jobs!

~Matt

---


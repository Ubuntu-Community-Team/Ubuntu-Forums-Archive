---
title: "Minecraft Crashes."
date: 2015-06-13
forum: Gaming &amp; Leisure
---

### Post by dasfreakinmann on 2015-06-13
I open the mincraft.jar using Java I am able to sign in and launch the game but soon after it crashes and i get ```
Java HotSpot(TM) Server VM warning: Using incremental CMS is deprecated and will likely be removed in a future release
[23:58:23] [Client thread/INFO]: Setting user: PrivateEagan
[23:58:23] [Client thread/INFO]: (Session ID is token:0343a20a95144b5590aa7efe29c7b0ef:c95f6aa35c56434f856ec69ef29512c1)
[23:58:27] [Client thread/INFO]: LWJGL Version: 2.9.4
[23:58:27] [Client thread/INFO]: Reloading ResourceManager: Default
If on Windows, make sure to provide all of the necessary dll's as specified in the twitchsdk README. Also, make sure to set the PATH environment variable to point to the directory containing the dll's.
[23:58:28] [Client thread/ERROR]: Couldn't initialize twitch stream
[23:58:28] [Sound Library Loader/INFO]: Starting up SoundSystem...
[23:58:28] [Thread-6/INFO]: Initializing LWJGL OpenAL
[23:58:28] [Thread-6/INFO]: (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
[23:58:28] [Thread-6/INFO]: OpenAL initialized.
[23:58:28] [Sound Library Loader/INFO]: Sound engine started
[23:58:31] [Client thread/INFO]: Created: 512x512 textures-atlas
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x82550764, pid=2180, tid=3060722496
#
# JRE version: Java(TM) SE Runtime Environment (8.0_45-b14) (build 1.8.0_45-b14)
# Java VM: Java HotSpot(TM) Server VM (25.45-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [nouveau_dri.so+0x390764]
#
# Failed to write core dump. Core dumps have been disabled. To enable core dumping, try "ulimit -c unlimited" before starting Java again
#
# An error report file with more information is saved as:
# /home/asdf/.minecraft/hs_err_pid2180.log
#
# If you would like to submit a bug report, please visit:
#   http://bugreport.java.com/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

```

---

### Post by Bucky Ball on 2015-06-13
*Thread moved to **Gaming & Leisure**.*

---

### Post by efflandt on 2015-06-13
Which Ubuntu version and graphics card/chip do you have? You appear to have a problem with nouveau which is the default driver for Nvidia cards if you do not install nvidia drivers. Unless you have an older nvidia card, you may want to install nvidia drivers which would likely be faster. Although, my GTX 750 Ti with the new Maxwell chip was so new that nouveau or nvidia-current package did not even support it when I installed 14.04. In my case nvidia-331-updates package worked, but I am currently using a newer driver from a ppa.

I have never used Oracle (or Sun) Java for minecraft in Linux, so not sure if there are any issues with Java 8. Initially I used openjdk-6-jre package and currently using openjdk-7-jre from regular Ubuntu packages.

---

### Post by GrouchyGaijin on 2015-06-13
> **efflandt said:**
> 
I have never used Oracle (or Sun) Java for minecraft in Linux, so not sure if there are any issues with Java 8. Initially I used openjdk-6-jre package and currently using openjdk-7-jre from regular Ubuntu packages.

Yeah I am using the openjdk-6-jre package from the repository and have not had any trouble with minecraft.

---

### Post by dasfreakinmann on 2015-06-13
> **GrouchyGaijin said:**
> Yeah I am using the openjdk-6-jre package from the repository and have not had any trouble with minecraft.

I've tried using Both Oracle 8 and jre 6

---

### Post by GrouchyGaijin on 2015-06-14
Then as efflandt mentioned, I would try using the actual Nvidia driver.

---


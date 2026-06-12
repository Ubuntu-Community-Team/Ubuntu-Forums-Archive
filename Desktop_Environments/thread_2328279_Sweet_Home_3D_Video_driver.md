---
title: "Sweet Home 3D Video driver"
date: 2016-06-19
forum: Desktop Environments
---

### Post by mune on 2016-06-19
Hi all

I used sweethome3d with the old distro ver: ubuntu 14.10 and with the one before.

Today I launched it (I'm using a fresh installation of ubuntu 16.4) and it closes immediately. After a bit of researches I got that the error isn't in the app but in the link between java and the linux 3D/video layer.

```

mune@lello:~$ sweethome3d
Java 3D: implicit antialiasing enabled
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f903a57bb6d, pid=6440, tid=140257443735296
#
# JRE version: OpenJDK Runtime Environment (8.0_91-b14) (build 1.8.0_91-8u91-b14-0ubuntu4~16.04.1-b14)
# Java VM: OpenJDK 64-Bit Server VM (25.91-b14 mixed mode linux-amd64 compressed oops)
# Problematic frame:
# C  [r600_dri.so+0x1f4b6d]

[...]

```

I guess it is something related to the video drivers (confirmed by my googlings but all for old versions).

What can I do?

Thanks

(Sorry  for the thread title but I pressed "enter" in place of "Backspace" so the post has been published incomplete and with a wrong title)

---

### Post by CantankRus on 2016-06-19
You could give Oracle Java 8 a go.
[**_[COLOR="#B22222"]INSTALL ORACLE JAVA 8[/COLOR]_**]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html")
The PPA supports 16.04.

---

### Post by mune on 2016-06-19
> **CantankRus said:**
> You could give Oracle Java 8 a go.
[**_[COLOR="#B22222"]INSTALL ORACLE JAVA 8[/COLOR]_**]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html")
The PPA supports 16.04.

Yes, I have already done the installation but it seems that SH uses anyway openJRE.

How can I force it to use the Oracke java?

---

### Post by CantankRus on 2016-06-20
I installed sweethome3d and it starts here.
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] java -version**
openjdk version "1.8.0_91"
OpenJDK Runtime Environment (build 1.8.0_91-8u91-b14-0ubuntu4~16.04.1-b14)
OpenJDK 64-Bit Server VM (build 25.91-b14, mixed mode)
```

Using nvidia drivers as in my sig below.

---

### Post by CantankRus on 2016-06-20
You could also try a newer version from getdeb.
Download the getdeb package from this page. This package adds the getdeb repository to your sources.

After installing getdeb, update your sources...
```
sudo apt update
```

Then upgrade sweethome3d to version 5.2...
```
sudo apt install sweethome3d
```

I would then disable the getdeb repo in your sources.

---

### Post by mune on 2016-06-21
> **CantankRus said:**
> I installed sweethome3d and it starts here.
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] java -version**
openjdk version "1.8.0_91"
OpenJDK Runtime Environment (build 1.8.0_91-8u91-b14-0ubuntu4~16.04.1-b14)
OpenJDK 64-Bit Server VM (build 25.91-b14, mixed mode)
```

Using nvidia drivers as in my sig below.

```

mune@lello:~$ java -version
java version "1.8.0_91"
Java(TM) SE Runtime Environment (build 1.8.0_91-b14)
Java HotSpot(TM) 64-Bit Server VM (build 25.91-b14, mixed mode)

```

This is weird: SH when crashes is complaining about openJDK even if the Oracle's java is installed.

---

### Post by mune on 2016-06-21
> **CantankRus said:**
> Then upgrade sweethome3d to version 5.2...
```
sudo apt install sweethome3d
```

```
sweethome3d is already the newest version (5.2-1~getdeb1).
```
:/

> I would then disable the getdeb repo in your sources.
I don't understand: what does it mean?

---

### Post by mune on 2016-06-21
> **mune said:**
> 
This is weird: SH when crashes is complaining about openJDK even if the Oracle's java is installed.

This is the key!

```

mune@lello:~$ which sweethome3d
/usr/bin/sweethome3d
mune@lello:~$ file /usr/bin/sweethome3d
/usr/bin/sweethome3d: symbolic link to ../share/sweethome3d/sweethome3d.sh
mune@lello:~$ less /usr/share/sweethome3d/sweethome3d.sh
-----------------------------------
#!/bin/sh
#
#
BASEPATH=/usr/share/sweethome3d
JAVA_ARGS="-Djava.library.path=/usr/lib/jni \
 -Dcom.eteks.sweethome3d.applicationFolders=$HOME/.eteks/sweethome3d:/usr/share/sweethome3d"

. /usr/lib/java-wrappers/java-wrappers.sh

find_java_runtime java6

find_jars j3dcore j3dutils vecmath batik
find_jars sunflow itext janino freehep-util freehep-io freehep-xml
find_jars freehep-graphics2d freehep-graphicsio freehep-graphicsio-svg
find_jars /usr/share/sweethome3d/sweethome3d.jar
find_jars /usr/share/icedtea-web/netx.jar

cd $BASEPATH
run_java com.eteks.sweethome3d.SweetHome3D -open "$@"

```

It has its own JRE, ignoring the system wide one.

Hot to change the SH script to force it to use the Oracle java ?

---

### Post by CantankRus on 2016-06-22
I don't think java is your problem.
I can run sweethome3d regardless of default java.
It will run using openjdk or oracle java.

Set default java with... 
```
sudo update-alternatives --config java
```

I can even remove openjdk-jre so as it has no option but to use oracle java, and vice versa.
When only  oracle java is installed SH3d gives a warning but still starts with the message "falling back to JAVA_CMD = java"
[ATTACH=CONFIG]269706[/ATTACH]


Going back to your first post I think the error is to do with your GPU/drivers.

To show your graphics details you can install **inxi** (system info script)....
```
sudo apt install inxi
```
eg...
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] inxi -G**
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti]
           Display Server: X.Org 1.18.3 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1680x1050@59.88hz
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 361.42
```

My guess is you have an amd/ati GPU and are now using the open source radeon driver.
[**_[COLOR="#B22222"]Why Radeon Users May Want to Avoid Ubuntu 16.04 LTS[/COLOR]_**]("http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04")

---

### Post by mune on 2016-06-22
> **CantankRus said:**
> Set default java with... 
I did but SH fails with both OpenJDK and the Oracle java.

The video settings are:
```
mune@lello:~$ inxi -G
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Caicos XT [Radeon HD 7470/8470 / R5 235/310 OEM]
           Display Server: X.Org 1.18.3 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.90hz
           GLX Renderer: Gallium 0.4 on AMD CAICOS (DRM 2.43.0, LLVM 3.8.0)
           GLX Version: 3.0 Mesa 11.2.0

```

> My guess is you have an amd/ati GPU and are now using the open source radeon driver.
[**_[COLOR="#B22222"]Why Radeon Users May Want to Avoid Ubuntu 16.04 LTS[/COLOR]_**]("http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04")

_And you were right!_
I went to the AMD site to download the new driver, but none is available. I don't understand if there is a solution or I have to eait for the AMD's catalyst driver new release.

---

### Post by CantankRus on 2016-06-22
Did you read the link in my previous post?
I believe you would have to wait, go back to 14.04 or if you're on a Desktop PC get an nvidia card.

---

### Post by mune on 2016-06-28
I found in many pages other users complaining that in Ubuntu 16.04 is missing the free driver fglrx and that AMD is not going to develop a closed source version nor Canonical is not going to the care to develop a free one.

I was almost hopeless when I read an [ article (of a couple of months ago)]("http://www.phoronix.com/scan.php?page=article&item=amd-gpu-pro&num=1") glorifying AMD for its new linux driver. I followed the link and I landed on this [page of the AMD'site]("http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx"), where I misunderstood 14.04 with 16,04.

I installed the driver it worked but now SH3D not only doesn't work but when it is launched it closes the Xsession  and then the system asks for user login for a new session.

---


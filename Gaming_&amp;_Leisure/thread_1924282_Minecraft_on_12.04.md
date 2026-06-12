---
title: "Minecraft on 12.04"
date: 2012-02-12
forum: Gaming &amp; Leisure
---

### Post by HavoK360 on 2012-02-12
Hey guys! Yet another bump for the day, so here it goes.
I decided to upgrade to 12.04 Beta, so I could look for some bugs myself, and so far, there aren't any! Except one. I have both OpenJDK6 and 7 from the Software center, but only Java 7 comes up as an application. When I use it, it WILL log me into minecraft, but after the "Updating Minecraft" screen, it goes black and doesnt do anything. I know that this isnt a video card error (I Use a Nivida GeForce GFX Card), and all the advanced drivers are up and running. Any suggestions? And please don't suggest the Bash script, all that does is force it to use Java automatically, not run the initial program. Thanks!
-BW

(If theres any questions on my computer, its an AMD Athlon64 X2 AM2+ running 2 GiB of ram, for the puny wattage on the computer.)

---

### Post by memzak on 2012-02-12
Error codes? Could you post what you get, if anything at all?

---

### Post by regor210 on 2012-02-12
I know that Oracle Java 7 works with Minecraft but you have to manually update LWJGL
 
[http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL)

If you don't you get a black screen.

Note. Looks like Mincraft is still using sun Java 6 by default.

---

### Post by memzak on 2012-02-12
It could be a completely different error causing the problem... but it's always good to update, go for the 2.8.1 (stable) version. 2.8.3 version has an error in it (If I remember correctly) where you can't click things properly.

You can update it [here]("http://lwjgl.org/index.php"). (make sure you replace all the files to do with lwjgl in the bin folder)

---

### Post by clj3 on 2012-04-27
ok i got the same problem and this is the error report(i found the lwjgl files and updated the correct ones) :
[IMG]http://postimage.org/image/g49wz8caf/[/IMG]

---

### Post by clj3 on 2012-04-27
sorry the link is:
[http://postimage.org/image/g49wz8caf/]("http://postimage.org/image/g49wz8caf/")

---

### Post by regor210 on 2012-04-27
You may be missing an OpenJDK plugin. Heres the wad I install.

$ sudo apt-get update
$ sudo apt-get install  ca-certificates-java icedtea-7-jre-cacao icedtea-7-jre-jamvm java-common  libatk-wrapper-java libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common libgnome2-0 libgnomevfs2-0 libgnomevfs2-common openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib ttf-dejavu-extra tzdata-java

---

### Post by clj3 on 2012-04-28
no, the minecraft window says the same thing:confused:

---

### Post by regor210 on 2012-04-28
[failed to get system properties (java.lang.NullPointerException)]

bad video card drivers? Failed to find accelerated OpenGL mode?

[http://www.gamefaqs.com/pc/606524-minecraft/answers?qid=259416](http://www.gamefaqs.com/pc/606524-minecraft/answers?qid=259416)


lets look at your 3D drivers.

Try these

# update
$ sudo apt-get update
$ sudo apt-get upgrade

$ sudo apt-get install mesa-utils

# video driver 3D test FPS
$ glxgears

#video card and driver information
$ lspci -vmk | grep -A 8 -B 2 VGA

And post what you get.

---

### Post by ThePinion on 2012-05-11
Once you've ran it once, follow the instructions on this page: [http://modifyubuntu.com/12.04/#minecraft](http://modifyubuntu.com/12.04/#minecraft)

---

### Post by scatcat1 on 2012-06-18
> **ThePinion said:**
> Once you've ran it once, follow the instructions on this page: [http://modifyubuntu.com/12.04/#minecraft](http://modifyubuntu.com/12.04/#minecraft) After trying everything else... this worked like a charm THANK YOU

---

### Post by nicanders on 2012-06-23
I a not sure how to put a new post out here, so I am just replying.  I am trying to help my son get back into minecraft.  When he click on it now he get the following message.
Cannot launch "minecraft"
No Compatible version of java 1.5+ is available.
Then it has two button below.
Open Java Preferences (which does not do anything) and Quit.
I do not know anything about Minecraft but I am trying to help him.  Thanks.

---

### Post by theopfor on 2012-06-23
> **nicanders said:**
> I a not sure how to put a new post out here, so I am just replying.  I am trying to help my son get back into minecraft.  When he click on it now he get the following message.
Cannot launch "minecraft"
No Compatible version of java 1.5+ is available.
Then it has two button below.
Open Java Preferences (which does not do anything) and Quit.
I do not know anything about Minecraft but I am trying to help him.  Thanks.
Delete your .minecraft, login into [minecraft]("http://minecraft.net"), press the play button on the homepage, then follow [this tutorial]("http://ubuntuforums.org/showthread.php?t=1726735").  After that, update your [lwjgl]("http://lwjgl.org/download.php") ([How to]("http://search.yahoo.com/r/_ylt=A0oGdSO6b.ZPAHYAYr5XNyoA;_ylu=X3oDMTE1bG9rb2p0BHNlYwNzcgRwb3MDMQRjb2xvA3NrMQR2dGlkA1NNRTEyMF8yMDY-/SIG=12cj6hhai/EXP=1340530746/**http%3a//www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL")). That method worked for me.

---

### Post by eshm on 2012-11-12
> **scatcat1 said:**
> After trying everything else... this worked like a charm THANK YOU

Just wanted to chime in to +1 that comment.  After a fresh install this worked like a charm for me as well.

---


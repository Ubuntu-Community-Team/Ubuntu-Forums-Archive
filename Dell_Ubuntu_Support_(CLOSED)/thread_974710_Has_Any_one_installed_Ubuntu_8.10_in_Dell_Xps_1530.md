---
title: "Has Any one installed Ubuntu 8.10 in Dell Xps 1530?"
date: 2008-11-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by KrishK on 2008-11-07
Actually I am using Ubuntu 8.04 Hardy and was thinking to upgrade to Intrepid. Has anyone installed it? I  would like to know the problems after installation. PLease someone who has installed 8.10 write me your review as well solutions for problems you encountered.

THanks:confused:

---

### Post by Gausian on 2008-11-07
the only thing that did not work perfectrly was the internal mic.  this is not fixed yet as far i know.

everything else worked out of the box.

---

### Post by DivinityX on 2008-11-08
i tried it out and my mouse would freakout when i touched the trackpad, and only a few of the keys on the keyboard worked...unless i messed something up...

---

### Post by jespdj on 2008-11-08
> **DivinityX said:**
> i tried it out and my mouse would freakout when i touched the trackpad, ...
This is a known problem that also happens with 8.04. You have to use a kernel parameter to fix this:
```
i8042.nomux=1
```
See [this thread](http://ubuntuforums.org/showthread.php?t=737060) for more information, or search for "trackpad 1530" or something similar in the forums here to find more info.

I have not yet installed 8.10 on my M1530, still using 8.04 (64-bit) and I'm not going to be upgrading soon. (I need the internal microphone to work with Skype, so I will not upgrade as long as there's no way to get the microphone to work).

See also this thread: [Internal mic not working after 8.10 upgrade](http://ubuntuforums.org/showthread.php?t=956565)

*edit*: also see this: [XPS M1530 too many problems after updating to 8.10](http://ubuntuforums.org/showthread.php?t=972085)

You could just download and burn an Ubuntu 8.10 Live CD, boot from it and see if it works.

---

### Post by Gausian on 2008-11-08
oh yeah forgot about the touchpad not working out of the box.  its an easy fix though.

---

### Post by entroix1 on 2008-11-08
It seems to me that I am the only one facing a lot of problems in ubuntu 8.10.
[http://ubuntuforums.org/showthread.php?t=972085](http://ubuntuforums.org/showthread.php?t=972085)

There is my original post. My wifi was fixed yesterday though when i updated my kernel. I never had a problem with my touchpad!

---

### Post by Clockswork on 2008-11-09
The only thing that didnt work for my after upgrading was my graphics drivers. Envy wouldnt install and the restricted would just freakout and leave me in safe-mode. 

But after clean installation everything worked perfectly =)

---

### Post by shashikants on 2008-11-10
Yup .. just installed 8.10 yesterday and it worked gr8 ..
yeah applied those fixes and its up and ruining...

---

### Post by CdeSousaG on 2009-01-28
I had some issues with the video, the wireless card and the microphone.  

I made an updated and the wireless and video got fixed. (I'm not using envy for the video drivers but you can use driver given by default and its going to work well. Its v 177)

I still have problems with the microphone and I can't find a solution... Anybody has something ?

---

### Post by jespdj on 2009-01-30
> **CdeSousaG said:**
> I still have problems with the microphone and I can't find a solution... Anybody has something ?

Might be because of [this bug](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/275998).

---

### Post by MooseMagnet on 2009-01-30
Inspiron 1300. I added the HTML to hal, but the touchpad still doesn't work correctly. But... it seems to be something other than the touchpad. It has taken up to 65 seconds for a touchpad tap to register. I did not have this problem with Feisty. You can click until your finger is numb, but you just have to wait until the machine is ready to accept the tap. And the cursor jumps all over the page when typing.

The graphics are scratchy, jumbled, ugly. I got some help from a Launchpad person, but they sent me a terminal command to load a new driver, and that driver had a bug in it. It crashed my whole mess, and I had to rebuild from ISO disk.

Firefox is soooo slow. Many times, the screen turns gray color - sleeps - while it's trying to load a page. And Totem does the same thing. Neither of these happened with Feisty.

I liked Feisty, but don't like Intrepid at all.

---

### Post by melcior on 2009-02-02
Yes and works fine. Goto this page:
[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530)
lot of information available.
My recomendation:
Upgrade the BIOS
and use the sources from dell:
[http://linux.dell.com/repo](http://linux.dell.com/repo)

I'm absolute begginer , but with some investigation and good friends you can do a good and performant instalation. 

Good luck

---


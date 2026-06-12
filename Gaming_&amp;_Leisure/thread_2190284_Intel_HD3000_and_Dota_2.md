---
title: "Intel HD3000 and Dota 2"
date: 2013-11-26
forum: Gaming &amp; Leisure
---

### Post by sideaway on 2013-11-26
Hi guys,

I have an HP Elitebook 8460p, running Ubuntu 13.10 64bit, i5-2410M with intel HD3000 graphics. I do a bit of casual gaming, Dota 2 is my favourite game and I DID have a desktop, but I've moved to a "space-restricted flat" so I've had to make do with just a laptop for all my computing needs. 

Basically the menus are unusable and if I can manage to launch a game I'm only getting like 0 - 2fps in game. Can anyone help?


```
hamish@Strahlhorn:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.3, 256 bits)
OpenGL version string:  2.1 Mesa 9.2.1

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```

```
hamish@Strahlhorn:~$ uname -a
Linux Strahlhorn 3.12.0-031200-generic #201311031935 SMP Mon Nov 4 00:36:54 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

[IMG]http://i.imgur.com/RaHLZP8.png[/IMG]

[IMG]http://i.imgur.com/lJ5Ki82.png[/IMG]

[IMG]http://i.imgur.com/rH3SP5u.png[/IMG]

---

### Post by DanglingPointer on 2013-11-26
Looks like the driver you are using is unable to render.  I know next to nothing about Intel iGPUs.  Perhaps there is an Intel propriety driver you can use for Linux?

---

### Post by Ranko Kohime on 2013-11-27
I ran into this issue myself a while back.  DanglingPointer is correct, hardware rendering isn't working in a case like that.  (Not that I had great performance with my own i3-2310M, but it (Dota 2) was playable, I suppose)

No, there is no proprietary driver; Intel is working with the Open Source community on their driver.

I honestly can't tell you what I did to resolve it, because I never figured out what caused it.  Try xorg-edgers, perhaps?

---

### Post by sideaway on 2013-11-28
Added xorg-edgers PPA, did an apt-get update and upgrade;

```
hamish@Strahlhorn:~$ ug
[sudo] password for hamish: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hamish@Strahlhorn:~$ 

```

Some how I think relaunching and testing the game isn't going to net different results :(

(ug is an alias for upgrade)

---

### Post by oldrocker99 on 2013-11-29
You might try opening Synaptic, clicking the 'Origin' button, and searching for and clicking on the x-org repository, which **might** have upgraded drivers even if upgrade did nothing.

---

### Post by dannyboy79 on 2013-11-29
the thread talks about Ubuntu 13.10 with the Linux 3.11 kernel and Mesa 9.2 being pretty decent with the HD GPU's built into the sandy and ivy intel chips. Are you running mesa 9.2? Here's the article [http://www.phoronix.com/scan.php?page=article&item=intel_sandyivy_ubuntu1310&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_sandyivy_ubuntu1310&num=1)

---

### Post by sideaway on 2013-11-30
> **oldrocker99 said:**
> You might try opening Synaptic, clicking the 'Origin' button, and searching for and clicking on the x-org repository, which **might** have upgraded drivers even if upgrade did nothing.

Trying this now.

> **dannyboy79 said:**
> the thread talks about Ubuntu 13.10 with the Linux 3.11 kernel and Mesa 9.2 being pretty decent with the HD GPU's built into the sandy and ivy intel chips. Are you running mesa 9.2? Here's the article [http://www.phoronix.com/scan.php?page=article&item=intel_sandyivy_ubuntu1310&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_sandyivy_ubuntu1310&num=1)

I'm running 9.2.1, you can see this from my first post :)

---

### Post by sideaway on 2013-11-30
Hi all, turns out I wasn't even using the Intel drivers... All working now they'reinstalled. Thanks oldrocker99.

---

### Post by strattonbrazil on 2013-12-31
> **sideaway said:**
> Hi all, turns out I wasn't even using the Intel drivers... All working now they'reinstalled. Thanks oldrocker99.

How did you verify you weren't using the Intel drivers?  Did you just go to the xorg-edgers PPA and mark "xserver-xorg-video-intel" for complete reinstall?

---

### Post by sideaway on 2014-01-13
> **strattonbrazil said:**
> How did you verify you weren't using the Intel drivers?  Did you just go to the xorg-edgers PPA and mark "xserver-xorg-video-intel" for complete reinstall?

Yep basically!

---


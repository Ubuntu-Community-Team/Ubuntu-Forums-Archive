---
title: "Dell Inspiron 1420"
date: 2008-12-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Lief on 2008-12-28
Completely new to ubuntu, first post on the forum, probably the first begging for help thread of many.

I have basic computer skills and decided Ubuntu is a good skill to pick up, am attempting to run it off my laptop however I'm having a really difficult time getting the proper graphics drivers. After blundering through it last night I managed to get git core installed and found a git repository with the driver I need, however, when I attempt to fetch the git repository it comes up with fatal: not a git repository, any ideas? (also on another side note, Ubuntu doesn't seem to want me to access Gmail, made registration hard.)

---

### Post by gettinoriginal on 2008-12-28
Run these to in terminal and it should give you the updated repositories you need.  If you are not running intrepid, just substitute your dist.

```
 sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list 
```

```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update 
```

---

### Post by Lief on 2008-12-28
Ran the two codes, both were successful, re attempted to fetch the git repository came up with the same error, tried just searching for the drivers I needed via utility to no avail. Would it help if I were to post the git repository I'm trying to access?

I assume so:
```
git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel
```

---

### Post by gettinoriginal on 2008-12-28
Hope this helps:  :P

[http://www.x.org/wiki/CompileXserverManually](http://www.x.org/wiki/CompileXserverManually)

---

### Post by Lief on 2008-12-28
Actually, found and downloaded the actual tar.gz file in one of the repositories in the guide, any chance you could tell me how to install/activate/unzip whatever the proper terminology would be?

---

### Post by gettinoriginal on 2008-12-28
This is different than windows, just right click the file and "extract", read the "read me" file for installation instructions.  A good guide to installation is here. 

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Lief on 2008-12-28
Sorry to keep bothering, no installation instructions found, is there a way to just run it in terminal?

After extracting when attempt to 
```
./configure
    make
    su
    make install
``` 
It just tells me that the command/commands are not found, do I need to get something else to do this?

---

### Post by Lief on 2008-12-28
Ahead of time - Sorry for the double post.
 I'm off to work, I'll leave this screen up and check it when I'm back so feel free to post if you can think of anything to solve my problem.
 I think my biggest problem here is that I'm having a hard time understanding the very basic terminology making the guides difficult to understand, so feel free to dumb it down for me :)

---

### Post by gettinoriginal on 2008-12-28
```
 gksu make install 
```

---

### Post by Lief on 2008-12-28
All ready for work, leaving in a couple minutes, tried the gksu it seemed to do something but it didn't install it, would it help if I told you that this is a graphics driver (to be specific the file is <xf86-video-intel-2.5.99.1>) sorry for the difficulty again, see you in 6 hours :)

---

### Post by gettinoriginal on 2008-12-28
Then just try:

```
 sudo apt-get install xf86-video-intel-2.5.99.1 
```

---

### Post by iggykoopa on 2008-12-28
just wondering if your trying to get testing versions of the drivers or something? I have a 1420, the graphics drivers are included by default if you have the intel card. If you have the nvidia you just need to go to the hardware drivers section (it should come up automatically) in the system menu, and enable the drivers.

---

### Post by Lief on 2008-12-29
Heres how the whole thing started, I got a new HD dock for Christmas and decided, hey I can finally run ubuntu, so inspiron 1420 originally with vista now has Ubuntu, this whole graphics driver problem stemmed from me wanting to enable visual effects (figured it would be an easy enough learning experience)

 I went to enable visual effects and it attempted to search for a driver, not finding one my computer proceeded to tell me that it was incapable of enabling visual effects (even on a normal level)

 I don't really know where I should be going for drivers I was just poking around on various websites and repositories looking for what I needed, if you guys could disect the situation and tell me what I need for my intel graphics inspiron 1410 I would be much obliged. 

Apologies for the block of text.

---

### Post by gettinoriginal on 2008-12-29
iggykoopa he has intel, I have nividia, maybe you are better at helping than me, so I will back out for now.  :P

---

### Post by notwen on 2008-12-29
Dell releases custom Ubuntu images that cover all their N-Series models, including the different GPUs available on said models.  I own a Inspiron 1420n(shipped w/ Feisty) and am currently running Hardy w/o any issue.  Check [here]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Dell_OS_Factory_Recovery_8.04.1_DVD_ISO") for more information regarding the Dell restore DVD.  Keep in mind that this will wipe your machine and install Ubuntu, so if you do proceed w/ installing don't forget to backup any data you want.  =]

---

### Post by Lief on 2008-12-29
I actually tried using that DVD but I popped my internal hard drive first (running vista on it for school purposes) it wont install properly on an external hard drive which is the basis of my need to get a graphics driver :) (I'm just an annoying little puzzle aren't I?)

---

### Post by notwen on 2008-12-30
You popped it?   Have you tried dual-booting and eliminating the need of installing onto a external HDD?

---edit---
[Dual Boot Ubuntu/Vista, Vista installed first.]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")

---

### Post by Lief on 2008-12-31
> **notwen said:**
> You popped it?   Have you tried dual-booting and eliminating the need of installing onto a external HDD?

---edit---
[Dual Boot Ubuntu/Vista, Vista installed first.]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")


Overall problem was solved, I'm becoming addicted to ubuntu so I may just do the daul boot just so that I can run it anywhere I go...

---


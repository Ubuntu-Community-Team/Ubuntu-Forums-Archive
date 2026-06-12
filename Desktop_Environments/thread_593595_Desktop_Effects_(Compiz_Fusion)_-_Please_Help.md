---
title: "Desktop Effects (Compiz Fusion) - Please Help"
date: 2007-10-27
forum: Desktop Environments
---

### Post by pigbig842001 on 2007-10-27
**Desktop Effects (Compiz Fusion) - Please Help**

Hi,

I've a problem related to desktop effects. I had Ubuntu 7.04 (Feisty Fawn, i386 version) installed earlier. I went with **Driver CD install** option. Everything worked fine and I was able to run **Desktop Effects**.

Now, I did a fresh installation of Ubuntu 7.10 (Gutsy Gibbon, AMD64 version). I went through the same way. Now, I am unable to run desktop effects. It keeps on saying that it can not be run. Where could be the problem.

**My system specifications:**
Intel Core 2 Duo E4400, 2.0 GHz
Intel DG965WH motherboard
Integrated Graphics, GMA X3000, 256 MB (If run on DVMT mode then it's 384 MB).
RAM - 1 GB, 667 MHz (2 x 512 MB)

If I run **glxinfo** then it says that **direct rendering - yes**.

I don't see any reason why my system can't run compiz-fusion if **I can run the heaviest graphics games gracefully**.

Please Help. :mad: :confused: :(

---

### Post by crash0 on 2007-10-27
there's a similiar thread somewhere on this forum. it says that some graphic cards are blacklisted on compizfusion for now because of some bugs. i have the same problem as you do and i hope there will be a fix soon.

---

### Post by qbox on 2007-10-27
try this

go to jou home directory and make a file ~/.config/compiz/compiz-manager and put in it the line:

SKIP_CHECKS=yes

---

### Post by pigbig842001 on 2007-10-27
> **qbox said:**
> try this

go to jou home directory and make a file ~/.config/compiz/compiz-manager and put in it the line:

SKIP_CHECKS=yes
your methods seems promising. let me try this. thanx

---

### Post by pigbig842001 on 2007-10-27
> **qbox said:**
> try this

go to jou home directory and make a file ~/.config/compiz/compiz-manager and put in it the line:

SKIP_CHECKS=yes
Hi,
Thank God, your method worked and finally I could get compiz-fusion running. 
 
The following are running:
1) Alt+Tab.
2) Wobbly windows and sticky windows.
3) Zoom.
 
But there are many things which are not enabled.
1) There is no cube rotation, instead the windows just slides to left/right. I am very disappointed.
2) Scaling is not working.
3) There is no water effect.
4) There is no film effect.
5) Except for the three mentioned above, nothing is working.
 
Is this the end of compiz-fusion on Ubuntu 7.10? Where are the guts of Gutsy Gibbon?
 
Please Help.

---

### Post by justsomedude on 2007-10-27
Don`t worry, all the effects you want are there. 

Just install the *compizconfig-settings-manager* and you`ll be fine.

:)

---

### Post by pigbig842001 on 2007-10-28
> **justsomedude said:**
> Don`t worry, all the effects you want are there. 

Just install the *compizconfig-settings-manager* and you`ll be fine.

:)
Hi, thanks for your input.
 
I tried installing CCSM deb package but it won't install. It's giving some **python error.**
 
Is there any deb package for CCSM which can be installed on Ubuntu without a glitch??? I need a package suitable for AMD64 system. My python verision is 2.5 which is default for ubuntu.

---

### Post by justsomedude on 2007-10-28
Where did you get this package?

It's available in the repos (I'm on 32bit, but I'm sure you can get it for 64bit, too):

```
sudo apt-get install compizconfig-settings-manager
```

Or do a search for "compiz" in Synaptic, you'll find it...

If you have trouble configuring, check out this link:

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

Have fun! :-)

---

### Post by qbox on 2007-10-28
> **pigbig842001 said:**
> Hi,
Thank God, your method worked and finally I could get compiz-fusion running. 
 
The following are running:
1) Alt+Tab.
2) Wobbly windows and sticky windows.
3) Zoom.
 
But there are many things which are not enabled.
1) There is no cube rotation, instead the windows just slides to left/right. I am very disappointed.
2) Scaling is not working.
3) There is no water effect.
4) There is no film effect.
5) Except for the three mentioned above, nothing is working.
 
Is this the end of compiz-fusion on Ubuntu 7.10? Where are the guts of Gutsy Gibbon?
 
Please Help.

You have the effects but you need to enable it.
System->Preferences->Advanced Desktop Effects Settings
There is a list with effects. Enable that you want and enjoy :)

---

### Post by pigbig842001 on 2007-10-30
Let me tell you the actual story.
 
1) The place where I live has no internet connection. So forget about **aptitude.**
 
2) I have only one source of internet and that is GPRS. But, I was unable to make correct settings and hence thought that I can't use **aptitude**.
 
3) But, now after working on it for more than 12 hrs. continuously I could use **wvdial** to make stable GPRS connection.
 
4) Now, I am at a liberty to download CCSM (CompizConfig Settings Manager).
 
5) I have downloaded CCSM and all the plugins are running properly.
 
Thanks everybody.

---

### Post by pigbig842001 on 2007-10-30
Scaling's still not working. CTRL+ALT+UP doesn't work. Rest is fine.
 
any leads so that scaling works???

---

### Post by dboot on 2007-11-02
I don't mean to take over this thread, but it would be great if I could get some help with my graphics card + compiz fusion problem.

After installing restricted drivers and configuring my xorg.conf file to use the nvidia driver, I installed compiz. Initially I tried enabling the Advanced Desktop Effects but I get an error stating that I can't. I suppose my graphics card it blacklisted, so I created the compiz file mentioned a few posts back. The error didn't come up but the windows that I had open turned black. I could still see the top of the windows but the "content" turned black and was useless.

I have a Dell c840 Laptop with a GeForce 440 Go graphics card. 
"grep | direct rendering" returns yes.

Do I have any options with a blacklisted (for good reasons apparently) graphics card?

Any help would be appreciated!

---

### Post by dancallo1190 on 2007-11-02
> **pigbig842001 said:**
> **Desktop Effects (Compiz Fusion) - Please Help**

Hi,

I've a problem related to desktop effects. I had Ubuntu 7.04 (Feisty Fawn, i386 version) installed earlier. I went with **Driver CD install** option. Everything worked fine and I was able to run **Desktop Effects**.

Now, I did a fresh installation of Ubuntu 7.10 (Gutsy Gibbon, AMD64 version). I went through the same way. Now, I am unable to run desktop effects. It keeps on saying that it can not be run. Where could be the problem.

**My system specifications:**
Intel Core 2 Duo E4400, 2.0 GHz
Intel DG965WH motherboard
Integrated Graphics, GMA X3000, 256 MB (If run on DVMT mode then it's 384 MB).
RAM - 1 GB, 667 MHz (2 x 512 MB)

If I run **glxinfo** then it says that **direct rendering - yes**.

I don't see any reason why my system can't run compiz-fusion if **I can run the heaviest graphics games gracefully**.

Please Help. :mad: :confused: :(

I have Ubuntu 7.10 Gusty Gibbon installed on my Dell Dimension 2300 Tower, which has an AGP Graphics card with 32MB RAM and I'm able to run all the special effects including the cube effects with compizconfig-settings-manager installed and configured.

---

### Post by pigbig842001 on 2007-11-10
Thanx everybody. Now compiz is running properly. There is only one problem. Recently I installed Xgl and water effect is running nicely (before that water effect wouldn't run).
 
But, now, **glxinfo** report says that **direct rendering** is not there.
 
Any ideas?

---

### Post by Motorhead Kaze on 2007-11-11
Hmmm.  Well I have a similar trouble in that I too have no cube, but I followed the download steps to get Compiz and Emerald via the command line, have all the goodies ticked (cube, rotation, etc), have my desktop size set correct, and there are wobbly windows, super and tab does it's cool thing, but no cube.

Why is that?  I'm not yearning for the cube, I just can't stand it when things don't work after I follow the directions.

---

### Post by Don9307 on 2007-11-13
I too have all the goodies checked on compiz-fusion setup on my E-Machine and I too do not get a cube.  What I get is a rotating cube experience in which it looks like I'm on the inside of the cube looking out vs. outside of the cube.   This works fine on my laptop, just not my desktop.  It has to be related to the difference in graphics card in some way.

---


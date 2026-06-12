---
title: "Ubuntu Unity Desktop doesn't display icons"
date: 2011-08-03
forum: Desktop Environments
---

### Post by themanyfaces on 2011-08-03
My Ubuntu system runs a "blacklisted" video card, which i have bypassed. I am able to use Compiz fine with no problems for Ubuntu Classic, and i can use unity... only one problem :/

The icons in the unity Launcher don't display. I know they are there, and I can interact with them, but I can't see them.

---

### Post by themanyfaces on 2011-08-04
help?

---

### Post by apollothethird on 2011-08-04
> **themanyfaces said:**
> My Ubuntu system runs a "blacklisted" video card, which i have bypassed. I am able to use Compiz fine with no problems for Ubuntu Classic, and i can use unity... only one problem :/

The icons in the unity Launcher don't display. I know they are there, and I can interact with them, but I can't see them.

Try running "Aditional Drivers" from the System -> Administration menu.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by themanyfaces on 2011-08-04
> **apollothethird said:**
> Try running "Aditional Drivers" from the System -> Administration menu.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")
I have the latest nVidia Drivers for ubuntu... Compiz works... the Unity launcher bar doesn't have icons though... I'm using Unity 2D for right now...

---

### Post by apollothethird on 2011-08-04
> **themanyfaces said:**
> I have the latest nVidia Drivers for ubuntu... Compiz works... the Unity launcher bar doesn't have icons though... I'm using Unity 2D for right now...

Did you run additional drivers?

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by themanyfaces on 2011-08-05
Yes I did... And i got nothing new.

It says the 'No Propritary drivers are in use.." and i am using the only one in the list.
Below it says the the driver is activated, but not in use...

---

### Post by apollothethird on 2011-08-05
> **themanyfaces said:**
> Yes I did... And i got nothing new.

It says the 'No Propritary drivers are in use.." and i am using the only one in the list.
Below it says the the driver is activated, but not in use...

There are lots of steps to get the proper support for running Unity 3d.  I had problems with one of my cards.  I followed all the suggestions for a long time and finally got it working.  I'm not sure exactly which of the steps got it working.  But I can go over the steps with you.

I did lots of reading.  Some of the readings appeared to suggest that my card wasn't supported.

Which video card do you have, by the way.  Is this video card correctly named in your xorg.conf file?

What is the driver nvidia driver version you're currently running?

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by themanyfaces on 2011-08-05
> There are lots of steps to get the proper support for running Unity 3d.   I had problems with one of my cards.  I followed all the suggestions  for a long time and finally got it working.  I'm not sure exactly which  of the steps got it working.  But I can go over the steps with you.

I did lots of reading.  Some of the readings appeared to suggest that my card wasn't supported.

Which video card do you have, by the way.  Is this video card correctly named in your xorg.conf file?

What is the driver nvidia driver version you're currently running?

-- L. James

Graphics Card: nVidia GeForce 5500
Driver: NVIDIA accelerated graphics driver (version 173)
I dont know how to read an xorg.conf file... like what means what in it...

Compiz works just fine for Ubuntu classic, and i am using Metacity's compositing for Unity 2D...

---

### Post by apollothethird on 2011-08-05
> **themanyfaces said:**
> Graphics Card: nVidia GeForce 5500
Driver: NVIDIA accelerated graphics driver (version 173)
I dont know how to read an xorg.conf file... like what means what in it...

Compiz works just fine for Ubuntu classic, and i am using Metacity's compositing for Unity 2D...

If you're mentioning Unity 2D because you're satisfied with it and not interested in working toward Unity 3D support let me know.  I'll stop trying to help getting the 3D support activated.  I believe about the only thing you're missing is fancy visual effects.

The xorg.conf file can be found in /etc/X11.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by themanyfaces on 2011-08-05
> **apollothethird said:**
> If you're mentioning Unity 2D because you're satisfied with it and not interested in working toward Unity 3D support let me know.  I'll stop trying to help getting the 3D support activated.  I believe about the only thing you're missing is fancy visual effects.

The xorg.conf file can be found in /etc/X11.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)
I am mentioning Unity 2D because I have modified it so the launcher is always visible, which causes some errors else where. I want to use Unity 3D because the "Always show" Option is supported and doesn't cause errors.
While yes I am sort of satisfied with Unity 2D, i would like to use officially supported Unity 3D, which will have updates more often then Unity 2D.
I use the nVidia x server settings program to modify the xorg.conf file.

---

### Post by themanyfaces on 2011-08-05
okay?

---

### Post by apollothethird on 2011-08-05
> **themanyfaces said:**
> I am mentioning Unity 2D because I have modified it so the launcher is always visible, which causes some errors else where. I want to use Unity 3D because the "Always show" Option is supported and doesn't cause errors.
While yes I am sort of satisfied with Unity 2D, i would like to use officially supported Unity 3D, which will have updates more often then Unity 2D.
I use the nVidia x server settings program to modify the xorg.conf file.

Both Unity 3D and Unity 2D is officially supported by Unity.  Someone else might have suggestions on fixing the Unity 2D problem.  Since I have a lot of experience with making Unity 3D work, I was going over the things I did (or would do) for a computer I was having problems with running Unity 3D, which I resolved in two computers.

Most likely xorg.conf has your video card by name since you used the nvidia program to modify it.  Can you tell me if the video card is in the xorg.conf file by the your correct video card name and model/version?

Also, did you manually run nvidia-xconfig from a console screen?

You might have done everything that I come up with, or you might not have.  But on two machines in my shop, 3D didn't work until I spent many hours researching and changing configurations until I got it working.  I was on the verge of buying a new video card for both machines, but stayed with the steps I'm going over with you, which eventually brought Unity 3D support.

I still have a machine that doesn't work with 3D.  I've mostly given up on that machine and run it in 2D.  I'll eventually purchase another video card for it.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by themanyfaces on 2011-08-05
okay... I ran The nVidia program from the launcher. Can you tell me what you did to make unity 3d work? I am running Natty on a Compaq Presario SR1010Z. Thank you so far :)

---

### Post by apollothethird on 2011-08-05
> **themanyfaces said:**
> okay... I ran The nVidia program from the launcher. Can you tell me what you did to make unity 3d work? I am running Natty on a Compaq Presario SR1010Z. Thank you so far :)

I did everything I'm mentioning to you and more.  Many of the things I did probably didn't make any difference.  I'm going over some of the major items that I think gave me 3D support.

Can you tell me if your card is mentioned by the model/version number in your xorg.conf file?

By the way, I don't see the nvidia-xconfig program in the launcher.  It's not there by default.  Did you put it into yours.  The nvidia application in my launcher assisted in my configuration, but running it didn't give me immediate Unity 3D support.  It might for some people, but it didn't for me.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by themanyfaces on 2011-08-05
> **apollothethird said:**
> I did everything I'm mentioning to you and more.  Many of the things I did probably didn't make any difference.  I'm going over some of the major items that I think gave me 3D support.

Can you tell me if your card is mentioned by the model/version number in your xorg.conf file?

By the way, I don't see the nvidia-xconfig program in the launcher.  It's not there by default.  Did you put it into yours.  The nvidia application in my launcher assisted in my configuration, but running it didn't give me immediate Unity 3D support.  It might for some people, but it didn't for me.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")
I ran it from the dash thing when you click on the Ubuntu logo.

i've also atached a copy of my xorg.conf file... i have changed the file format though...

---

### Post by themanyfaces on 2011-08-06
Help?

---

### Post by apollothethird on 2011-08-06
> **themanyfaces said:**
> I ran it from the dash thing when you click on the Ubuntu logo.

i've also atached a copy of my xorg.conf file... i have changed the file format though...

What is the name of the program you ran.  I have specified a few times the program that should be run.  I don't think you have run this program.


-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by themanyfaces on 2011-08-06
nvidia-xconfig

---

### Post by apollothethird on 2011-08-06
> **themanyfaces said:**
> nvidia-xconfig

I'm surprised... extremely surprised.  I don't find nvidia-xconfig in the launcher of any of my many installations.  You're probably having problems because you've made many significant changes from the distro.  I'm very careful to stay with the distro provided configurations to insure compatibility to what the developers and contributors have thoroughly tested.

I don't mind helping people who have changed their distros to something else, but I feel it important to know, this will help me be prepared for anomalies.

Can you give me the output of:

```
/usr/lib/nux/unity_support_test -p
```

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by themanyfaces on 2011-08-06
```
Warning: UNITY_FORCE_START enabled, no check for unity or compiz support.
nickolas@nickolas:~$ 

```

---

### Post by apollothethird on 2011-08-06
> **themanyfaces said:**
> ```
Warning: UNITY_FORCE_START enabled, no check for unity or compiz support.
nickolas@nickolas:~$ 

```

It looks like you've done a lot of things.  How many video card driver versions have you tried?

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by themanyfaces on 2011-08-06
I only have one driver to choose from :/

---

### Post by apollothethird on 2011-08-06
> **themanyfaces said:**
> I only have one driver to choose from :/

There are a number of nvidia drivers you can choose from.

Backup your xorg.conf.  Try a version (using synaptic) with a higher number.  Try version 270.41.  Let me know how it goes.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by markmailhot on 2011-08-07
i am also having the same problems. i couldn't get my computer to load into unity with the nvidia 173 driver also the newer drivers don't support my card(old budget computer) i did get the 2d unity to work. but would like to use 3d. do you think my card is to old to support it? it is a nvidia fx 5 5200

---


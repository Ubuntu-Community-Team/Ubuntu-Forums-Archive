---
title: "Xfce 4.4 Release Candidate 2 (4.3.99.2) released"
date: 2006-11-05
forum: Desktop Environments
---

### Post by shunthemask on 2006-11-05
I was wondering whether anybody had any experience with it yet, but then i realized that it had only been posted 3 hours ago.

A word of caution, I had a very tough time with RC1 - so much so that I went back to Beta 1 (the default with Xubuntu 6.06).  But, the release notes state that some memory leaks have been plugged which is exactly what I was looking for.

[http://www.xfce.org]("http://www.xfce.org")

Anybody have feedback yet?

---

### Post by kalikiana on 2006-11-06
I do have no critical problems with RC1, but I am waiting for a fix for xfdesktop and easpecially the new features in thunar and xarchiver.

However, the repository hasn't been updated yet and I will be really disappointed if I must mess up my system with a manual install again.

---

### Post by videodrome on 2006-11-06
I just ran the installer and it appears to have correctly updated a vanilla edgy xubuntu system without any problems.

Note that you have to 

1) install the libvte-dev package before installing.

2) make the xfce4-4.4RC2-installer.run file executable.

3) run the installer like this: sudo ./xfce4-4.4RC2-installer.run

---

### Post by shunthemask on 2006-11-08
I ran the installer and it installed with no hitches (after i I installed the libvte-dev package) but my two issues with the rc2 install were that the trash didn't work in thunar and my jumpdrives didn't automount in thunar.  I remedied the trash issue by taking ownership of the ~/.local/share/Trash from the root account.  The second issue, I don't know how to remedy, which I think is kind of weird since I am using all of the same configuration files from the same user account.

> **kalikiana said:**
> 
However, the repository hasn't been updated yet and I will be really disappointed if I must mess up my system with a manual install again.


I don't think that you shall mess up your system if you install a new version of xfce as long as you don't overwrite your currently installed version.  I am running Xubuntu 6.06 and when I got to gdm I just chose the Xfce 4.4 session instead of the Xfce session to use the rc2 version.

---

### Post by josys36 on 2006-11-08
Installing now so I will post how it went and how I feel about it. Right now I love XFCE for some items, and gnome for others.

Jason

---

### Post by josys36 on 2006-11-08
Well I installed and then un-installed. what I don't get is why when I install xubuntu-desktop my fonts and windows look fine. If I install XFCE using their installer it looks like crap. The window titles are so small I can't read them, and then the menus in firefox are so freaken huge they look like fisher price designed them. 

Is there an easy way to install this thing and then copy over the settings from xubuntu's XFCE? I just wish they would put the darn thing in the repos and be done with it.

Jason

---

### Post by shunthemask on 2006-11-08
> **josys36 said:**
> Well I installed and then un-installed. what I don't get is why when I install xubuntu-desktop my fonts and windows look fine. If I install XFCE using their installer it looks like crap. The window titles are so small I can't read them, and then the menus in firefox are so freaken huge they look like fisher price designed them. 

Is there an easy way to install this thing and then copy over the settings from xubuntu's XFCE? I just wish they would put the darn thing in the repos and be done with it.

Jason

If you log in with the same account, then your xfce settings should be carried over, at least in my understanding.  All of your settings should be in the ~/.config directory.  As for putting it in the repos, that would be an entirely new release of xubuntu, which is just ubuntu with the xubuntu-desktop package on top.  So, we wait...

---

### Post by kalikiana on 2006-11-09
I did now install RC2 because I don't want to wait for Feisty to get an update. In fact, I used the graphical installer, installed it to /usr and it works like a charm. I suggest not to choose a different location except ~/ because that can mess it all up very easily - which is why my effort to use RC1 on Dapper originally failed.

---

### Post by josys36 on 2006-11-09
> **shunthemask said:**
> If you log in with the same account, then your xfce settings should be carried over, at least in my understanding.  All of your settings should be in the ~/.config directory.  As for putting it in the repos, that would be an entirely new release of xubuntu, which is just ubuntu with the xubuntu-desktop package on top.  So, we wait...

That is what I would have thought too. But every time I have done this, I sign in with the same account and my fonts and window sizes go wacko. Maybe I need to copy over some configuration settings from the .config directory?

Jason

---

### Post by josys36 on 2006-11-09
What I am going to do tonight is remove xubuntu-desktop and then just install the RC2 from XFCE. I will post what happens here. I will also remove the .config files before I try to do an install. Just so I can be sure that the install creates it's own.

Jason

---

### Post by josys36 on 2006-11-09
Well I think I figured out what was causing my issues. Every time I turn on sub-pixel hinting my fonts and screen go nuts. What makes it really funny is that if I turn it off and log back out and in the problem is still there. The only way to fix it is to remove the xfce files from .config. I have to re-setup the desktop, but that is OK with me.

Jason

---

### Post by dannyboy79 on 2006-11-09
i am running dapper xubuntu and i have already upgraded thunar to the second latest release since a new one just came out but i am thinking about just doing all of xfce like you guys. i know that when I tried rc1 it didn't work and I ended up just reinstalling xubuntu from scratch. one thing that is weird is what the guy above stated, he said, " In fact, I used the graphical installer, installed it to /usr and it works like a charm. I suggest not to choose a different location except ~/" 

now I don't know what that means because at first he says he installed it to /usr but then he says you shouldn't install it to anything except the root folder/partition, or am i not understanding what ~? means? can some1 help and then also inform me what they did to get the graphical installer to work? also, i have an ancient laptop, 266mhz Pentium MMX with 128mb ram, and am pretty happy right now, my thunar has trash support, I installed xffm-samba from source so i can browse samba shares. i tried installing all of xffm but that wouldn't work, it kept saying that I didn't have something installed even though when I went to look for it, it was there>?

---

### Post by kalikiana on 2006-11-09
> **dannyboy79 said:**
> 
now I don't know what that means because at first he says he installed it to /usr but then he says you shouldn't install it to anything except the root folder/partition, or am i not understanding what ~? means? can some1 help and then also inform me what they did to get the graphical installer to work?

I'm sorry as my post appears to have been a bit unclear. So... when I had Xubuntu Dapper and updated XFCE to RC1, I chose to install it to my home folder and that worked. But I decided that I'd really prefer a system wide install, so I removed it and installed it under /usr/local which was the installer's default suggestion. Unfortunately that resulted in multiple versions of e.g. Thunar and other apps and therefore many things did not work as expected anymore.
Finally I decided to upgrade to Xubuntu Edgy. So the upgrade magically fixed all the problems I had encountered with the faulty RC1 installation. Since RC2 came out then I naturally wanted to have that version and so I tried the installer again, but this time chose /usr as the installation folder. Now it works like a charm. So I recommend to install to either /usr for a system-wide setup or your home folder for a user setup.

---

### Post by dannyboy79 on 2006-11-09
i have dapper though, you are saying that it worked for you and you;re in edgy correct?>

---

### Post by kalikiana on 2006-11-09
> **dannyboy79 said:**
> i have dapper though, you are saying that it worked for you and you;re in edgy correct?>

I have Edgy now, that is correct. I assume if you install to the correct path (/usr), the installer should work for you just fine as for the problems I had. In case there is an additional Dapper specific problem I can't help you out.

---

### Post by josys36 on 2006-11-10
> **dannyboy79 said:**
> i am running dapper xubuntu and i have already upgraded thunar to the second latest release since a new one just came out but i am thinking about just doing all of xfce like you guys. i know that when I tried rc1 it didn't work and I ended up just reinstalling xubuntu from scratch. one thing that is weird is what the guy above stated, he said, " In fact, I used the graphical installer, installed it to /usr and it works like a charm. I suggest not to choose a different location except ~/" 

now I don't know what that means because at first he says he installed it to /usr but then he says you shouldn't install it to anything except the root folder/partition, or am i not understanding what ~? means? can some1 help and then also inform me what they did to get the graphical installer to work? also, i have an ancient laptop, 266mhz Pentium MMX with 128mb ram, and am pretty happy right now, my thunar has trash support, I installed xffm-samba from source so i can browse samba shares. i tried installing all of xffm but that wouldn't work, it kept saying that I didn't have something installed even though when I went to look for it, it was there>?

There is a post here somewhere that outlines what dependencies will be required if you want to install XFCE from XFCE.org. Really it was an easy process once the dependencies are there. Just do a search for XFCE and there is a post on how to install RC1. The process is the same for RC2 so you should have no trouble. 

Jason

---

### Post by dannyboy79 on 2006-11-10
i already have xfce installed (i run xubuntu dapper), that I believe is or was the problem. I did try the rc1 graphical installer back when it first came out, it didn;'t end up working, don't know why? Thanks anyway for posting those links.

---

### Post by IMS3 on 2006-11-10
For those who are finding it difficult to install Xfce check out:

[http://www.os-works.com/documentation/xfce-installers/4.2.0/xfce-installer/](http://www.os-works.com/documentation/xfce-installers/4.2.0/xfce-installer/)

There are a few dependancies that need to be sorted.

They can be fixed by reading the link above.

There is also an error that I encountered during the setup.

To fix that I installed the development package for the package name that appeared at the bottom of the error log file and then ran setup again.

Use Synaptic Package Manager to install the packages needed.

Then restart to update new Xfce interface.

---

### Post by josys36 on 2006-11-10
Here is the post I spoke of before.

[http://ubuntuforums.org/showthread.php?t=251350](http://ubuntuforums.org/showthread.php?t=251350)

There is one minor correction that has to be made. The post has a list of dependencies that should be installed. One is wrong. It says libdbh1.0-dev where it should just say libdbh-dev. If you have these then you have the dependencies for installing XFCE. 

Also, Once you are in the graphical installer I had to shut off the following items to get it to install. 

1. Debugging
2. The volume control. 

Other then that it installed fine.

Jason

---

### Post by dannyboy79 on 2006-11-11
> **josys36 said:**
> Here is the post I spoke of before.

[http://ubuntuforums.org/showthread.php?t=251350](http://ubuntuforums.org/showthread.php?t=251350)

There is one minor correction that has to be made. The post has a list of dependencies that should be installed. One is wrong. It says libdbh1.0-dev where it should just say libdbh-dev. If you have these then you have the dependencies for installing XFCE. 

Also, Once you are in the graphical installer I had to shut off the following items to get it to install. 

1. Debugging
2. The volume control. 

Other then that it installed fine.

Jason

Jason, thank you for the tips but could you please inform newbies like myself how I would shut off debugging and volume control after you are in  the installer? thank you

---

### Post by shunthemask on 2006-11-11
> **josys36 said:**
> 

Also, Once you are in the graphical installer I had to shut off the following items to get it to install. 

1. Debugging
2. The volume control. 



I don't recall what package I installed to get alsa to work, but I vaguely remember that I had to install one.  I think that it was one of these:

alsa                            -
alsa-base                       - ALSA driver configuration files
alsa-oss                        - ALSA wrapper for OSS applications
alsa-utils                      - ALSA utilities

I agree with turning off the debugging, at least you have to do so to enable the optimizations :-D .

---

### Post by dannyboy79 on 2006-11-11
ok, well now thats 2 people that say you should turn off debugging but neither tel a newbie how?? can anyone help with how to turn off volume control and debugging? thank you if you can

---

### Post by shunthemask on 2006-11-11
> **dannyboy79 said:**
> ok, well now thats 2 people that say you should turn off debugging but neither tel a newbie how?? can anyone help with how to turn off volume control and debugging? thank you if you can

When you run the graphical installer a dialogue box comes up asking whether you want to enable optimizations, enable debugging, use alsa and something else.

---

### Post by josys36 on 2006-11-13
> **dannyboy79 said:**
> ok, well now thats 2 people that say you should turn off debugging but neither tel a newbie how?? can anyone help with how to turn off volume control and debugging? thank you if you can

Sorry about that! Once the graphical installer can compile it will come up with a dialog box where you can make some choice about how XFCE will be compiled. From there you can shutoff the debug, disable the volume control, and turn on the extensive optimizations. I would post a screen shot for you but I don't have the graphical installer here since I am working right now in Windows.

Jason

---

### Post by sawjew on 2006-11-28
I tried this on my ubuntu desktop system and just installed the default xfce and it works quite well but I wanted to upgrade my laptop running xubuntu and keep everything working together as it already is.  To upgrade to rc2 I just added the Debian unstable repository ```
deb http://ftp.debian.org unstable main
```

I then just used synaptic to select all the xfce and thunar related packages and upgrade them.

afterwards I unchecked the debian repository and rebooted to make sure and it's all there and working perfectly including compositing.

I love the new software uninstaller and the printing dialogs.

---


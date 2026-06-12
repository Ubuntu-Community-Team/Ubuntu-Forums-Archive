---
title: "Lousy UT2004 Ubuntu Performance"
date: 2005-02-05
forum: Gaming &amp; Leisure
---

### Post by rlwelch on 2005-02-05
Hey. 

UT2004 and installs on my Ubuntu system, but I'm having some problems.
1) The performance sucks. Even on "normal" details at 800*600 I'll average about 30FPS, with dips down to 20FPS, on ONS-Torlan. It's ugly and slow!I have a Gefore 6800 and an Athlon XP 2800+. The game should not be this slow. In Windows I would be getting 50-60FPS constantly with high settings at 1024*768  :|   Is it supposed to be this way? Is this just due to the lousiness of the UT2004 OpenGL engine? Do any other Ubuntu users notice this?

2) EDIT: resolution problem solved! I had to edit the ~/.ut2004/System/UT2004.ini file to change the resolution

Can anyone help me out?

---

### Post by wnaLinux on 2005-02-06
Have you tryed adding the render accelaration option in your XF86Config-4 file. If not do the following:

sudo gedit /etc/X11/XF86Config-4

Find this section:

 Section "Device"
        Identifier      "NVIDIA Corporation NV34M [GeForce FX Go 5200]"
        Driver           "nvidia"
        BusID           "PCI:1:0:0"

Add this below:

        Option          "RenderAccel"           "true"
        Option          "NvAGP"                     "1"

After you have done that save the edited file. Since you are already  are running X windows the configuration won't apply until you restart X. To restart X press CRTL+ALT+BACKSPACE.

Hope this helps!

---

### Post by Phreakazoid on 2005-02-06
Low performance could (possibly) be caused by the nvidia drivers in the warty repositories which are fairly old now (6111, when the latest is 6629).  There was recently a fairly significant boost for performance in a recent nvidia driver release, but I can't remember which version it was.  This brought the linux nVidia OpenGL performance on par with the Windows drivers.

---

### Post by MrPsycho on 2005-02-06
I have a strange performance problem in that the game freezes for a second every time I encounter a new model.  After playing a map for awhile, I will have seen all the models and I don't get the hiccups anymore.  Not sure exactly how to fix that..

Anyways so this thread gave me an idea.  Would it work to upgrade the nvidia drivers manually
[http://www.nvidia.com/object/linux_display_ia32_1.0-6629.html](http://www.nvidia.com/object/linux_display_ia32_1.0-6629.html) available here
instead of an apt-get?

I can't find any repositories which host the latest deb of the drivers.  Would I break my system if I installed from the binary?

---

### Post by valadil on 2005-02-06
Try the hoary repositories.  You may have to dl some other dependencies from hoary, but it should be cleaner this way than the binary would be.

---

### Post by wnaLinux on 2005-02-06
I think this will help you: 

[http://www.ubuntuforums.org/showthread.php?t=12823](http://www.ubuntuforums.org/showthread.php?t=12823)

It has been tested on your video card series (geforce 6800) so give that a try. I would also add the option that I told you about on my first post . If you do those things you should have a damn good display while playing the game.

---

### Post by MrPsycho on 2005-02-06
Thanks for that link.   Heres something from that page:
> 
Note that the repositories for the hoary beta release do include the new driver packages, but it's not advisable to use them with warty.

Ok, how inadvisable is it?  If all I'm using is a precompiled kernel anyways, whats the problem?  I really don't want to go to all the trouble mentioned in that post if I can use Hoary instead. (this is less about convenience and more about avoiding the likely event that I would break something)

---

### Post by arthureggplant on 2005-02-06
Well, I'm not sure I can help figure out why you're having problems, but I will say that I'm using a p4 3ghz with a nvidia5700 and I have the settings maxed, running at 1280x1024 and I have 30fps+ performance. Given that your video card is vastly better than mine, I'd conjecture that you've got other processes running or something that is eating cpu in the background. 

I just switched over from mandrake yesterday and went straight to hoary. I also dumped gnome for kde (which is what i'm used to) and noticed quite a difference in pefromance. Granted this might be because of a better kernel selection and kde, but all and all the machine feels as good as it did on mandrake. 

So to stop rambling, check top before you boot up UT. What's your cpu load going into running UT? if you have access to another machine, you can login to your machine while you've got UT running and see what's going on.

---

### Post by MrPsycho on 2005-02-06
When I mark the upgrade for nvidia-glx on the hoary repository, I get the message:

To be installed
     linux-image-2.6.10-2-386
     linux-restricted-modules-2.6.10-2-386

Does this mean that there isnt a version for my kernel? (2.6.8.1-4-k7)

---

### Post by rlwelch on 2005-02-07
> So to stop rambling, check top before you boot up UT. What's your cpu load going into running UT? if you have access to another machine, you can login to your machine while you've got UT running and see what's going on.
Both the CPU and memory usage are quite low going into the game. I don't think that's the problem. What's very strange is that I can run Doom 3 at better framerates than UT2004 (in Onslaught maps). I thought it must have been a problem with UT2004.

> There was recently a fairly significant boost for performance in a recent nvidia driver release, but I can't remember which version it was. This brought the linux nVidia OpenGL performance on par with the Windows drivers.I was wondering about this. I'm going to try the newest drivers from nVidia's site and see if it does the trick. I'll post back if anything changes.

---

### Post by wnaLinux on 2005-02-11
When your done with that I would also install the latest patch from [www.unrealtournament.com](www.unrealtournament.com) (just to make sure its not a bug with the game) . Let me know what happens.

Good Luck!

P.S. I know how frustrating that can be. RedHat and Fedora have very lousy preformance with UT aswell, overall I have never tryed UT on a debian based system.

---

### Post by jdodson on 2005-02-11
on the ubuntu guide in the nvidia graphics card section there is an area(assuming you are using a nvidia card) on graphics performance.  [http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

anyways, i had a negative effect when i applied that commend, i.e. it slowed games WAY down.  anyways, perhaps you should remove that command(if you use it) or turn it on(if you don't).  i have no idea if it will help, just a thought.

---


---
title: "World of Warcraft working in d3d but not in opengl"
date: 2007-05-04
forum: Gaming &amp; Leisure
---

### Post by marcozs on 2007-05-04
Hi all,

I posted this already but I thought to make it a stand alone post, since the title wasn't really fitting.

I have Feisty running on an AMD 3800+ 1Gb RAM and a Geforce6800U. I followed the HowTo about running WoW. I just skipped the installation step, I copyed the whole WoW folder from my winxp partition into the linux partition.

Then if I run WoW in d3d mode it's playable, about 30fps on 1280x1024. If I try to run it in opengl mode at the same resolution then the fps just drop below 2 and I have a really hard time to get the mouse over the button to exit the game!

It worked in opengl only the first time I run it until I heartstoned to the Outlands... since then the only way to play is in d3d and it really annoys me cause under windows WoW is perfectly fluid in full detail...

I tried to change all the options in setup.rft, even lowering the resolution to 800x600 doesn't slightly improve the fps!!
It's really weird, anyone else experienced the same problem or can suggest a solution?

---

### Post by Filipek on 2007-05-04
> **marcozs said:**
> Hi all,

I posted this already but I thought to make it a stand alone post, since the title wasn't really fitting.

I have Feisty running on an AMD 3800+ 1Gb RAM and a Geforce6800U. I followed the HowTo about running WoW. I just skipped the installation step, I copyed the whole WoW folder from my winxp partition into the linux partition.

Then if I run WoW in d3d mode it's playable, about 30fps on 1280x1024. If I try to run it in opengl mode at the same resolution then the fps just drop below 2 and I have a really hard time to get the mouse over the button to exit the game!

It worked in opengl only the first time I run it until I heartstoned to the Outlands... since then the only way to play is in d3d and it really annoys me cause under windows WoW is perfectly fluid in full detail...

I tried to change all the options in setup.rft, even lowering the resolution to 800x600 doesn't slightly improve the fps!!
It's really weird, anyone else experienced the same problem or can suggest a solution?


I had similar problem but it was not related neither to the game settings nor the system. Sometimes the game does not exit properly in my case and the cache files get corrupted somehow.

After that, it is absolutely necessary to delete the Cache folder in WoW directory (when the game is not active).

However, this is probably not your case since the game runs smoothly in D3D. BTW, why do you want OPENGL when you have 30fps in D3D? :-)

---

### Post by marcozs on 2007-05-04
> **Filipek said:**
> ... the cache files get corrupted somehow.

I didn't think about that... in fact the first times the game crashed so I will try to clean them...

> **Filipek said:**
> However, this is probably not your case since the game runs smoothly in D3D. BTW, why do you want OPENGL when you have 30fps in D3D? :-)

One reason is that 30fps is the top I get... It can drop to 10-15, which is not very nice... 
The second reason is that I cannot stand that it works better in windows :-D

---

### Post by gbesso on 2007-05-04
What video card do you have?
Do you have direct rendering enabled? 
Type the following in a terminal: 
```
glxinfo | grep rendering
```

It should say ```
direct rendering: Yes
```

Are you running it in Wine or Cedega?

---

### Post by marcozs on 2007-05-04
> **gbesso said:**
> What video card do you have?

Nvidia Geforce 6800U

> **gbesso said:**
> Do you have direct rendering enabled?

I do think so, it wouldn't let me use compiz otherwise I guess?

> **gbesso said:**
> Are you running it in Wine or Cedega?

Latest wine from winehq repos for Feisty

---

### Post by gbesso on 2007-05-04
Try the command I posted before and tell me what it says.
Are you running a 32bit or 64bit version of ubuntu?

EDIT: I just realised what you said, you have compiz running. was it running when you tried to play? compiz and beryl are known to cause fps issues in games. try without compiz running.
EDIT2: Oh, and as for cleaning the cache files, don't forget to delete the WDB folder as well, just deleting Cache might not be enough.

---

### Post by marcozs on 2007-05-04
> **gbesso said:**
> EDIT: I just realised what you said, you have compiz running. was it running when you tried to play? compiz and beryl are known to cause fps issues in games. try without compiz running.

I am running the 32bit version. I was aware that compiz could cause problems, so I turn it off while I play... 
I will try the command you metioned when I get home.

P.s. Anyway the only problem I got if I keep compiz on is just that the gnome panel appears in foreground

---

### Post by gbesso on 2007-05-04
Okay, Don't forget to delete your WDB folder too.
I'll check back later.

---

### Post by marcozs on 2007-05-04
> **gbesso said:**
> 
```
glxinfo | grep rendering
direct rendering: Yes
```


Checked and it says like that... tried to clean the cache, no improvements.
Still going ok in d3d but not in opengl :(

---

### Post by gbesso on 2007-05-04
What version of the NVIDIA drivers are you running? you can see by running nvidia-settings and looking at the NVIDIA Driver Version field under System Information.

If the command doesn't work, you can try 
glxinfo | grep NVIDIA

It should say something like 
```
OpenGL vendor string: NVIDIA Corporation
OpenGL version string: 2.1.0 NVIDIA 97.55
```

If it's much older than that, you might want to reinstall the NVIDIA Drivers by getting the package from their website:
[http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)
There are other ways to install it such as the envy script, but that's the only way I've tried personally, and it works fine for me.

Note: To install the drivers using this method you need the linux-headers package that fits your running kernel, and the build-essential package.
```
sudo apt-get install linux-headers-`uname -r` build-essential
```

To install it you need to switch to a VT (Ctrl+Alt+F1) 

Login with your username and password, then type: 
```
sudo /etc/init.d/gdm stop
```
or if you're using Kubuntu 
```
sudo /etc/init.d/kdm stop
```
and then 
```
sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
```

After you install it do 
```
sudo nvidia-xconfig
```

Then to restart gnome do:
```
sudo /etc/init.d/gdm restart
```

Or if you use Kubuntu to restart KDE:
```
sudo /etc/init.d/kdm restart
```

It should switch to X on its own, but if after a few seconds it doesn't, press Ctrl+Alt+F7.

You should have an NVIDIA logo for a second before your login screen shows up.
Good luck.

[COLOR="Red"]NOTE: Every time you upgrade your kernel, for whatever reason, you will need to repeat this process.[/COLOR]

---


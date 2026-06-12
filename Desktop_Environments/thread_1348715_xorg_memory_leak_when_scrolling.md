---
title: "xorg memory leak when scrolling"
date: 2009-12-07
forum: Desktop Environments
---

### Post by countjoe on 2009-12-07
I'm having an odd issue after upgrading to 9.10... Certain apps will cause my system memory usage to grow when I scroll in a window. 

To reproduce, I open gnome-terminal, do something to that generates enough output to scroll the window, move the scroll bar up and down repeatedly, memory grows, then it appears to fill physical memory and then gnome-terminal crashes and then memory is recovered. Under normal use, it happens in gnome-terminal or Eclipse after a few hours of working(I'm a Java developer), and is EXTREMELY frustrating. Top reports memory belonging to Xorg.

Here is some data about my system:

[LIST]
[*]4GB of memory, only 10% in use after boot and launching normally used apps
[*]Kernel is linux-image-generic-pae
[*]Using Gnome desktop, and problem exists with or without compositing enabled
[*]All software is up-to-date as of the time of posting
[*]NVidia GeForce 7300 LE, running dual monitors via TwinView
[*]Scrolling issue confirmed present in:
   * gnome-terminal
   * eclipse galileo
   * gedit
[*]Scrolling issue confirmed NOT present in:
   * firefox
   * gvim
   * open office
[/LIST]

---

### Post by akashiraffee on 2009-12-07
Just to let you know, I installed ubuntu last week, am also a developer, and use a lot of terminals.  

I don't have any memory problems at all, it stays pretty consistent.  Right now I've had it on all day, six workspaces in gnome, 2 or more terminals with multiple tabs at all times, mem is about 40% of 2G.

---

### Post by CodZoY on 2009-12-07
Exact same problem here.
I've been having this for 2 days, and just realized it was caused by scrolling. Google took me here immediately :P.

My system: Ubuntu Karmic 9.10 amd64, Gnome with Compiz, 4GB RAM, ATI HD4850 (I'm using experimental xorg for 3D acceleration, at first I though this was the problem, but you have a GeForce, so I'm not really sure now).


Xorg at boot: 60MB Ram.
Opening gnome-system-monitor and doing some fast scrolls: less than 4 minutes to fill all my RAM.

---

### Post by anpufeng on 2009-12-07
it's really odd,

---

### Post by countjoe on 2009-12-08
I use practically the same software on my laptop, but don't have the problem there. And my laptop is NVidia as well, although I don't use dual-monitors or use the PAE kernel.

---

### Post by countjoe on 2009-12-08
I tried switching to generic (non-pae) kernel, problem persists.

---

### Post by CodZoY on 2009-12-08
I've tried purging the PPA repository for Xorg and reinstalling the Ubuntu official packages, but the problem is still there (plus, with no compositing/Compiz, as I can't have any without those PPA packages).


I haven't seen this filled as a bug anywhere U_U.

---

### Post by Usufruct on 2009-12-08
I've never been so frustrated by not being able to reproduce an issue before :)  I have Karmic on 4 different hardware setups and I have not been able to reproduce it.

---

### Post by countjoe on 2009-12-08
I think I may have narrowed the search ...

There is a bug that people are experiencing with Eclipse where dialog windows aren't functioning properly. The workaround until eclipse is fixed is to set the environment var GDK_NATIVE_WINDOWS=1, which disables a new GTK+ 2.18 feature called client side windows. [details]("http://blog.export.be/2009/10/fixing-eclipse-for-ubuntu-karmic-koala-9-10/")

If I run eclipse with GDK_NATIVE_WINDOWS=1, as the workaround states, then scrolling does NOT grow memory. I'm going to test other apps with this env var.

---

### Post by countjoe on 2009-12-08
Setting GDK_NATIVE_WINDOWS=1 fixes the problem for all apps that were broken.

Now we know the issue is with GTK+ 2.18 client side windows.

---

### Post by CodZoY on 2009-12-08
Thanks for the info countjoe!, that solved the problem :D.

---

### Post by Usufruct on 2009-12-08
Thanks countjoe - I can finally reproduce the issue!

---

### Post by countjoe on 2009-12-08
[Bug Report]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/494189")

---

### Post by Elcid247 on 2009-12-30
hey guys i tried to set GDK_NATIVE_WINDOWS=1 globally but it doesn't work.

i added it to ~/.bashrc, /etc/bash.bashrc, /etc/profile and /etc/environment

nothing! works,

weird thing is it works from inside the terminal, i mean if i open eclipse or whatever from a terminal, it works and

```
$ echo $GDK_NATIVE_WINDOWS
1

```

y doesn't this work with outside applications? i have to run everything from terminal? :S

i've never understood the global variable system in linux really, can some1 tell me where to put this?

thnx

---

### Post by legatek on 2010-01-09
I'm running Jaunty with an ATI card, and the scrolling issue happens for me in Google Chrome browser.

---

### Post by ert45 on 2010-04-15
Hello,

I could not reproduce the scroll bug so maybe the fix I used for the memory leak works.

The solution proposed in [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/186354](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/186354) worked for me: disable xinerama.

On ubuntu 9.04 (using an Intel GMA chipset), I added this at the bottom of my /etc/X11/xorg.conf and then had no more problem after restarting the X server:

Section "Serverflags"
    Option "Xinerama" "false"
Endsection

---


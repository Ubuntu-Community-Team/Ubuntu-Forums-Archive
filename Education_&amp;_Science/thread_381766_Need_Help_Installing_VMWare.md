---
title: "Need Help Installing VMWare"
date: 2007-03-11
forum: Education &amp; Science
---

### Post by Keymaster on 2007-03-11
I downloaded VMWare 5.0.rpm from the vmware website, and used alien to convert it to a debian file.  After it installed I ran the config script, and it is asking for the location of the C header files that match my running kernel  I'm running Ubuntu 6.06 i386 after a fresh install off of the cd.  I really need to get VMware running soon.  Can anyone help? Thanks

---

### Post by in_flu_ence on 2007-03-11
I use vmware server (Free) with the tar.gz files.

the instruction is very simple but i think you need the linux-headers files installed. Sorry. I am still a sub-newbie so i can't remember all the file name.

and once u have done that, you should have some files installed under /usr/src.

Re-run the installation script. for my case i did a sudo ./vmware-install.pl

and things will work. at the point where it ask for the location, there should be a default [/usr/... ] and you are at the right track.

Just use the default setting.

Apology if I miss any point but that's the general direction. I think you will get some useful how-to by searching vmware server.

---

### Post by Keymaster on 2007-03-12
The default location doesn't work.  I'd use VMWare on my Windows side, but it's Vista, and consumes enough RAM on its own. lol  I'll research vmware server, and see what happens.  Any other advice is of course more than welcome.

---

### Post by in_flu_ence on 2007-03-12
Vista is, my opinion, a waste of resources. To me, it is like building a supercomputer to make my screensaver look nicer.

Having vmware server is very easy in ubuntu (esp in 32bit). I have that in 64bit as well. Run very smoothly and stable. I basically can do some simple CFD in my vmware.

Alternatively, you can try virtualbox. I think it is also very popular in this forum. I like it in my first impression because it has a .deb package but it seems not able to support widescreen. so i end up with distorted screen for my virtual platform.

Not very sure if vista can support vmware as yet. basically, vista doesn't support everything to me from hardware to software.

---

### Post by Keymaster on 2007-03-12
Vista is a waste of resources, but I need to learn it for my job.  Also my machine is widescreen, so we'll see how everything works out if VMWare doesn't work.  I also hear the latest version of VMWare Workstation works in Vista.

---

### Post by Keymaster on 2007-03-13
Virtualbox installed, but now none of my package managers work (synaptic, dpkg, apt-get, auto update, etc...)  I really don't want to reinstall linux again.  Any idea how to fix it  Nothing shows up in synaptic, and when I first load it it says that virtualbox needs to be reinstalled but it can't find the archive.

Edit Update: nevermind.  I fixed that problem by using "sudo apt-get remove virtualbox"

---

### Post by in_flu_ence on 2007-03-13
did you use the .deb package provided and matching your version?

I tried virtualbox in desktops and laptops and seems ok. my problem with virtualbox goes to the screen

My advice still try to install vmware. I think they are the top players for some reason. they are more stable in my case.

---


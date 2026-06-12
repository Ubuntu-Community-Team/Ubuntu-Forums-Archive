---
title: "Couple of questions..."
date: 2005-04-09
forum: Desktop Environments
---

### Post by SquireSCA on 2005-04-09
OK, I installed ubuntu alongside WinXP Pro this time, so that should I bork Linux, I have something to fall back on.

I installed ubuntu 5.04 official onto a 40GB partition on my 89GB SATA boot drive.  I immediately patched the kernel to i686 SMP(latest) and rebooted into it.  I then mounted my 250GB NTFS SATA storage drive by editing the fstab file, and mounted it as /media/storage.  

Question #1 is, how do I get that mount point to show up in Gnome's "My Computer"?  I can navigate to the drive with the file manager, but I cannot add an incon to that folder like the DVD, floppy and USB drives have.

Next, I installed the NVidia drivers through Apt-get, using the instructions on the unofficial ubuntu guide.  WHen I run glxgears, here is the output:

dave@ubuntu:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
glxgears: Error: couldn't get an RGB, Double-buffered visual.
dave@ubuntu:~$

I cannot figure it out.  Everything looks set up properly, I edited that /etc/X11/xorg.conf file, and changed the driver from "nv" to "nvidia", and same result.  I restarted X, and I even rebooted the machine, but I cannot get that driver to take.

My last problem, is getting my DVD drives to use DMA.  I cannot seem to figure it out and I have spent a couple hours poking around.

Three main problems, probably pretty easy to a Linux veteran, but I cannot seem to get it worked out.  If I can get those three things, I think that the rest would be smooth sailing.  I decided against Suse 9.3 and I am determined to make this work if it kills me.

---

### Post by SquireSCA on 2005-04-09
I tried enabling DMA on my drives, and here was the output:

dave@ubuntu:~$ sudo hdparm -d1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
dave@ubuntu:~$ sudo hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
dave@ubuntu:~$

---

### Post by claudius on 2005-04-09
I have exactly the same problems like you with the nvidia-drivers. I tried really a lot, but I couldn't fix the problem and no one was able to help :-(((
... if you find a solution though, please post it! 
thanx a lot and good luck!

---

### Post by SquireSCA on 2005-04-09
If I figure it out, I will post it.  So far, my only fix is to boot into WinXP or Suse...  LOL

I am installing Kubuntu to see how it mounts the drices through KDE, and perhaps KDE has some config utils to make some of this stuff easier...  I don't know why they have to make it so hard to do simple mundane things...

---

### Post by jtmo3 on 2005-04-09
I had the same problem with getting dma enabled on my dvd drive. I ended up putting this...

piix
ide-core

and putting it ABOVE

ide-cd
ide-disk
ide-generic


in my /etc/modules file. 

Then adding this to the end of my /etc/hdparm.conf file...

/dev/hda {
write_cache = on
dma = on
transfer_mode = 68
interrupt_unmask = on
io32_support = 3
}

Then in /etc/rcS.d -- I did cp S07hdparm S29hdparm.

After all this, it finally is working. Your situation might be different. Good luck.

---

### Post by SquireSCA on 2005-04-09
[QUOTE=jtmo3]I had the same problem with getting dma enabled on my dvd drive. I ended up putting this...

piix
ide-core

and putting it ABOVE

ide-cd
ide-disk
ide-generic


in my /etc/modules file. 

Then adding this to the end of my /etc/hdparm.conf file...

/dev/hda {
write_cache = on
dma = on
transfer_mode = 68
interrupt_unmask = on
io32_support = 3
}

Then in /etc/rcS.d -- I did cp S07hdparm S29hdparm.

After all this, it finally is working. Your situation might be different. Good luck.[/QUOTE]

I cannot believe that in 2005, one has to go to such lengths to enable an almost universally required setting in a "cutting edge" OS...  This is the kind of crap that holds Linux back from gaining popularity in the mainstream market.  

To the average user, all the security and open-source software in the world is useless if you can't get the OS to do the basics...  hehe

---

### Post by taygan on 2005-04-09
does "sudo nvidia-glx-config enable" help?

---

### Post by SquireSCA on 2005-04-10
[QUOTE=taygan]does "sudo nvidia-glx-config enable" help?[/QUOTE]

Nope.  When I launch the nvidia-settings app it says it cannot locate the nvidia-cp or something.  The little NVidia utility pops up, but it is blank.

---


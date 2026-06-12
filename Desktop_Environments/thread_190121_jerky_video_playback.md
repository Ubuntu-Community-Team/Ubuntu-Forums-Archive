---
title: "jerky video playback"
date: 2006-06-05
forum: Desktop Environments
---

### Post by wswswsws on 2006-06-05
hey people, how it going, hope you can help. 

So iv got my ubuntu nearly perfect. can access my NTFS drives, MSN, Torrent, java etc..

But playing my movie files, especially when your watching in a bigger window, their very jerky. Any ideas how i can fix this? (XviD, RMVB etc..)

I used to Automatix to install all my codecs.

treid VLC, movie player and mplayer

iv got an S754 Athlon64 CPU so that aint the problem.

ps. before i used Automatix, i used EasyUbuntu, but i couldnt even play video files after using it. 

Hope we can get this fixed, and i can pretty much dump windoze forever:P 

(well all i need is an avi to dvd converter to replace convertXtoDVD)

---

### Post by Rule on 2006-06-05
enable DMA

hdparm -d 1 -A 1 -m 16 -u 1 -a 64 /dev/hda

and you can add it to your /etc/hdparm.conf so it's turned on when you start your computer.

---

### Post by titus1950 on 2006-06-05
[QUOTE=wswswsws]hey people, how it going, hope you can help. 

So iv got my ubuntu nearly perfect. can access my NTFS drives, MSN, Torrent, java etc..

But playing my movie files, especially when your watching in a bigger window, their very jerky. Any ideas how i can fix this? (XviD, RMVB etc..)

I used to Automatix to install all my codecs.

treid VLC, movie player and mplayer

iv got an S754 Athlon64 CPU so that aint the problem.

ps. before i used Automatix, i used EasyUbuntu, but i couldnt even play video files after using it. 

Hope we can get this fixed, and i can pretty much dump windoze forever:P 

(well all i need is an avi to dvd converter to replace convertXtoDVD)[/QUOTE]


Read this: 

[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---

### Post by wswswsws on 2006-06-05
sorry, forgot to mention my dma is already enabled. (it was by default)

edit:

**************************************************
**************************************************

john@john-desktop:~$ sudo hdparm /dev/hdc
Password:

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
john@john-desktop:~$ sudo gedit /etc/hdparm.conf

*************************************************
*************************************************

and i added the bit to the bottom of my   /etc/hdparm.conf}



#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}
/dev/cdrom {
    dma = on
}

/dev/hdc {
   dma = on
   }

---

### Post by wswswsws on 2006-06-06
more info: I have not installed the ATI drivers ( AGP 9600XT ) When i installed the ATI drivers from "easy Ubunyu" i couldnt access the graphical login screen, so had to reinstall ununtu

---

### Post by wswswsws on 2006-06-07
MORE INFO. 
when i lower my screen resolution to 800 by 600 it gets less jerky, but its still definatly there.

---

### Post by volfro on 2006-06-10
I'm having the exact same issue.  DMA is enabled on all my discs (removable and otherwise) and the system is plenty fast enough to keep up with DVD-resolution playback.  

Perhaps the only solution is to wait for a nice update...

---

### Post by wswswsws on 2006-06-10
ah, its nice to hear im not the only one:)

---

### Post by mgmiller on 2006-06-10
It sounds like you don't have the accelerated drivers installed for your ati video card.  This can make a huge difference in video performance.  Unfortunately, ATI cards can be a bit harder to get going in acclerated mode than nvidia based cards, but it can be done.  I suggest you search the wiki on installing ati accelerated drivers.

---

### Post by dolphinholmer on 2006-06-18
Have you installed Compiz or Xgl? I had exactly the same problem and after uninstalling these and reverting to backups of xorg.conf and gdm.conf-custom playback was fine.

---

### Post by dasratsel on 2006-06-18
i was having the same problem, so i went into xorg.conf and found my comp was using the vesa driver, so i did "sudo dpkg-reconfigure xserver-xorg" and manualy selected a savage driver and DVD playback is now perfect... even if you dont configure the special ATI drivers, selecting a generic ATI driver will drasticly help performance if ur using a vesa driver 'r something like that... hope this helps

~Xavier

---

### Post by jimisdead on 2006-06-29
I'm having the same problem after a recent update - it's not a hardware issue (1.8Ghz Pentium M & GeForce 6800) - I do have Compiz and XGL installed though (but not being currently used), so I will uninstall and try again.

---

### Post by Avionix on 2006-09-05
I also had Jerky video playback on all my video players, VLC and Totem etc, this was since my upgrade to Dapper - the fix, "sudo dpkg-reconfigure xserver-xorg" and choosing another driver instead of vesa, in my case sis.
Now all is good. Still have to figure out how to configure firestarter properly, some day perhaps.

---

### Post by daemonoid on 2006-09-05
I suffered the same problems.

The latest ati drivers have a few issues but on the whole are reasonably easy to install...

Take a look at this thread (which no one really answered):

[http://ubuntuforums.org/showthread.php?t=249436](http://ubuntuforums.org/showthread.php?t=249436)

It's got links to the driver install as well as my solution to the dodgy XV problems.

Doing this sped things up no end! especially 3d.

---


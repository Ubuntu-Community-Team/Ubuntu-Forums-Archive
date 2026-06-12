---
title: "Can't Open Anything Under Places Menu"
date: 2010-10-15
forum: Desktop Environments
---

### Post by steven.smith on 2010-10-15
Hey there people!
   I have a VPS with Ubuntu 9.04 and have been messing around with Ubuntu Desktop. This problem has been going on for awhile now, but only recently did I care enough to actually dig deeper into it.
   
   
   The thing is, I can't access any of the folders under "Places" and various other settings on the desktop. What happens is everytime I click on it, a bar opens on the taskbar saying "Opening [example]" and then it disappears and the program/folder doesn't open up. For example, when I click on Places--->Music, a "Opening Music" bar appears for about 10 seconds and then simply disappears. Nothing opens up, no error messages. I've looked around and haven't been able to find a suitable answer, which is why I'm asking it here.
   
      
      
I automatically assumed the problem was Nautilus, so when I ran the command it came up with this error:
      > 
      Xlib: extension "RANDR" missing on display ":1.0".*
      Xlib: extension "Generic Event Extension" missing on display ":1.0". 
      Xlib: extension "Generic Event Extension" missing on display ":1.0". 
      Xlib: extension "Generic Event Extension" missing on display ":1.0". 
      
      (nautilus:3700): GVFS-RemoteVolumeMonitor-WARNING **: remote volume 
      monitor with dbus name org.gtk.Private.HalVolumeMonitor is not supported 
      
      (nautilus:3700): GVFS-RemoteVolumeMonitor-WARNING **: remote volume 
      monitor with dbus name org.gtk.Private.GPhoto2VolumeMonitor is not supported 
      
      ** (nautilus:3700): WARNING **: Failed to initialize hal : (null) 
      
      process 3700: Attempt to remove filter function 0x7f251f9d1df0 user data 
      0xa9e840, but no such filter has been added 
      libhal.c 3126 : LibHalContext *ctx is NULL 
      Segmentation fault
   *   *
   
   
   The same error happens when I try to open a folder with Gnome. I tried reinstalling hal but that didn't make a difference either.
   

   So does anybody know the problem and how to solve it? I wouldn't have posted this if I hadn't already tried everything else I could think of. I really appreciate anyone that can help me with this.
   
      
      
   *   Thanks in advance for all your help

---

### Post by henpecked412 on 2010-12-03
> **steven.smith said:**
> Hey there people!
   I have a VPS with Ubuntu 9.04 and have been messing around with Ubuntu Desktop. This problem has been going on for awhile now, but only recently did I care enough to actually dig deeper into it.
   
   
   The thing is, I can't access any of the folders under "Places" and various other settings on the desktop. What happens is everytime I click on it, a bar opens on the taskbar saying "Opening [example]" and then it disappears and the program/folder doesn't open up. For example, when I click on Places--->Music, a "Opening Music" bar appears for about 10 seconds and then simply disappears. Nothing opens up, no error messages. I've looked around and haven't been able to find a suitable answer, which is why I'm asking it here.
   
      
      
I automatically assumed the problem was Nautilus, so when I ran the command it came up with this error:
      *
   
   
   The same error happens when I try to open a folder with Gnome. I tried reinstalling hal but that didn't make a difference either.
   

   So does anybody know the problem and how to solve it? I wouldn't have posted this if I hadn't already tried everything else I could think of. I really appreciate anyone that can help me with this.
   
      
      
   *   Thanks in advance for all your help

iv got same problem

---


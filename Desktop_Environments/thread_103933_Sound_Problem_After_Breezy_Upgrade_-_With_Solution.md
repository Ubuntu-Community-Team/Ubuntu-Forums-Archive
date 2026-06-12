---
title: "Sound Problem After Breezy Upgrade - With Solution (aka Missing group memberships)"
date: 2005-12-15
forum: Desktop Environments
---

### Post by LanceRushing on 2005-12-15
Thought I would share my solution for the fixing my sound problem.

**Short answer:**

```
$ sudo usermod -G audio [username]
```
Logout and log back in.

**Long Answer:**

Upgraded from 5.04.  First time I logged in I got the familiar ubuntu drum roll.  But once logged in no sound.  

After getting the dreaded: 
**Failed to construct test pipeline for 'ESD - Enlightenment Sound Daemon'**

And System->Preferences->Sound had nothing under "Default sound card".  At first I thought maybe hardware, but that didn't make sense because GDM did make the drum roll. 

I started poking around the forums and never round a solution, so I took a break.  When I came back I opened up a terminal and noticed 
```
$ esd
sox: Can't open output file '/dev/dsp': Permission denied
```

Hmm.. ```
 $ ls -l /dev/dsp
crw-rw----  1 root audio 14, 3 2005-12-14 22:06 /dev/dsp

```
/dev/dsp is only writable by root and the audio group..

```
 $ groups 
username 

```

Eureka!!!

```
$ sudo usermod -G audio [username]
```

Logout and log back in, and let there be sound!

P.S. Shouldn't these groups been set also? tape, floppy, cdrom, fax, voice, video, etc....  (any one wish to share their results of **$ groups** ?)


-Lance

---


---
title: "WINE problem.."
date: 2006-03-19
forum: Desktop Environments
---

### Post by LordMelkor on 2006-03-19
When I open winecfg and click the audio tab... it quits... here is the message i get...

Creating link /home/krishanu/.kde/socket-ubuntu.
can't create mcop directory

.... very weird esp because im on ubuntu not kubuntu.. whats it trying to do with kde? How can I fix this?

---

### Post by Zeroangel on 2006-03-19
Try creating it yourself.

Certain apps are designed for KDE so they require KDE runtimes, libraries, and configs. The ARTS sound server is native to KDE and probably the very reason why this is happening.

---

### Post by LordMelkor on 2006-03-19
thx that worked.

---

### Post by Shampyon on 2006-03-21
I've run into a similar problem. I run winecfg from terminal, and everything's fine until I click the Audio tab. Then I get this message:

[B][myusername]@ubuntu:~$ winecfg
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/user/.kde/socket-ubuntu.
can't create mcop directory[/B]

Kind of ironic. I only just fixed up my sound problems in the rest of Ubuntu, and now wine wants to have a go ;) 

I'm guessing I'm missing an ALSA dependancy? Or is it something to do with the fact that I'm using the dreaded Soundblaster Audigy Value (which reads in lspci as "Creative Labs SB Audigy LS")?

EDIT:
I've followed some instructions in other threads, and I think I've succeeded in creating the needed link. Now I'm getting this lovely error:
[B]
[myusername]@ubuntu:~$ winecfg
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack[/B]

I'll see if I can fix this up, and edit my success/failure in here.

EDIT2: Did some checking. Looks like I have nothing to worry about, since I use ALSA for my sound. I've posted a summarry opf what I did to get WINE up and running in this thread:
**[http://www.ubuntuforums.org/showthread.php?p=846165#post846165](http://www.ubuntuforums.org/showthread.php?p=846165#post846165)**
in this specific post:
**[http://www.ubuntuforums.org/showpost.php?p=846165&postcount=7](http://www.ubuntuforums.org/showpost.php?p=846165&postcount=7)**

---


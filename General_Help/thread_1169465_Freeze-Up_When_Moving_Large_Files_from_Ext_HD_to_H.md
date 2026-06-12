---
title: "Freeze-Up When Moving Large Files from Ext HD to HDD"
date: 2009-05-25
forum: General Help
---

### Post by tacantara on 2009-05-25
I was attempting to copy a large (nearly 5GB of videos and text files) file off my external HD to the home directory on my HDD.  Shortly into the process, the copy process stopped.  I waited 10 minutes to see if it was just "thinking" but there was no further advance on the process.  I run the system monitor on the taskbar, and it doesn't appear to be overworking the CPU (in fact, there was very little CPU usage).  My disk is set up with the ext4 file system.  Has anyone else encountered problems like this, and is it something that can be fixed?

The external HD has an NTFS file system (I used this drive previously when I was operating Windows, so it took on NTFS by default).  Could that be part of the problem?

---

### Post by tacantara on 2009-05-26
Bump!

---

### Post by kmitnick on 2009-05-26
what is the output of top command during the copying process???

---

### Post by tacantara on 2009-05-26
I'm not moving files using the terminal.  I drop-and-drag using the Nautilus file system.  I'm guessing that you're recommending moving files through the terminal instead?

---

### Post by tacantara on 2009-05-27
I attempted to move the large files thorugh the terminal. Same result - the external HD indicator light stops blinking (no activity), as does the activity light on my computer HDD. I had to stop all processes and restart my computer to bring everything back to "normal." Even then, I couldn't get the computer to reboot. It got to the shutdown page, and left me with a blinking cursor. I had to manually power down from there. Is it just me, or the fact that I'm trying to move several GB worth of stuff in one move, or is there something more that I'm missing?
 
** Additional Info ** The hang-up during shutdown wasn't relieved by manual power down.  I disconnected the external HD from the USB port, and the computer resumed the shutdown/restart process.

---

### Post by kmitnick on 2009-05-27
can you post the content of ```
/etc/fstab
```
and the output of ```
ls /dev | grep sd
```

---


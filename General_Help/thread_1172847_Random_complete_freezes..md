---
title: "Random complete freezes."
date: 2009-05-29
forum: General Help
---

### Post by YenTheFirst on 2009-05-29
Hello, I've got a problem, and I'm not sure where to even start with it.

I'm running Kubuntu 8.04 on a Lenovo Thinkpad x60 tablet. For the most part, it works really well, and I enjoy using it. However, from time to time (sometimes weeks apart), the system will completely lock up.

When it locks up, it locks up completely. No mouse input, no keyboard input (ctrl-alt-f1 does nothing, nor does ctrl-alt-backspace), the clock is frozen at whatever time it froze, and the screen doesn't update. The only way out is a hard reboot.

The crashes happen pretty far apart, and nothing in particular seems to predict them. After rebooting, dmesg and syslog don't seem to say anything useful.

I'm aware all sorts of different things might be causing this problem, but I have no idea where to start troubleshooting/debugging this. Any ideas?

---

### Post by Favux on 2009-05-29
Hi YenTheFirst,

You aren't alone.  Here's a related thread with a link to yet another.  [http://ubuntuforums.org/showthread.php?t=1167523](http://ubuntuforums.org/showthread.php?t=1167523)

I hope this helps.

---

### Post by YenTheFirst on 2009-05-29
Hi Favux, thanks for the reply. Both threads deal with 9.04, but maybe the problem is the same. Neither thread comes to a solution though, either. This seems to be a quite bothersome thing.

---

### Post by Favux on 2009-05-29
Hi YenTheFirst,

My fault, i misread 8.04 for 9.04.  I thought I was putting you in touch with folks with the same/similar problems.  I apologize.

---

### Post by wpshooter on 2009-05-29
Have you ran memtest ?

---

### Post by YenTheFirst on 2009-05-30
Favux, thanks for your reply, and no problem at all. 

wpshooter: I ran memtest, it ran and passed, with no errors, 5 times. One thing, though - It was using the memory range 'BIOS-std'. If I used 'BIOS-all', it would display 1000+ errors, and freeze up.

I don't know much about memtest, so I don't know if this is something noteworthy, or something to be expected. I have 2GB of RAM in the system, and memtest said it was testing from 120k-2038M

---


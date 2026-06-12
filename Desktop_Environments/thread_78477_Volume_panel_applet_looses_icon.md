---
title: "Volume panel applet looses icon"
date: 2005-10-18
forum: Desktop Environments
---

### Post by Qrk on 2005-10-18
The volume panel applet on the gnome-panel randomly disappears from the panel. The applet is still running... in fact, if you click the panel in just the right place (its only a few pixels wide) the applet works. But the icon randomly appears and dissapears. I was going to file a bug report, but I thought I'd check to see if anyone had a similar problem and if there was an easy fix.

---

### Post by jamesford on 2005-10-18
i had that some days ago but remocing the applet and adding a new one a few times and a few reboots inbetween sovled it. its been working for  days now

---

### Post by bonifacio on 2005-11-18
i just noticed this problem today.  if anybody had a solution, please let us know.

i definitely think that this is a bug.  i tried killing the process of mixer_applet2, and a dialog ask me to reload or don't.  tried both cases none seems to work.  a couple of restart and logoff don't do it either.

oh and another thing, it may be related, but it has a strange effect on totem.  the speaker icon on the left of the sidebar is gone too.  you know its there because the placeholder still works its just the icon thats gone.

---

### Post by KevB on 2005-11-19
Had this same problem, and found the solution in this post:

[http://ubuntuforums.org/showthread.php?t=79725&highlight=volume+icon](http://ubuntuforums.org/showthread.php?t=79725&highlight=volume+icon)

Turns out it was the Icon theme I had selected.. there is a work around to get the volume icon showing the the theme you like.

Take Care,
Kev

---

### Post by bonifacio on 2005-11-20
KevB,

Wow, thanks for bringing this up.  Indeed it was the icon theme I had chosen (Iris BTW).  Sure enough choosing a different one resolved this problem.

---


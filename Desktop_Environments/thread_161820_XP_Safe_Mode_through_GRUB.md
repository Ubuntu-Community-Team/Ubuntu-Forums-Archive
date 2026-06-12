---
title: "XP Safe Mode through GRUB?"
date: 2006-04-17
forum: Desktop Environments
---

### Post by BoboChimp on 2006-04-17
This all seems very ironic to me...
I've got a 3 year old laptop with a 40 gig drive.  i decided to give my Ubuntu partition more space at the expense of the XP partition (Hooray right?).  I backed up the things i didn't want to lose and went to partitioning and reinstalling both OSes.  I did XP while d/c from the net.  It's scary how quickly pop ups start happening otherwise.  After that, I got Ubuntu up and running.  Today i went back to XP install my AV/Firewall that i paid for last November.  I decided in the interest of security i would throw up a small firewall (Tiny Personal Firewall) before connecting the the net to re-download PC-Cillin.  I installed PC-Cillin and attempted to uninstall Tiny just before i rebooted (PC-Cillin requires a reboot after installation).  The machine locked up during the uninstall of Tiny.  Now it crashes every time i try to boot into XP.  I'm pretty sure i could fix it if i could get into safe mode.  

So finally, here's the question...

Does anyone know how to get into XP Safe Mode from GRUB?  Or is there a way to do it from the XP install disk?

---

### Post by jazzmuzik on 2006-04-17
If  recall correctly, immediately after you select Windows from the Grub menu, press the F8 key. Er, I'm pretty sure it's F8 anyway. That should give you a menu of Windows options and you should be able to get into Safe Mode.

---

### Post by BoboChimp on 2006-04-17
maybe i didn't catch it fast enough.  I know it's F8 for sure on a regular boot.  I was thinking maybe GRUB somehow put me into the process further along so that i couldn't use that key b/c i did try.

i'll try again (quicker) and re-post.

---

### Post by Super King on 2006-04-17
As a last resort you can power down your laptop after Windows starts to boot. The next time you choose Windows from GRUB you'll get the "you did not shut down correctly" message along with all the Safe Mode/Last Good config choices.

---

### Post by BoboChimp on 2006-04-17
for anyone interested, you have to push F8 REALLY fast.  i guess now the problem is back on me.

---

### Post by jazzmuzik on 2006-04-17
[QUOTE=BoboChimp]for anyone interested, you have to push F8 REALLY fast.  i guess now the problem is back on me.[/QUOTE]

What I do is press F8 repeatedly (but don't hold it down). That always works for me. But not too fast that you overload the keyboard buffer.

---


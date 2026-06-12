---
title: "boot up issues with grub"
date: 2009-05-20
forum: General Help
---

### Post by 5mattyb5 on 2009-05-20
Hi all I have a silly little problem.  When i boot up the system sees grub then shows a boot spalsh then nothing...I mean nothing just a black screen mouse and keyboard rendered useless.  If i press esc at grub to see the menu and select the only kernel in the list it boots up fine.  That is the first entry in the list so obviously /boot/grub/menu.lst is set "default 0".  Startup-manager also shows the correct entry but for shits and giggles after a successful boot I chose the "last used" option, of course that didn't work.  Has anybody ever seen such a silly problem before, and maybe even have a solution.

---

### Post by KhurramM on 2009-05-20
Either u are having a display error, if so,

then boot into recovery mode, on the grub and repair X, hope this helps.

Else there may be a hardware issue. Better get some one experinced handle this.

DO backup your precious data.

---

### Post by 5mattyb5 on 2009-05-21
Thanks for the suggestion but no luck.  I should add that this same operating system is running fine on another machine I got installed off the same disc.  Maybe hardware but I really don't think so because it worked until I upgraded to jaunty.

---

### Post by dandnsmith on 2009-05-21
If there is only one entry in the grub boot list, then it sounds like a timing issue - don't know what yet.

You could, possibly, eke out a little more info by changing the entry to remove the 'quiet' and 'splash' bits. You'll then get a lot displayed, and *either* it won't glitch anymore *or* you'll find out what stage in the boot process/initialisation it gets to.

---

### Post by 5mattyb5 on 2009-05-21
Well I don't know what did it for sure but it's working again.  I tried what dandnsmith had suggested however right before that I also reinstalled grub....why not right?  any way thanx everyone for all your help it really is appreciated, I always say many heads are better than one.

---


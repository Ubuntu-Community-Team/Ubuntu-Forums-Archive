---
title: "Problems getting applications to start in Hardy"
date: 2009-01-11
forum: General Help
---

### Post by FamousAmos on 2009-01-11
I don't know if this is the right forum for this, but if it is I hope someone will move it to the correct place.  I upgraded to Hardy Heron 8.04 several months ago, and since that time I have had intermittent issues with certain applications randomly refusing to start.  Specifically Firefox, Nautilus File Browser and Totem Music Player.  Pidgin Instant Messenger seems to be unaffected and will continue to work after these other applications have died.  What happens is that when you go to start any of the above applications, they act like they're trying to start up, then they crash.  Also, trying to reboot through the Red On/Off button in the upper right corner does not do anything.  The only thing I've been able to do when this happens is to reboot the machine.  

Has anyone else experienced this, and if so can you tell me what the solution/work around for this problem is?  Thanks.    

Also, I'm running 2.6.24-22-generic

---

### Post by gettinoriginal on 2009-01-12
I have had that problem in the past after "playing" with my system :roll:, and this fixed it for me:
Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

---

### Post by FamousAmos on 2009-01-13
Hi, thanks for your reply!  I tried your suggestion, and so far so good.  It's only been a day, so it may still recur, but so far it looks positive.

---

### Post by FamousAmos on 2009-03-09
Update:  I tried your suggestion, and it appeared to work for a while, but lately it has been recurring again.  To recap - after running for a while, not doing any specific activities(as far as I can tell), Firefox will refuse to start(it doesn't die if it's running, it just won't start up again once you close it), the file browser won't open, terminals won't open(they open the window but it's just blank and unresponsive).  Pidgin seems unaffected by all this for some reason.  I'd love to be able to get some idea of the state of the system when this happens, but without a terminal or a file browser I know of no way to do that.  Does anyone have any ideas?  Thanks in advance.

---

### Post by FamousAmos on 2009-03-11
Does anyone have any thoughts?  

Thanks

---


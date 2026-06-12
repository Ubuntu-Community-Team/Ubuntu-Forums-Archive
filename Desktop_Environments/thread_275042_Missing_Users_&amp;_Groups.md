---
title: "Missing Users &amp; Groups"
date: 2006-10-10
forum: Desktop Environments
---

### Post by bcollignon on 2006-10-10
Is there any way to reconfigure missing desktop menues (Administration for one) when recovering from losing SUDO priveleges.  I have SUDO back and operational (via GRUB and booting into recovery mode), but the groups to which I belonged are unknown.  How do I get them, and the corresponding menus missing in Gnome back?  I'm a relative noob, so thanks for the guidance of any gurus.

---

### Post by bcollignon on 2006-10-11
Replying to yourself can be gratifying.  I found the answer to this problem with some help from a collegue at work.  Neither of us is really beyond the newbie stage of Ubuntu, but he is more proficient at Linux in general than I.  So, for those of you interested...

Typing usermod -G has the disastrous effect of eliminating you from the groups you're in; which is of some use to Ubuntu and Gnome, apparently.  It can also add you to groups, but you have to know, in the first place, which groups you need to be in.  Good Luck finding the groups, other than by typing "Groups" under someone else's login.  Than, at least, you have a starting point.  For more information regarding usermod, type man usermod at the console.  

I was able to restore the groups I was in previously by, as I said, attaining root status after pressing ESC at GRUB during bootup.  Recovery mode allows this.  Then, using visudo, I was able to place my name in the administrator role at the end of the file.  Alas, SUDO was restored when I logged in under Gnome.  However, my menus were abbreviated and I had to manually assign myself to the admin group with the command adduser MYNAME admin.  Typing Groups at this point will not show me as a member of admin until next login.  Then I was able, under Gnome, to look in System > Administration > Users & Groups to find the groups available.  Then, one by one, I assigned them with the command above.  Lengthy, but no re-install necessary like under Windows, perhaps.

---


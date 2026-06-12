---
title: "Fast User Switcher doesn't show restart or shutdown options"
date: 2009-04-16
forum: General Help
---

### Post by amrbekhit on 2009-04-16
Hello all,

My fast user switcher applet does not show the restart or shutdown options, only the Guest session, lock screen and log out ones. 

What's interesting is that if I use the shutdown command in the gnome-do (the terminal shutdown command shuts down instantly), the fast user switcher applet reverts to normal and the other options reappear. I then need to use the shutdown command again to actually shutdown/restart the system. 

I initially thought this had something to do with either gnome-do or pidgin but I disabled them both and the problem persisted.

It's almost like there's one system running on top of the other - the first shutdown closes the first system and then the second shutdown closes the computer. I'm wondering if the gnome-do shutdown command is different from the terminal one as the terminal one requires sudo, but gnome-do doesn't ask me for a password, and checking the output of top shows that gnome-do is owned by the user, and not root.

Any ideas?

--Amr

---

### Post by BazookaAce on 2009-04-16
Try to go to: 

System-->Administration-->Login Window-->Local-->Show Actions menu.

I solved my problem "back in the days".

---

### Post by amrbekhit on 2009-04-16
Hi Bazooka,

Thanks for your reply. I checked that option and it was already enabled. Turning it off and restarting did not solve the problem, unfortunately.

--Amr

---

### Post by BazookaAce on 2009-04-16
Hmm, okay. Then i'm afraid i don't know what's causing your problem. But just wait a litle bit. I'm sure someone with more Ubuntu-knowledge will help you out :)

- BA

---

### Post by amrbekhit on 2009-04-17
No problem, thanks for your time. I shall try and be patient!

---


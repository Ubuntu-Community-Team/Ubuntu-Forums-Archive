---
title: "Customizing the guest session"
date: 2009-10-29
forum: Desktop Environments
---

### Post by humphreybc on 2009-10-29
Hi guys,

I posted this elsewhere but received no replies. I was wondering whether it's possible to customize the guest session, ie, different theme, panel layout, fonts, background etc etc and actually have the session save it permanently.

The reason I ask is that, in my opinion, the default karmic theme is ugly compared to what can be achieved with a different theme and font settings... and when guests use my computer, I want to show off how beautiful Ubuntu is to them.

Thanks

---

### Post by mcduck on 2009-10-29
Any files located inside /etc/skel will be copied to newly created user's home directories (including the guest session!). Since all user settings are just hidden files in home directory, all you have to do is copy the setting files you want into /etc/skel.

What I usually do is that I create a fresh new user, customize the desktop & application settings the way I want them to be for all new users (and guest), and then copy everything from that user's home to /etc/skel. Then I remove that user since I won't need it any more.

Another way would be using Sabayon, which is a graphical tool for adjusting Gnome settings for different users & groups.

---

### Post by humphreybc on 2009-10-29
I've created a new user called, "newuser" - once I have customized the user, how do I gain access to "newuser" 's home directory from MY sesson?

EDIT: Don't worry, worked it out. Thanks, worked like a charm!

---


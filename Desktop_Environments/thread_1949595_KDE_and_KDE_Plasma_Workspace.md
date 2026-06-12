---
title: "KDE and KDE Plasma Workspace"
date: 2012-03-30
forum: Desktop Environments
---

### Post by amira-uk on 2012-03-30
Sorry if this is a really stupid question but I can't figure it out.

I have Kubuntu 11.10 on both my desktop PC and my netbook. On my PC the version of KDE looks like Windows with the start bar at the bottom but on my netbook I have the plasma workspace with icons everywhere and it doesn't look very good.

Is there a way of choosing how KDE works or has it done this automatically due to my hardware or something?

Thanks.

---

### Post by SeijiSensei on 2012-03-30
Create a new user account for yourself on the netbook and log into that.  You'll get the default desktop.  Is that what you want it to look like?  If so, in your normal account, run

```

cd ~
mv .kde .kde.old

```

then log out and log back in.  You can do the same thing in Dolphin by first enabling "show hidden files" by holding down Alt and hitting the period.  Then highlight the .kde directory and rename it .kde.old.

---

### Post by amira-uk on 2012-03-30
Thanks for that but it didn't work. I got the same desktop when i made another user. I think I shall give XFCE another try, or try Gnome because since upgrading from 11.04 to 11.10 KDE has been slow and buggy on here, lovely on my PC though.

---


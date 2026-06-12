---
title: "Top Panel Disappear after Ubuntu 10.04 Intall"
date: 2011-04-01
forum: Desktop Environments
---

### Post by webusr1 on 2011-04-01
All,
I installed Ubuntu 10.04 on a Compaq Desktop and the initial install worked great. It found all hardware devices and audio, video, network, CD/DVD and all these devices work great. I created all user accounts, but the next day when I powered up the Compaq I lost the GNOME  Top Panel for all users. So, Ubuntu 10.04 no longer provides the Applications, Places, and System drop downs. It doesn't provide the right side items of the Top Panel where the notification and logout, powerdown drop downs reside.

Any help would be greatly appreciated.

Thanks!

---

### Post by Rubi1200 on 2011-04-01
Since this is a fresh install I assume you have not made too many customizations, especially to the panel correct?

Try this when you next get to the desktop:

Ctrl + Alt + T to open a terminal

and then these commands to reset the panels to default:

```
gconftool-2 --shutdown 
rm -rf ~/.gconf/apps/panel 
pkill gnome-panel
```That should do it. Just be aware that any custom panel settings will be lost.
You might also have to log out and in again.

---

### Post by webusr1 on 2011-04-01
Correct. There has been no customization because it's a fresh install (the old hard drive failed hard and since I spared it out, I did the fresh install). A few more questions...

I see that "sudo" is not required. Will every user have to run these commands? If every user has to do this, then is there a way to correct the config across all users users using sudo???

I created ten users... It would be nice for root to fix it across the board.

Thanks!

---

### Post by operatorace on 2011-04-01
Definitely do sudo then.

---

### Post by Rubi1200 on 2011-04-01
> **webusr1 said:**
> Correct. There has been no customization because it's a fresh install (the old hard drive failed hard and since I spared it out, I did the fresh install). A few more questions...

I see that "sudo" is not required. Will every user have to run these commands? If every user has to do this, then is there a way to correct the config across all users users using sudo???

I created ten users... It would be nice for root to fix it across the board.

Thanks!
Ten users including your account or ten total?

If you are the only one with administrative privileges it should work for all accounts/users.

Not sure if you need to do this as root though and I would first try it the regular way before invoking root privileges.

---

### Post by webusr1 on 2011-04-01
I have two accounts with Admin privileges, and the total is ten. Everyone in the family uses the PC, including visiting relatives. This exposes those windows users to a really superior Linux Desktop Operating System with the hassle free bonus of NO VIRUS's on our home PC.  ;-D

I'll try it without sudo first and post back my results. It just seems that "~/"  is only removing the panel file (.gconf/apps/panel) for the user that is logged in. I would assume that all users have this same file their home directory.

---

### Post by Rubi1200 on 2011-04-01
You are right about the second command; it is only for the user currently logged in.

Therefore, using sudo is unlikely to make any difference.

I did a quick Google search on how to do this for multiple users, but nothing turned up immediately.

Unless someone else has a better suggestion, you may have to log in and do this on each account.

---

### Post by Krytarik on 2011-04-01
If the same issue exists with *all* user accounts, it's unlikely that the cause is a misconfiguration of *each* user's panels.
Does the bottom panel still come up?

Try just restarting gnome-panel:
- press Ctrl+Alt+T
- enter:```

killall gnome-panel
```

---

### Post by webusr1 on 2011-04-01
Every account lost the Top Panel. This is a weird problem. Hope these GDM problems get resolved soon. I had another different GDM problem on Dell PC....

I'll try out these suggestions tonight and let you guys know what I found.

Thanks all!

---

### Post by webusr1 on 2011-04-01
You guys are gonna laugh when you find out what the solution was... My Dad put a new Samsung LCD and the AutoSCAN had not been set yet. So, the top panel was there, but was not visible. After holding down the the AutoSCAN button on the LCD the panel appeared. Problem solved!

Thanks for your support. We love Ubuntu!!!

---

### Post by Rubi1200 on 2011-04-02
Glad you got things sorted out :)

Please mark this thread Solved using the Thread Tools near the top of the page.

---


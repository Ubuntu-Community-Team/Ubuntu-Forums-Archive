---
title: "Multiple DE on the same install"
date: 2015-10-19
forum: Desktop Environments
---

### Post by el_rico on 2015-10-19
Hello,

I know how to install multiple DE, or switch from one to another. My question is more how multiple DE can be on the same install.

More specifically, we are different users at home. And some prefer Unity, another Gnome Shell, and yet another XFCE. How can I add - and what should I take care of - other DE while:
[LIST]
Preserving current state (boot, login, ...)
[/LIST]
[LIST]
Avoiding pollution from one DE to another
[/LIST]
My understanding is that those DE share system files and config files. Also, a DE comes with applications that are quite specific to it...

So, is it possible? How to maintain the best possible "isolation"? I'd like not to have multiple Ubuntu installation just for that... (that would also prevent user switching)

Thanks!

---

### Post by marcus_s on 2015-10-19
With Ubuntu, it is possible to install different DE's on the same machine. A user is able to choose the environment one wants to be in, in the login screen. One has to click the little cogwheel in the login prompt box, and select the environment. Normally each environment keeps its files in their dedicated folder in a user's folder. For example, [Enlightenment]("http://www.enlightenment.org") stores its files in the folder [FONT=courier new]/home/[username]/.e[/FONT] .

There are some caveats when installing some environments into Ubuntu: for example, you can install GNOME 3 - but this might effectively break Unity (at least this was the case with earlier Ubuntus, such as 14.04 and below). This means that you might be unable to use Ubuntu's standard environment (called Unity). So you might want to be careful when installing different environments.

Apart from that, each user created gets own profile on that Ubuntu installation. This means your Desktop is separate from another user's Desktop on that installation. This is due to the fact that every profile for a user is in a different folder inside [FONT=courier new]/home[/FONT] - therefore user data cannot interfere with other user's data (file systems in use in Linux work with user permission settings for access).

Bottom line is: Yes, you can do that - but be careful if you want to retain Ubuntu's original desktop experience.

---

### Post by cmcanulty on 2015-10-19
yes that is correct I used to have multiple DEs and each user can also have any different ones they like. I did find some flakiness in the panel configurations on a laptop, on a desktop I didn't. The issues were very minor though.

---

### Post by Frogs Hair on 2015-10-19
Multiple DE's can be cluttered and though system files are shared file managers are different for each except for Gnome and Unity. Similar applications doing the same job is common also. KDE and Gnome based desktops/applications are not the best match as far as theme compatibility. All applications installed are available to each user making for a cluttered experience .

---

### Post by cmcanulty on 2015-10-19
yes I agree though the apps you don't want can all be uninstalled which is a bit laborious but in the end smoother. I finally decided xubuntu has the right traditional look for me but I do add libre office and a few other of the more standard ubuntu apps. Of course that makes the lightweight DEs not as lightweight but to me the panels and menus are the things I really like to make a smooth working DE. Good luck, half the fun of Linux is getting things to be exactly as you wish.

---

### Post by vasa1 on 2015-10-19
IIRC, xfce-notifyd takes over the notification system and merely logging back into Unity doesn't restore Unity's notification system. There are quite a few posts about that over at Ask Ubuntu.

I also remember that the appearance of the GRUB screen and splash screen and login screens can get altered.

Even menu items can look confusing because all the text editors (for example) maybe referred to generically in the menus rather than by their application names.

Overall, quite messy unless you do a bit of cleaning up.

---

### Post by el_rico on 2015-10-20
OK, thanks for the hints!

So, it seems to be not as easy as just installing the desktop packages and few settings... So I'll just have to install multiple Ubuntus (maybe a good motivation to play with btrfs for file deduplication ;)), and users will have to reboot.

-ec

---


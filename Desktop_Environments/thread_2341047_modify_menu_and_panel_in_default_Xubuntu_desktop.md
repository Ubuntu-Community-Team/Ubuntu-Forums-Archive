---
title: "modify menu and panel in default Xubuntu desktop"
date: 2016-10-24
forum: Desktop Environments
---

### Post by janxub on 2016-10-24
Hello

I created a small network with samba 4 as domain controller. So users can log in on a member client (pc runninig Xubuntu 16.04) and then their home account gets mounted from the server on the local client. when a user logs out all data are stored on the samba 4 dc and his home folder gets unmounted.

When a user logs in for the first time the default Xubuntu desktop configuration is used to set up the new account.

Now I would like to make some changes in the default Xubuntu desktop configurations:
a) replace the Whikers-Menu with the old one (menu before whikers came in)
b) create a second panel at the bottom of the Xubuntu desktop
c) add the most important applications (for example libreoffice writer, calc, draw, impress) to the bottom panel

So that when a user logs in for the first time, he/she has the 'old menu' at the top left corner and a panel at the bottom with every day applications in that panel.

How do I have to modify or add some files in /etc/xdg to reach my aim?

Kind regards, janxub

---

### Post by Dennis N on 2016-10-24
Have you looked at **Whisker Menu > Settings > Panel**? This is where all you ask can be done. Be sure you are logged in to the account that is to be customized.

+ on top will add a new panel. You drag it to the desired location. The original panel is panel 0 in the selector at top, the new one is panel 1, so any changes you make only affects that selected panel. All the options for the selected panel are in the tabbed sections under that. 

The Items tab allows you to add or remove items - you need to add the "Applications Menu" and remove the "Whisker Menu" for goal (a). Add a "Launcher" for applications you want to launch from a panel icon. Position panel items with the arrow keys. They are shown in left to right order in the display.

Experiment and Expore.

---

### Post by ajgreeny on 2016-10-24
I think you wanted all those changes to be automatically applied to any new user you create, which is a bit different to Dennis N's suggestion, though what he says is basically correct; I just think it does not do quite what you want.

The old style menu is still available in the panels of XFCE as the Applications Menu, added in the usual way with a right click, and a second panel can easily be added from the panel properties dialogue, using the + sign at the top, and then dragging it where you want.

Any application launchers you want can be added to a panel by firstly adding launchers separately for each app needed, then configuring the launchers one by one.

I am not, however, sure how you get that current panel configuration into a new user by default when first created but it looks as if replacing the **/etc/xdg/xfce4/panel/default.xml** with **~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml** from a newly configured user's home, and then renaming it also to default.xml might work.

Worth a try, but back up the system files you edit first so you can restore them if needed.

---

### Post by janxub on 2016-10-25
Hello and thanks for the replies!!

Perhaps my initial question wasn't quite clear. Sorry.
But the idea replacing the "defaults" files with one of the "desired configuration" seems quite well.

Thank's (to both) again!!

Kind regards, janxub

---

### Post by ajgreeny on 2016-10-25
Please let us know if it works should you get round to trying it.  It will be very helpful to others.

---

### Post by janxub on 2016-11-04
hello ajgreeny

I'm working on it. But without success til now. It seems to be more difficult, than I thought. On my Xubuntu-Test-Desktop I couldn't find a solution I'm happy with it.

Kind regards

---

### Post by CantankRus on 2016-11-05
If you want to customize the look of newly created accounts wouldn't you use the /etc/skel directory.
> The /etc/skel directory contains files and directories that are automatically copied over to a 
new user's home directory when such user is created by the useradd program.
[http://www.linfo.org/etc_skel.html](http://www.linfo.org/etc_skel.html)

Log into a new account, set up the xfce panel how you want, then copy ~/.config/xfce4 of that account to /etc/skel
maintaining the home folder directory structure.
Should now have a **/etc/skel/.config/xfce4** directory containing xfce4 configs which will be copied over when new accounts are created.

---


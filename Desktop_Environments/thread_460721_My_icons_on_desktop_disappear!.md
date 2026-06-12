---
title: "My icons on desktop disappear!"
date: 2007-05-31
forum: Desktop Environments
---

### Post by pac-man on 2007-05-31
Hi I'm new to this forum and I come around with a question. Everything seemed to be OK with my xubuntu 6.06.1 until I decided to uninstall the firefox 1.5 and install the version 2.0.0.3.

All of a sudden and without any reason, after using firefox for a while, the icons I got on my desktop disappear! and that ain't all, when I right-click on my desktop to show the menu, it doesn't appear and the background color of the desktop also changed.

Any help will be much apreciated. Thanks in advance.

---

### Post by pac-man on 2007-06-01
bump.

Anyone?

---

### Post by Znupi on 2007-06-01
Have you tried rebooting? Maybe thunar crashed...

---

### Post by pac-man on 2007-06-01
Hehe, it was several days ago, of course i've rebooted lots of times and it didn't work for me.

I tried to reinstall xfce4 desktop and it didn't work either, my desktop icons, the apps menu in the top panel and the right click menu (that menu that has the same elements than the apps menu in top panel) .. all are still gone!

I am forced to type alt+f2 to run a command, to be able to use the terminal.

---

### Post by ThomasNL on 2007-06-01
I think you uninstalled ubuntu-desktop

---

### Post by pac-man on 2007-06-01
Nope, it wans't even installed when everything was OK.

Remeber, i'm using xubuntu

---

### Post by Znupi on 2007-06-01
Is thunar working? Check **gconf-editor** and look through (I think) **apps->thunar->desktop->preferences** and make sure **show_desktop** is checked. This is how nautilus works, I'm not sure thunar works the same, but it may be something close.

---

### Post by pac-man on 2007-06-06
Thunar doesn't even appear under the apps item in gconf-editor; however, thunar works fine.

I've updated my xubuntu from 6.06 to 6.10 and the problem is still there, only affecting my user session.

Any other ideas?

---

### Post by cyrylski on 2007-06-07
I have the same. No icons, no right-click menu omn the desktop. I guess that's because I messed sth up while removing Xfce. I first installed it via terminal with a guide so I only copied commands into bash. Then I removed packages via synaptic, now I'll have to restore Xfce :/

---

### Post by ogmundur on 2007-06-11
I had the same problem - went away by allowing xfce to manage the desktop in the settings manager. Applications -> Settings -> Settings Manager -> Desktop -> Allow Xfce to manage the Desktop. Hope this helps.

---

### Post by elev on 2008-04-02
Thanks ogmundur, 
I was having this problem in Xubuntu and now the icons are back.\
I wonder how that box go unchecked in the first place...


Thanks again.

---


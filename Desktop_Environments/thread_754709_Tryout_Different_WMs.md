---
title: "Tryout Different WMs"
date: 2008-04-14
forum: Desktop Environments
---

### Post by Kiri on 2008-04-14
I'm thinking about trying out some different Window Managers, mainly because I can't seem to get multi-monitor setup working properly in gnome. 

Can I try out other WMs without messing up my gnome desktop?
If I install KDE, Openbox, Xmonad, Enlightenment, etc will I still have all my standard gnome apps and settings there if I switch back to gnome?

Is there anything else I need to consider? I guess that installing other WMs will take a fair bit of disk space, and I may not be able to run all the applications I currently have installed on them ?

thanks

---

### Post by joselin on 2008-04-14
Sure, there is no problem on it. Just install it, and in your others WM you have all the applications available.

Regards

---

### Post by kerry_s on 2008-04-14
> **Kiri said:**
> I'm thinking about trying out some different Window Managers, mainly because I can't seem to get multi-monitor setup working properly in gnome. 

Can I try out other WMs without messing up my gnome desktop?
If I install KDE, Openbox, Xmonad, Enlightenment, etc will I still have all my standard gnome apps and settings there if I switch back to gnome?

Is there anything else I need to consider? I guess that installing other WMs will take a fair bit of disk space, and I may not be able to run all the applications I currently have installed on them ?

thanks

the de's, yes there could be problems, there big and bring alot of stuff.
the wm's aren't bad there usually smaller and won't install alot of extra things.

for de's i recommend just grabbing some live cd's.
the wm's should be alright, not much gets installed so they can be easily cleaned up.

i'll start you off with fluxbox, which is the most common light wm.
[B]sudo apt-get install fluxbox menu
sudo update-menus
[/B]
now log out, choose fluxbox in the menu and log back in.

good luck

---

### Post by urukrama on 2008-04-14
As kerry_s said, window managers are small and won't take much space on your hard disk. You should be able to play nearly all applications in window managers, though they may not automatically show up in the menus of the window manager (but that is easily solved by editing these).

For help with Openbox or Pekwm, have a look at the links in my signature. They should help you to get started. The Openbox guide is much more comprehensive and covers some things that will be relevant for other window managers as well (such as Gtk themes, wallpapers, etc.)

---

### Post by Koori23 on 2008-04-14
> **kerry_s said:**
> 
[B]sudo apt-get install fluxbox menu
sudo update-menus
[/B]
now log out, choose fluxbox in the menu and log back in.

good luck


this part is VERY IMPORTANT. If you don't run "sudo update-menus", you'll likely get very frustrated, very quickly because you can't access anything.

I've noticed when you go installing and uninstalling DE's, you risk taking out some innocent programs with it; in my case, it was gstreamer plugins and Mplayer.

---

### Post by Kiri on 2008-04-15
Thanks for the replies everyone. I'm planning to give some like openbox a try.
I would also like to try KDE, but I might try and do that through a virtual CD or in a VM based on advice here

---


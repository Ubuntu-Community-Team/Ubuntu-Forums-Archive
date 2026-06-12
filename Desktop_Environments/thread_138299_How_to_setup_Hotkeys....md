---
title: "How to setup Hotkeys...?"
date: 2006-03-01
forum: Desktop Environments
---

### Post by adie273 on 2006-03-01
Could anyone tell me how to get hotkeys to work?

I installed hotkeys and would like t get my volume buttons to work.

Does anyone know how to set this kinda thing up?

Thanks in advance for any help,

Adie

---

### Post by gingermark on 2006-03-01
I searched google for "kde hotkeys" and the first hit was [this rather garish page](http://www.kriyayoga.com/love_blog/post.php/426). It's for SuSE, but I assume the instructions will work.

Kubuntu uses it's own "System Settings" instead of KDE's Control Centre, but the Control Centre should still be on your sysem I think. To run it, press Alt+F2, type 'kcontrol', and press enter.

---

### Post by msak007 on 2006-03-01
Hmm I've seen a post about getting the volume keys to work before, and I'm not sure how but mine worked right out of the box. I don't think I had to install anything for hot keys though. I did it through System Settings - [this link]("http://www.kubuntu.org/docs/kquickguide/C/ch03s07.html#regional-khotkeys") tells you how to get to KHotKeys in System Settings. The first thing I did was to choose a keyboard layout and chose the closest thing to my keyboard (I think it was a Microsoft Wireless Media Keyboard or something like that - not all the keys I have on my keyboard are useable though). Then once you've enabled a layout, You can use KHotKeys and Keyboard Shortcuts to customize your keyboard shortcuts to get hot keys to work and have certain keys launch locations / applications. If you find that the keyboard layouts are completely missing after upgrading to KDE 3.5.1 as I did, [this thread]("http://www.kubuntu.org/docs/kquickguide/C/ch03s07.html#regional-khotkeys") should help you out. It links you to  [this]("https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/30295") bug report, which tells you to issue the command "sudo ln -s /etc/X11/xkb /usr/share/X11". That's what fixed it for me anyway. Hope this helps.

---

### Post by f1dave on 2006-03-02
An alternative to hotkeys you may like to try is xbindkeys. It works really well with my wireless logitech set, even picking up all the extra media keys. Install it, then run 

xbindkeys-config

To start setting up shortcuts.

---


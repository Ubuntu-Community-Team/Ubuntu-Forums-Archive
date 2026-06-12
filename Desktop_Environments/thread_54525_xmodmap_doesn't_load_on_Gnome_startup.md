---
title: "xmodmap doesn't load on Gnome startup"
date: 2005-08-05
forum: Desktop Environments
---

### Post by vitorsouza on 2005-08-05
Hello there,

First of all, I've browsed a lot of threads and tried a lot of stuff. I'm getting very weird behaviour and that's why I'm posting to the forum, so please help me.

I created a /etc/xmodmap.conf file with some keys configuration (AltGr+Q = /, AltGr+W = ?, the old story...) and after I log into Gnome executing `xmodmap /etc/xmodmap.conf` makes the keys work fine.

I want to execute that automatically for every user that logs in. So I tried everything except the solutions that tell me to create a ~/.gnomerc or something like it. It's imperative that it works for *every* user.

That being said, I've tried putting `xmodmap /etc/xmodmap.conf` in /etc/gdm/PostLogin, /etc/X11/Xsession.d/60xmodmap-fix, /etc/X11/xinit/xinitrc and /etc/X11/Xsession, with no success.

I "debugged" a little bit. Placed some `echo something > /tmp/tmpfile` on some of the scripts above and I see they execute fine, but the keys just don't work. I have installed KUbuntu before, and putting it into xinitrc or Xsession made it work (both by starting in KDE and through console with `startx`). Does Gnome overwrite it with its own configuration? How can I solve this issue?

My xmodmap.conf follows:

```

keycode 0x18 =	q	Q	at	Greek_OMEGA	slash	Greek_OMEGA
keycode 0x19 =	w	W	lstroke	Lstroke	question	Lstroke
keycode 0x1A =	e	E	EuroSign	EuroSign	degree	EuroSign

``` 

Thanks in advance for any pointers.

Vítor Souza

---

### Post by strikeforce on 2005-08-05
Have you tried System -> Preferences -> Keyboard.

Then monitor what files are changed?

---

### Post by vitorsouza on 2005-08-08
[QUOTE=strikeforce]Have you tried System -> Preferences -> Keyboard.

Then monitor what files are changed?[/QUOTE]

Thanks for the reply.

I tried that, but didn't help me. Two files are changed:

~/.gconf/desktop/gnome/peripherals/keyboard/kbd/%gconf.xml
~/.gconfd/saved_state

Both of them are in my user directory, so that doesn't solve my problem. Besides, saved_state is unreadable and %gconf.xml is an XML file representing the changes I made under System -> Preferences -> Keyboard, and there is no configuration there for changing specific keys (like what xmodmap does).

The weird thing is that this is very easy under KDE (I've done it using KUbuntu), but GNOME seems to override whatever xmodmap configuration loaded during the execution of /etc/X11/xinit/xinitrc (ran by startx script) or /etc/X11/Xsession (ran by GDM/KDM).

I installed KUbuntu before but then replaced it by Ubuntu because I thought it would have better support (since Canonical probably uses Ubuntu/Gnome), but I'm thinking of switching back... I guess I'm a KDE guy...  ;-) 

Thanks,

Vítor Souza

---


---
title: "KDE Compose Key"
date: 2006-11-07
forum: Desktop Environments
---

### Post by BitTorrentBuddha on 2006-11-07
I recently switched to KDE, mostly for aesthetic preference, and I was wondering, is there a way to use the compose key, prefereably mapping it to caps lock as I had GNOME?

---

### Post by BitTorrentBuddha on 2006-11-10
Found it after some menu digging. To anyone interested who may stumble upon this thread, this is how to do it as of edgy, it can be accomplished by running:```
kcontrol
``` And then select: 
Regional & Accessibility > Keyboard Layouts > Xkb Options.
In that tab make sure "Enable xkb options" is enabled then scroll down and enable "Caps Lock is Compose" (or change the compose key to whatever you want.) Apply and voila, it works again.

---

### Post by nekr0z on 2006-11-20
I have another problem of that sort. I use GNOME on my laptop (can't stand KDE), but I use two KDE applications in GNOME, Amarok and Psi (just because I can't stand anything else).

The problem is, Compose key doesn't work in these two apps. It works perfect everywhere else, but not in Qt applications (in Dapper it used to work everywhere).

Can this be fixed somehow?

---

### Post by lemsx1 on 2007-12-02
It seems that for us Gnome users the command should be:

setxkbmap -option compose:menu

Now I try doing Compose+N+~ to produce ñ as would be done in Gnome... However, that does not seem to work. 

Perhaps because of Compiz? AmaroK is such a good app... it's a shame that it was written for KDE and not Gnome ;-)

---

### Post by lemsx1 on 2007-12-02
$> setxkbmap -print
xkb_keymap {
        xkb_keycodes  { include "xfree86+aliases(qwerty)"       };
        xkb_types     { include "complete"      };
        xkb_compat    { include "complete"      };
        xkb_symbols   { include "pc(pc105)+us+compose(menu)"    };
        xkb_geometry  { include "pc(pc105)"     };
};


man setxkbmap showed me a few tricks... Still not working though.

---

### Post by lemsx1 on 2007-12-02
Sorry but it did work, it's just that KDE uses different ways to do things:

[http://www.astro.ufl.edu/it/docs/intl-keyboard.html](http://www.astro.ufl.edu/it/docs/intl-keyboard.html)


Compose+'+e = é

In Gnome you can do e+' as well (and I'm used to doing it this way.

Good to know thoug. 

Next problem...

---


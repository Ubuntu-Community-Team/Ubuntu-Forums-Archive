---
title: "Multimedia Keys"
date: 2006-09-16
forum: Desktop Environments
---

### Post by jeppewinther on 2006-09-16
Just recently installed Ubuntu, and was quite surpriced to see that my Multimedia Keys worked straight out of the box, with fancy volume graphics and whatnot (Most of everything worked actually, pleasant install :).

Alas, it was not ment to last, though. I installed Amaroke, fiddled a bit with the Global Hotkeys in that program and screwed up my general gnome settings somehow. The keys still registre (XF86LowerVolume type output from trying to binding them in Keyboard Shortcuts and using xev) but although I can bind them, they don't work anymore.
I've gotten a workaround using KeyTouch, but it's sluggish, and slightly buggy (displays "Muted" when I try to alter the volume, works at different speeds each time, sometimes not at all and so on) so I was wondering if there was someway to get the original thing working again short of reinstalling.

/Jeppe Winther

---

### Post by jeppewinther on 2006-09-17
bump

---

### Post by lagagnon on 2006-09-17
In Preferences try changing your keyboard to a wrong keyboard and then back again to the right one? Might work, just a guess...

---

### Post by jeppewinther on 2006-10-13
I got around to resolving the issue :)

Apparently gnome didn't like the XF86FunctionName format the keys were listed as when I tried to rebind the keys. When I reverted to using the old format, things worked like a charm.

I discovered this by chance, when I tried to set up a new user. It all worked like when I first installed!
So while logged on as this new user I went into the System -> Preferences -> Keyboard Shortcuts menu, and found the keycodes that was originally used (0xa0, 0xae, 0xb0 were the ones listed for mute, vol-up and vol-down respectively for my keyboard). Then I logged back onto my own user, and through a bit of tinkering found out that the file that holds this kind of information is stored at /home/user/.gconf/apps/gnome_settings_daemon/keybindings/%gconf.xml .

So I edited that file, replaced the XF86 references with the 0xa0 type codes, and everything is working like a charm.
The Keyboard Shortcuts gui doesn't allow you to type in codes manually, least not as far as I know, and although I did find a tool that allowed this at some point, I couldn't find it again.

Hope this is useful to someone.

---

### Post by zeddock on 2008-02-07
Under Gusty I found this:
```
~/.gconf/apps/gnome-volume-control$
```

I think it must be an updated addition.  But I still cannot figure out how to get my control buttons to affect change.

There is a beautiful little screen display that shows volume going up and down but it doesn't actually change anything.

zeddock

---


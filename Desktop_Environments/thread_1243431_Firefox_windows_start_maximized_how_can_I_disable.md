---
title: "Firefox windows start maximized: how can I disable?"
date: 2009-08-18
forum: Desktop Environments
---

### Post by dannyman on 2009-08-18
Hello,

I have a Dell Mini 10, which shipped with Ubuntu.  It is a very nice distro but I have one irritation: every time I open a new window in Firefox it maximizes itself.  I can hit the maximize button again to make it normal size but really . . . !?

Can someone advise where this vendor configuration is likely to be set so that I might undo it?  Thanks!

Sincerely,
-daniel

---

### Post by Nate8nate on 2009-08-18
All you have to do is unmaximize it then close Firefox by going to File->Quit instead of clicking the X.  It should start at your defined size.

---

### Post by dannyman on 2009-08-18
Nate,

Thanks, but that is not it.  I unmaximize, File: Quit, restart, and the new window is maximized.

If a popup opens, it is maximized.

Something in the desktop environment is kludged. :(

Sincerely,
-daniel

---

### Post by jerrrys on 2009-08-18
you can also try

View->Zoom->Reset.

---

### Post by dannyman on 2009-08-18
Thanks, Jerry.  Alas, this isn't a font size issue: the Firefox _window_ is full-screen.

---

### Post by Nate8nate on 2009-08-18
Try shift-clicking the X button to close Firefox.

---

### Post by Nate8nate on 2009-08-18
By the way, do you use Compiz or Metacity for compositing?

---

### Post by jerrrys on 2009-08-18
ok dannyman...

been looking here

[http://kb.mozillazine.org/Category:Issues_(Firefox](http://kb.mozillazine.org/Category:Issues_(Firefox))

and found this

[http://support.mozilla.com/en-US/kb/Firefox+window+is+too+large+or+opens+off+screen](http://support.mozilla.com/en-US/kb/Firefox+window+is+too+large+or+opens+off+screen)

---

### Post by dannyman on 2009-08-18
Thanks, jerrys!

I tried that but no dice.  I'm pretty damn certain this is configured into Gnome somewhere . . . I know you can do stuff like this in other window anagers . . .

Cheers,
-danny

---

### Post by jerrrys on 2009-08-18
your right danny, i remember reading about a 'terminal' fix a couple of months back and it was in the forum.  firefox was in the title, think ill do a quick search

---

### Post by jerrrys on 2009-08-18
[ATTACH]125374[/ATTACH]

got it right this time TOP ONE

---

### Post by dannyman on 2009-08-18
For what it is worth, if I switch to xfce, and start Firefox, the window opens set to the appropriate size.

I tried digging around in gconf-editor but found nothing obvious.  Many references to metacity, which sounds like either a city simulator or a growing tumor . . .

---

### Post by dannyman on 2009-08-18
Thanks again, jerrys.  I was able to get in there with the "ccsm" command but that setting had no effect.  (I even restarted the window manager . . .)

---

### Post by jerrrys on 2009-08-18
did you go here?

[ATTACH]125383[/ATTACH]

---

### Post by dannyman on 2009-08-18
jerrys,

Yes, even if I disable that setting in gconf-editor and reboot, nada. :/

---

### Post by dannyman on 2009-08-18
Ah!

[http://mydellmini.com/forum/ubuntu-netbook-remix/1525-windows-always-open-maximized.html](http://mydellmini.com/forum/ubuntu-netbook-remix/1525-windows-always-open-maximized.html)

I did:

```
sudo killall maximus
sudo apt-get remove maximus
```

Problem solved.

NOTE: my approach has been somewhat "sledgehammer" . . .

---

### Post by jerrrys on 2009-08-18
:)

---


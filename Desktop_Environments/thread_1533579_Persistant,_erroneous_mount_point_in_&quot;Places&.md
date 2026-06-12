---
title: "Persistant, erroneous mount point in &quot;Places&quot;"
date: 2010-07-18
forum: Desktop Environments
---

### Post by Krank on 2010-07-18
I've been living with this problem a while now - it's not life-threatening or whatever, but it's annoying and I'm at a complete loss as to why it's happening.

In Places, there are a bunch of stuff, right? First the Nautilus bookmarks, then whatever's in the /etc/fstab etc, right?

[IMG]http://i215.photobucket.com/albums/cc308/krank23/Technical%20difficulties/Extramountpointunabletomountdownloa.jpg[/IMG]

A bit like that, right? Only, as you can see, something's not right. There are two entries for "Downloads". One is a perfectly working SMB-mounted network location. The other, well... the screenshot really says it all. And when I write "all", I mean everything I've been able to gather on the error. I really am at a complete loss. The end of my rope.

The extra Downloads thingie has no Eject button, only responds with an unhelpful "Unable to mount" message when I select it, and has neither rename nor remove in its context menu.

[IMG]http://i215.photobucket.com/albums/cc308/krank23/Technical%20difficulties/Extramountpointcontextmenu.jpg[/IMG]

So what have I tried?

[LIST]
[*]Well, logging in as another user (or using sudo to launch nautilus) shows it's not system-wide, as the extra entry doesn't appear for anyone but me.
[*]Removing all references to "downloads" from the /etc/fstab file only removes the working entry, not the problematic one.
[*]It's not a bookmark, so I can't really remove it there.
[*]I've been looking through the gconf-editor, but can't seem to find anything there, either.
[*]The problem stuck with me through the upgrade from 9.10 to 10.04.
[/LIST]


So... Any ideas? Preferrably ideas not including removing my user and all its settings?

---

### Post by Krank on 2010-07-18
Nevermind, I finally found the right key in the gconf-editor. Weird.

---

### Post by Krank on 2010-07-19
Apparently not.

If I comment out the entry in /etc/fstab, then reboot, then uncomment and do a sudo mount -a...

...then it works. No extra item in places.

However, if I reboot the computer with the /etc/fstab entry uncommented, then the entry is there when I log in.



Problem *sigh* still unsolved, I guess.

---


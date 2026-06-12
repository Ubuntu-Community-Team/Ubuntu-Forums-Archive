---
title: "KDE version of Keyboard Shortcuts"
date: 2005-11-07
forum: Desktop Environments
---

### Post by stimpack on 2005-11-07
I know there is a simple shortcut editor, I wonder if there is somthing like Gnomes, where I can assign multimedia keys to volume/play/stop etc.. I dont see any options for this in KDE?

---

### Post by aysiu on 2005-11-08
[QUOTE=stimpack]I know there is a simple shortcut editor, I wonder if there is somthing like Gnomes, where I can assign multimedia keys to volume/play/stop etc.. I dont see any options for this in KDE?[/QUOTE] I believe it's in System Settings under Regional/Accessibility > Keyboard Shortcuts.

---

### Post by asimon on 2005-11-09
Yes, this is really a mess in KDE.

For generall volume control I just posted instructions at another thread, see [Comment #5 of Volume control in Kubuntu?](http://www.ubuntuforums.org/showpost.php?p=478403&postcount=5).

Play, Stop, Forward, etc. are player specific. For amarok for example go to "Settings -> Configure Shortcuts..." in the menu. Most KDE apps have a "Configure Shortcuts..." menu entry.

---

### Post by stimpack on 2005-11-09
The solution in the end was to use xmodmap to map the multimedia keys to XF86RaiseVolume etc.. 

For Starting a web browser it was a little more involved, again mapping a multimedia key to XF86WWW with xmodmap and then following this guide [http://www.ubuntuforums.org/showthread.php?t=87737](http://www.ubuntuforums.org/showthread.php?t=87737) using KHotkeys to map XF86WWW for firefox.

Gnome surprisingly was much better than KDE for once, it needed no work, it all worked 'out of the box'. Though I can tell KHotkeys is alot more powerful when youve got it going.

---

### Post by mavr on 2006-02-05
I still can't get mine to work. I've tried to set up the shortcuts from the mixer, but my combination FN+arrowUP doesn't seem to be a valid one. Actually when i press it nothing happens. I've got xmodmap but i've no idea what to do with it. Can anybody help me? As already said on this thread i did it on Gnome with no problem but it seems much harder on Kde, like a lot of things i've been through already.
Gnome+1

---

### Post by droiders on 2006-03-08
bleh, i'm a douche, ignore that whoever saw it....why can you delete a post on here?

---


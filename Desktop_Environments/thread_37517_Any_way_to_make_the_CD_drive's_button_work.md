---
title: "Any way to make the CD drive's button work?"
date: 2005-05-27
forum: Desktop Environments
---

### Post by Curlydave on 2005-05-27
The CDrom interface reminds me of middle school with the old-school macs, where to eject you had to click on an icon on the desktop that appeared and do it from there. I'd like to be able to just hit the button on my drive. any fixes? What causes this bug in the first place? What's so weird is that even when running no OS like in bootup it works, but not in ubuntu. Weird.

---

### Post by verbalshadow on 2005-05-27
[QUOTE=Curlydave]The CDrom interface reminds me of middle school with the old-school macs, where to eject you had to click on an icon on the desktop that appeared and do it from there. I'd like to be able to just hit the button on my drive. any fixes? What causes this bug in the first place? What's so weird is that even when running no OS like in bootup it works, but not in ubuntu. Weird.[/QUOTE]

do you have a CD in the drive if so this is the normal behavior ie mac like.
ubuntu mounts the cd and then disable the button to ensure that it not removed until umounted ie Eject in the right click menu. i think its a good thing but i got kids that love pushing buttons,

If there is no cd in the drive i have no idea what is wrong.

i have no idea how to disable this "feature", sorry.

---

### Post by infinito on 2005-05-27
[QUOTE=Curlydave]The CDrom interface reminds me of middle school with the old-school macs, where to eject you had to click on an icon on the desktop that appeared and do it from there. I'd like to be able to just hit the button on my drive. any fixes? What causes this bug in the first place? What's so weird is that even when running no OS like in bootup it works, but not in ubuntu. Weird.[/QUOTE]
This is the expected behaviour with HAL/DBUS/HOTPLUG architecture on Linux right now. I've read that someday this will change, and then dbus will recognize the button pressed, so it will umount and eject the cd, but this will be in the future (or not).

By now, don't expect this to change,,,

---

### Post by neighborlee on 2005-06-09
[QUOTE=infinito]This is the expected behaviour with HAL/DBUS/HOTPLUG architecture on Linux right now. I've read that someday this will change, and then dbus will recognize the button pressed, so it will umount and eject the cd, but this will be in the future (or not).

By now, don't expect this to change,,,[/QUOTE]

curious..maybe someone shoud talk with suse developers..they seem to have this working just fine ..mandrake does too faik and knoppix also uses it , and of course xandors and maybe linspire..others do too but I dont have complete list.

good luck to the team in fixing this..

cheers
nl

---

### Post by word_virus on 2005-06-09
[QUOTE=neighborlee]curious..maybe someone shoud talk with suse developers..they seem to have this working just fine ..mandrake does too faik and knoppix also uses it , and of course xandors and maybe linspire..others do too but I dont have complete list.

good luck to the team in fixing this..

cheers
nl[/QUOTE]

I for one prefer the default drive-locking behavior.  I keep my tower on the floor and can't tell you how many times I've accidentally bumped it with my knee or something and accidentally ejected the cd I was listening to.  It might be nice if it was a behavior that could be toggled on/off, though, say during a major cd ripping session.

---

### Post by angkor on 2005-06-09
I really don't mind the current behaviour as I rarely use cds anyways. If you're constantly changing cds I can imagine its a bit troublesome, but for now I don't really care.

---

### Post by Trickyphillips on 2005-06-09
Hmm. When I try to eject a CD while the drive is mounted, it will open up 1/10 of the way, and slide back in. If I press the button a couple more times, it fully ejects.  :razz:

---

### Post by zAo on 2005-06-09
On topic: is there a cd in your drive? Is it listed when you type 'mount' ?
If so: try 'sudo umount /dev/hdc' (when hdc is you cdromdrive).

---


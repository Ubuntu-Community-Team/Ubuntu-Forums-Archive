---
title: "Problem with screen settings"
date: 2008-08-26
forum: Desktop Environments
---

### Post by olafvi on 2008-08-26
A friend has Feisty Fawn Kubuntu installed. He is less than a Linux newbie, much less, much much less. Anyway, this is a software question that is affecting hardware. He thought he'd had enough of the default wallpaper and wanted to have some pictures instead. I told him, if it ain't broke, don't fix it...did he listen? Unfortunately he is 30 miles away and I don't have any linux installed at this moment (for shame). He did something that ended up making his screen larger than his monitor. He can see the upper left corner, I believe he said, but the rest is off the screen. Is there any way to correct this, especially given that he can't even see most of the screen? Or do I have to make a trip and install a more current release. As I say he can only see part of the screen as it appears to have blown up in size and now he can only see part of it. Maybe fix it using line commands??? I can install Linux and do rather basic troubleshooting but my career was on a mainframe so am no expert on this. Any help would be greatly appreciated.
Thanks,
olafvi/George

---

### Post by jonathanku on 2008-08-26
> **olafvi said:**
> He did something that ended up making his screen larger than his monitor. He can see the upper left corner, I believe he said, but the rest is off the screen.

My guess that either the screen resolution has flipped to something very low (e.g. 640 x 480) so the main components of the desktop can't all fit in that few pixels. So the resolution would need changed.

Or.... some setting (probably resolution) has changed causing the monitor to go to default settings. So check if the actual monitor has settings for shifting or squashing the picture on screen.



If xorg.conf has been messed around (this controls screen resolution stuff amongst other things), then it might be looking for a backup of that file. The file lives in /etc/X11/
...and backups should too. So you could backup the current xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.20080826
```
then re-instate a previous backup:
```
sudo cp /etc/X11/xorg.conf.oldbackup /etc/X11/xorg.conf
``` (where "xorg.conf.oldbackup" is another backup you've identified).

..
..
If that doesn't help (or makes things worse!) re-instate the latest backup:
```
sudo cp /etc/X11/xorg.conf.20080826 /etc/X11/xorg.conf
```
Just a thought based on my past experience.

---

### Post by jedi-penguin on 2008-08-26
try this command

dpkg-reconfig xserver-xorg

It will reset the screen setting for the machine

---


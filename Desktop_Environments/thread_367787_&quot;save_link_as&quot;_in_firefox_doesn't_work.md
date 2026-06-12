---
title: "&quot;save link as&quot; in firefox doesn't work"
date: 2007-02-22
forum: Desktop Environments
---

### Post by ubername on 2007-02-22
Hi (on reflection I might have posted this under the absolute beginners forum)

I am trying to download the webmail extension for Thunderbird. So I went to the extension page (using firefox) and found the download link.

When I right click on the link and select "save link as" the cursor changes for a moment but then nothing happens.

I tested whether this was a problem specifically for thunderbird / firefox downloads by going to another website  and right clicking one of their links. Same thing. So it seems my "save link as" function is not working.

It worked fine under windows which is why I am posting on the ubuntu forum. 

FYI

I have a dual-boot Ubuntu / XP PC, both looking at a FAT 32 partition where I store the FF and TB profiles. I also have firestarter running. (but I think firestarter runs automatically: It's just that I have the gnome interface running)

Can you help?

TIA

---

### Post by louis_nichols on 2007-02-22
That's tricky business, sharing profiles between Linux and Windows. That's because settings stored for both TB anf FF often use absolute paths, which work very different in the 2 OSs, as you know. I'd say it's no wonder you have trouble. But tracking it down and solving it might prove a pain.

I can only think of one thing, but it's a long shot, Go to the about:config page of the applications and search for the option ui.allow_platform_file_picker. Change its setting, whatever it is at that moment, Then try again.

My suggestion is to not share the profiles between the 2 OSs.

---

### Post by airtonix on 2007-02-23
NO this isnt a fat32 problem....i too have this problem. not a fatty in sight.

download anything and firefox hangs. opening sysmte monitor reveals that netstat is running nad not giving up cpu resources.

---

### Post by louis_nichols on 2007-02-23
I never said it had anything to do with FAT32.

I said it is connected to the way the 2 OS's refer to paths:

WINDOWS: C:\aaa\bbb\ccc
LINUX: /home/username/aaa/bbb

This is sure to cause trouble. Been there myself.

---

### Post by ubername on 2007-02-23
Thanks for the help

My firefox about:config has the parameter (ui.allow_platform_file_picker) set to true, my thunderbird about:config doesn't have the entry at all. Maybe that's the problem?

That said, when I delete messages in TB from one platform they are deleted in the other platform (and when I change things like bookmarks in FF they are also reflected in the other platform.).

Interestingly, if I use the 'Install extension' option from the extension webpage it sort of works. I tested by trying to download the FireFTP extension. That installed, but when I tried to run it from the FF tools menu, it said 'You do not have appropriate permissions or directory does not exist'

TIA for any help

---


---
title: "Update Manager malfunctioning"
date: 2005-12-16
forum: Desktop Environments
---

### Post by SamH on 2005-12-16
The last couple of weeks, I've noticed that Update Manager will not download and install updates.  It notifies me properly, lets me login to run the update, but when the secondary window opens to show download progress, it immediately closes.

Apt-get update and apt-get upgrade function normally from CLI so it's not like this is a great big deal.  I haven't thought until just now if upgrade in Synaptic is working, I'll try that next time I get the uprade notification in my system tray.  It should work because I have installed new packages with Synaptic since the Update Manager has started acting goofy.

Just wondering if anybody else is having an issue with it.

---

### Post by carlosqueso on 2005-12-16
I think this may be a bug. [http://bugzilla.ubuntu.com/show_bug.cgi?id=20586](http://bugzilla.ubuntu.com/show_bug.cgi?id=20586) is the bug I filed on it, but I can't seem to get any info that helps the people fix it.  Maybe there are logs or something I can look at, but I don't know.

---

### Post by SamH on 2005-12-16
Yep, carlos, that is exactly what I'm seeing.

Guess I should remember to look in bugzilla.

I haven't thought about it much since it's so easy to work around.  Lately, when I do see the update icon, I just go straight to a terminal and do the sudo apt-get routine.

Thanks for the bugzilla link, I'll start checking it occasionally for a resolution.

---


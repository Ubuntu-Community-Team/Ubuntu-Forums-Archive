---
title: "Soundjuicer - MP3 profile missing"
date: 2007-12-21
forum: Desktop Environments
---

### Post by radioraheem on 2007-12-21
I've ripped CDs to MP3 (high quality VBR) using Sound Juicer before, but for some reason the MP3 profile does not show up in the preferences screen any more.

If I go to the Edit Profiles area it is there, but it does not appear in the drop down menu list of profiles.  I know the screen where you actually edit the profile has a checkbox for Active, but it makes no difference whether or not it is checked.  I even tried unchecking it, shutting down sound juicer, and then restarting and re-enabling it but that didn't help.

Very weird considering it worked fine the last time I tried to use it.  I've checked dependencies and several forum threads without luck.  Most of them pertain to enabling MP3 ripping in Sound Juicer, but it appears that a stock Gutsy install already has everything that's needed to do it.

Anyone seen this before or have any idea of why it won't work?  I even tried to reinstall sound juicer using synaptic but it won't let me remove the package without removing the entire ubuntu-desktop.

Thanks in advance for any tips!

---

### Post by bigfox on 2007-12-22
I am noticing the same problem.

I found two bug reports about this issue in launchpad.net

[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/84007](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/84007)
[https://bugs.launchpad.net/sound-juicer/+bug/109849](https://bugs.launchpad.net/sound-juicer/+bug/109849)

---

### Post by radioraheem on 2007-12-26
Well that's strange, I fired up sound juicer today and now the MP3 profile is back.  No major updates run since I posted this originally.

Oh well, at least now it's working.  Hope the problem doesn't come back.

---

### Post by radioraheem on 2008-01-05
Well strike that, it just disappeared as quickly as it reappeared.  Color me confused.

---

### Post by radioraheem on 2008-01-27
Just started having the same problem with a fresh install of Linux Mint.  I updated tickets at LaunchPad.  Hope they can figure it out!

[https://bugs.launchpad.net/sound-juicer/+bug/109849](https://bugs.launchpad.net/sound-juicer/+bug/109849)

[https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/178652](https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/178652)

---

### Post by mexicola on 2008-01-29
Had the same problem, installed gstreamer0.10-plugins-ugly and gstreamer0.10-plugins-ugly-multiverse and it works fine! For some reason it didn't install the multiverse by default...

---

### Post by radioraheem on 2008-02-10
I had the first one installed already but gstreamer0.10-plugins-ugly-multiverse was not.

Installed it and presto, sound juicer works again.

Thanks!!!

---

### Post by radioraheem on 2008-02-19
Drat... this seems to have only temporarily solved the problem...  the MP3 profile disappeared again.

I have updated the bug page for soundjuicer with more details, hopefully they'll fix this problem in the next release.

My kingdom for a reliable linux cd ripper....

---

### Post by 8086 on 2008-06-29
Just enable the multiverse version of the gstreamer ugly plugin using synaptic.

---


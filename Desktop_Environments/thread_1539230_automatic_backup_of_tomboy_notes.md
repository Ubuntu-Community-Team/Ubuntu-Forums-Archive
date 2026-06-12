---
title: "automatic backup of tomboy notes ?"
date: 2010-07-26
forum: Desktop Environments
---

### Post by AM_SOS on 2010-07-26
hi all,

i have been using tomboy notes for some time now, and i must admit that they have must life much easier for me :)

however, since i now have several notes, most of which i do not want to delete immediately, i am wondering is there is some way of backing up all the notes ?

i looked around, but tomboy seems to be a pretty basic software, and there doesn't seem to be any backup facility available.

obviously, i don't want to take the inefficient way of manually copy-paste the content of each note on to OO writer and saving all this data.

anyone ? how to i do an automatic backup ?

thanks!

---

### Post by dv3500ea on 2010-07-26
You could use ubuntu one ([https://one.ubuntu.com/]("https://one.ubuntu.com/"))
I don't use it much but it has a feature to synchronise tomboy notes online:
> To setup, open Tomboy, choose Edit > Preferences and click the Synchronization tab. Select the "Tomboy Web" Service and click the "Connect" button. Login to the Ubuntu One website and add your computer to synchronize notes. When you see the confirmation page appear, close your web browser and click "Save" in the Tomboy preferences window. You can also enable automatic synchronization by clicking the checkbox. (from the ubuntu one website)

---

### Post by sharm on 2010-07-26
Synchronization is nice, though of course if you delete a note it is also deleted from the server.

A true backup solution would be regularly backing up ~/.local/share/tomboy along with other import files and directories on your system.

---

### Post by AM_SOS on 2010-07-27
hi sharm,

i check usr/share/local/tomboy but it seems to only have only one sub folder "icons". i couldn't see any of the notes that i have saved.
am i missing something here ? or are the notes hidden or some such thing ?
thanks!

---

### Post by coldraven on 2010-07-27
I sync mine to my external USB HDD.
Handy if you want to re-install or play with a new release.

---

### Post by sharm on 2010-07-27
> **AM_SOS said:**
> hi sharm,

i check usr/share/local/tomboy but it seems to only have only one sub folder "icons". i couldn't see any of the notes that i have saved.
am i missing something here ? or are the notes hidden or some such thing ?
thanks!

The path I mentioned was ~/.local/share/tomboy .  ~ is your home directory.  And yes, by default, directories starting with . are hidden by nautilus (though you can tell it to show you hidden files and directories).

---


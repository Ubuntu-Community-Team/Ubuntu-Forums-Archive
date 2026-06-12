---
title: "plzz help!!!! problem with terminal"
date: 2008-01-25
forum: Desktop Effects &amp; Customization
---

### Post by alwar.sumit on 2008-01-25
i've installed ubuntu gusty recently...........i tried a command   rm -rf .*   in the terminal.
after that all the settings were lost.  previously when i type ls in terminal it shows the files and directories in color so that we can distinguish between them. but not all are coming in black color. what should i do??????

thanks.........

Sumit

---

### Post by dark_phantom on 2008-01-25
I assumed you did this at your home directory.  Well, the rm command is a pretty nasty command if not used properly.  I'm afraid you lost your data if it was not backed up.  Maybe others would know how to bring those config files back, but I doubt that's would be the case.

Just try to reinstall whatever tools you had, give that a shot.  Good luck and remember try to avoid the rm specially with a *.

---

### Post by startherepodcast on 2008-01-25
rm -rf * is generally not a command you should type in because it removes all your personal folder... Please see the dangerous command post at the top of the Linux Beginners Forum

---

### Post by Lord Illidan on 2008-01-25
Did someone on the forums suggest this command?

---

### Post by alwar.sumit on 2008-01-26
i want to ask how to recolor the terminal back??????
plzz help

---

### Post by BobCFC on 2008-01-26
You have probably deleted the config files in your home folder, you can copy the default options for the terminal back...


Paste this at the terminal:

```
cp /etc/skel/.bashrc ~
```

This copies the default config file back to you home folder.   Then type **bash** to reload it... hopefully the colours will return.



(The .bashrc file is a hidden file in your home directory containing the terminal config.  The skeleton folder has the default settings for new user accounts.)

---

### Post by alwar.sumit on 2008-01-27
thank you very much..........the commands works..........it recolor back the terminal..............but one problem still persists............that is the color is coming only in the names of directories..........file names are still colored black..............now wat shud i do??????????

thanks again..........

Sumit

---


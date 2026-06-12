---
title: "Cannot select any options in compizconfig"
date: 2007-11-14
forum: Desktop Effects &amp; Customization
---

### Post by dreamsR4living on 2007-11-14
Compiz Fusion was working fine before and still, but right now when I want to change anything in CCSM it is not possible to click any checkbox. Because of that I cannot change anything anymore in CCSM. I reinstalled it a few times, but it doesn't seem to work. :(

What can I do:confused:

By the way, I'm using Ubuntu Gutsy AMD 64

---

### Post by dentaku65 on 2007-11-14
Try:

```
sudo rm /usr/bin/ccsm
```

```
sudo apt-get --reinstall install compizconfig-settings-manager
```

```
ccsm &
```

Go in Preferences and set as Backend: Flat-file Configuration Backend

---

### Post by dreamsR4living on 2007-11-15
Thanx for the quick reply. I tried it, but I still have the same problem.

---

### Post by amrith on 2008-02-22
Even I am facing the same problem in only one this login.
In my other login their is no problem.
I did the above said options but didnt help.
:(

---

### Post by dreamsR4living on 2008-02-23
Some time ago I found the problem. For every user compiz stores its settings in the home folder. When you delete these settings the problem should be solved, but you need to reconfigure compiz.

Workaround;

1. Go to your home folder (graphically, not in terminal) and press Ctrl+H. It will show al your hidden folders (only in Ubuntu, not Kubuntu). There you will also find the folder ".config"

2. First make a backup of this folder somewhere else on you system as I don't know for sure what I deleted at that time. After you made the backup, delete every folder/file related to compiz within this folder.

3. In the home folder you will also find the folder ".gconf", from there go into the folder "apps" and do the same after you made a backup.

From there compiz (and everything else) should work as normally again and otherwise you have a backup. Another option is just to simply overwrite these folders with the folders from the other (working) user account.

Hope this will solve your problem :)

---


---
title: "Trouble &quot;resetting&quot; beryl"
date: 2007-06-28
forum: Desktop Effects &amp; Customization
---

### Post by traxtar3 on 2007-06-28
ok... Been using ubuntu for a while and getting very comfortable. Installed beryl. screwed around with it too much and screwed it up. removed it via synaptic and then reinstalled it to try to get the beryl defaults back. it went back to the old settings.

ok....

apt-get remove beryl (and all accociated packages)
apt-get install beryl (and all accociated packages)

Still no defaults.

How do i get a "fresh", just like out of the box, beryl? is there a config file i need delete, or a package i may have overlooked when removing it many times over and over again?

Any help would be much appreciated.

---

### Post by benanzo on 2007-06-28
you need to delete the hidden .beryl folder in your home directory.  Just open nautilus then hit CTRL-H to show hidden files/folders and delete it.  When you uninstall an app it usually doesn't get rid of the configuration files.  You have to select "Mark For Complete Removal" in Synaptic to delete those.

Good Luck!

---

### Post by hyperair on 2007-06-28
Just run this command:
```
 
rm -r .beryl
rm .beryl-managerrc

```

Then you should be fine. ^^

---

### Post by fongs on 2007-07-02
> **benanzo said:**
> you need to delete the hidden .beryl folder in your home directory.  Just open nautilus then hit CTRL-H to show hidden files/folders and delete it.  When you uninstall an app it usually doesn't get rid of the configuration files.  You have to select "Mark For Complete Removal" in Synaptic to delete those.

Good Luck!

where is nautilus i have the same problem.

---

### Post by mitchell486 on 2007-07-02
Nautilus is the window viewer. So. Open your home folder. So that you can view your files. Then hit Ctrl+H and it will show all your folders. Even the hidden ones.

---

### Post by traxtar3 on 2007-08-14
I figured it out. I didn't know i had to select a different session. Gnome or Gnome with XGL.  Randomness is key!

---


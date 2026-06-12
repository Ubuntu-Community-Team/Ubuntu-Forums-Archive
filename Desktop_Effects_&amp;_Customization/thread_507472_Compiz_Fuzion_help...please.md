---
title: "Compiz Fuzion help...please?"
date: 2007-07-23
forum: Desktop Effects &amp; Customization
---

### Post by mtrpcic on 2007-07-23
I'm trying to install Compiz Fuzion, and have tried twice to no success.  Both times I get an error message.

I can't post exactly what it is, but I get it after I do:   "apt-get upgrade"

A certain file returns "Error Code 1" and that's all it tells me.  Also, it screws up the updater and tells me to do the following:  "apt-get install -f"

Not sure what it all means because I'm new, but I found that removing Trevinos repositories and then doing:  "apt-get remove compiz" fixes it.

The first time I had this problem, I didn't know how to fix it and I couldn't use the GUI again, so I reformatted.  This time though I figured it out.


Has anyone else had this problem, and could they help me?

I'm following the sticky "Compiz Fuzion on Ubuntu Feisty 7.06" or whatever.

Any help would be GREATLY appreciated.  I'm using the official nvidia driver (installed with Envy) for my XFX GeForce 8500 GT, if that helps at all.

Thanks in advance.

---

### Post by Sqwishy on 2007-07-23
Error Code 1 means that you have conflicting packages or something and you need to uninstall one.
To install all the compiz packages you run 
```
sudo apt-get install compiz compizconfig-settings-manager compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins
```
I think it should uninstall compiz-gtk so don't worry.

---

### Post by mtrpcic on 2007-07-23
I believe it always was removing compiz-gtk, and I followed the guide exactly.  Which apt-get install should I use, yours:

**sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf**

or the one from the guide:


**sudo apt-get install compiz compizconfig-settings-manager compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins**

---

### Post by Sqwishy on 2007-07-23
It probobly doesn't matter, if theirs doesn't work try mine i guess.

---

### Post by mtrpcic on 2007-07-23
Thanks a ton man, it worked perfectly.  I did have to remove compiz-core.

Thanks again.

---


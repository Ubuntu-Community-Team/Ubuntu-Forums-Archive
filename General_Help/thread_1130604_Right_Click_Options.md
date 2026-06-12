---
title: "Right Click Options ?"
date: 2009-04-19
forum: General Help
---

### Post by ravi_buz on 2009-04-19
How can i add send to pen drive in the right click menu in ubuntu.

---

### Post by aaronp on 2009-04-20
Probably need to be a bit more specific in what you want but if I can assume you are talking about within Nautilus then there are a range of Nautilus scripts that you can use to add extra right click options to Nautilus file actions.
I believe if there is not one that matches what you need exactly you can write your own as well.

I'd say try looking at [www.gnome-look.org](www.gnome-look.org) first and check out the 'Nautilus Scripts' section in the link list on the LHS.

---

### Post by ravi_buz on 2009-04-20
Yes u r right i can add many things in the right click menu , But i am unable to find how to add send to removable device( pendrive ) the option u get in windows if u have inserted a pen drive or an removable device

---

### Post by Tim Sharitt on 2009-04-20
If you are using Ubuntu 8.10 or older, you will need to add a script (as aaronp suggested). However, in Ubuntu 9.04, this functionality has been added to the nautilus-sendto plugin.

Once you have found a script to do what you want, you'll need to install it.

First install nautilus-script-manager via Add/Remove, apt, or whatever method you prefer.

To install from the terminal with apt-get
```
sudo apt-get install nautilus-script-manager
```

Next you'll need to copy the script to /usr/share/nautilus-scripts.

From a terminal:
```
sudo cp /path/to/script /usr/share/nautilus-scripts/script
```

Then enable it with 
```
nautilus-script-manager enable script
```

Edit: There is a script here which may do what you want: [http://www.gdr-exiles.com/nautilus/](http://www.gdr-exiles.com/nautilus/) - Courtesy of Google ;)

---

### Post by aaronp on 2009-04-20
You may need to write your own then.

This thread here has a couple of links, one with a useful site that has a lot of scripts:
[http://ubuntuforums.org/showthread.php?t=802119](http://ubuntuforums.org/showthread.php?t=802119)

or this article here could help in writing one:
[http://www.linux.com/feature/114134](http://www.linux.com/feature/114134)

hth
Aaron

EDIT: Nautilus Actions looks like it is worth a try too if you are no comfortable writing scripts by hand: [http://www.grumz.net/index.php?q=node/8](http://www.grumz.net/index.php?q=node/8)

---

### Post by ravi_buz on 2009-04-20
Thanks for your help i will check the links

---

### Post by mc4man on 2009-04-20
> Edit: There is a script here which may do what you want

That nautilus script will work just fine to send to any mounted removable device with one main  condition
Nothing involved can contain a space, meaning the volume label of the drive (mount point) and or the file or dir. being sent. Files inside a sent dir. can contain spaces.

It also works fine by just adding to ~/.gnome2/nautilus-scripts instead of adding to /usr/share/nautilus-scripts if you so wish.

---


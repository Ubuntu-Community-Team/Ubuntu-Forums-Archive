---
title: "Install Mate desktop"
date: 2021-04-02
forum: Desktop Environments
---

### Post by dddman on 2021-04-02
Hello

I have installed Ubuntu desktop in my Dell tablet.  

[https://www.amazon.com/Dell-27XYW-Latitude-Notebook-i5-8350U/dp/B07B1QZ5HK](https://www.amazon.com/Dell-27XYW-Latitude-Notebook-i5-8350U/dp/B07B1QZ5HK)

I then installed the gnome desktop to the Ubuntu install and now want try out the mate desktop.  What is the terminal command for installing the mate desktop to an existing ubuntu install?

Thanks

---

### Post by CatKiller on 2021-04-02
```
sudo apt install mate-desktop-environment
```

Bear in mind that's going to double up things like text editors, file browsers, settings utilities, and so on. If you're going to keep wanting to try out different desktop environments it's better to do so from VMs or live USBs, and then just install the one that you want.

---

### Post by TheFu on 2021-04-02
Or 
```
sudo apt install mate-desktop
```
if you don't want all the integrations and extra applications.

However, using different DEs under the same account that are based on the same underlying libraries has some risks because settings for one DE could mean something different in another or could lead to undefined results.  Whenever testing out different DEs, it is always best to use a new useraccount for each until you decide which you want to be your daily driver.
Gnome3 and KDE shouldn't have any collisions with their settings, since Gnome3 uses GTK+ and KDE uses Qt.  But Mate is also based on GTK+, so collisions in settings could happen with Gnome3, Mate, XFCE, Cinnamon, off the top of my head.

---

### Post by dddman on 2021-04-02
Well I did as CatKiller said and now running the mate desktop.  It added another 500M to the install, Gnome desktop was like 600M.  So yes, its bloated, but everyone is playing nice so far.  I just want to try all three out.
Thanks for the help

---

### Post by ActionParsnip on 2021-04-03
Please mark as solved if the issue is sorted

---

### Post by dddman on 2021-04-03
Well I been playing with all three and find common glitches with the touchscreen and Bluetooth.  During all this Budgie caught my eye and I decided to have a go with it.  That turned out to be a bad idea, now nothing but windows will boot.  Too much crap on one install I guess.

Its been mention already, but looks like virtualbox is the way to go and I am familiar with the product.  So by running both OS at the same time; I should be able to have my cake and eat it too :)

---

### Post by dddman on 2021-04-04
Ok, got Ubuntu up and running as a virtualbox guest system.  Nothing wrong with Mate, but Ubuntu's sleek look and 5 years of support has won out.

I have 2 finger scrolling working, but not what I want.  Been trying to get one finger to work.  This may not be possible with any Linux touch system.

Haven't look at Bluetooth yet, but really don't care if my (Bt)Stylus works or not.

I assume Ubuntu can be reloaded in the 20G partition that has been created and that will give me a stand alone install that will work well with keyboard assist.

So for now I think this is the best I can do.

Solved

---


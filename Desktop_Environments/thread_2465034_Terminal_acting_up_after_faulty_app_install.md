---
title: "Terminal acting up after faulty app install"
date: 2021-07-20
forum: Desktop Environments
---

### Post by anarkitty on 2021-07-20
Apologies if this isn't in the right category, but I'm not too sure what happened here.

I just installed the lubuntu 20.04 lts and have been poking around making customizations. In my previous environment I installed the Folder Color application to use in caja, which seemed to work fine when I was using the lubuntu 20.10. However, I noticed with this one that I cannot find Caja or my default file manager in the menu or by searching. But I saw that it was installed, so I decided to go ahead and install the Folder Color package. 

However I think I mis-entered something. What should have been, 
```

sudo add-apt-repository ppa:costales/folder-color
sudo apt-get update
sudo apt-get install folder-color-caja
caja -q

```

I somehow missed entering that last "caja -q" and it asked to do an installation of 10.9MB. I thought that was odd and rather large but figured it was fine. Then I thought I'd better try to uninstall and reinstall it just in case, however the data was much smaller (something like 30kb which is more what I'd have expected). So, whatever was in that 10.9MB that ended up downloading the first time, I have no idea what it is or how to remove it.

Worse, is now whatever it might have just done to caja or anything else in my system, now certain things in my terminal window are strange, such as the inability to resize the terminal window with the cursor. It only lets me go into the menu and manually resize it which is ridiculous.

If anyone knows what is going on here and how to reverse it, that would be greatly appreciated.

I managed to get a screenshot of what packages it was adding (I think) on the first install:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288834&stc=1[/IMG]

---

### Post by Geoff_Lane on 2021-07-22
> **anarkitty said:**
> Apologies if this isn't in the right category, but I'm not too sure what happened here.

I just installed the lubuntu 20.04 lts and have been poking around making customizations. In my previous environment I installed the Folder Color application to use in caja, which seemed to work fine when I was using the lubuntu 20.10. However, I noticed with this one that I cannot find Caja or my default file manager in the menu or by searching. But I saw that it was installed, so I decided to go ahead and install the Folder Color package. 

However I think I mis-entered something. What should have been, 
```

sudo add-apt-repository ppa:costales/folder-color
sudo apt-get update
sudo apt-get install folder-color-caja
caja -q

```

I somehow missed entering that last "caja -q" and it asked to do an installation of 10.9MB. 



Try sudo apt-get --purge remove folder-color-caja
then sudo apt-get --purge autoremove

That might resolve it then maybe re-install

Geoff

---

### Post by guiverc on 2021-07-22
> **anarkitty said:**
> 
Worse, is now whatever it might have just done to caja or anything else in my system, now certain things in my terminal window are strange, such as the inability to resize the terminal window with the cursor. It only lets me go into the menu and manually resize it which is ridiculous.


Sorry I have no experience with folder-color so can't comment there.  (It's a GTK3 program so makes little sense to me on a LXQt/Qt5 environment; *inefficient* on resources)

Some links that maybe helpful

Check your appearance - [https://manual.lubuntu.me/lts/3/3.2/3.2.2/appearance.html](https://manual.lubuntu.me/lts/3/3.2/3.2.2/appearance.html) 
Openbox (or WM settings) - [https://manual.lubuntu.me/lts/3/3.2/3.2.11/openbox_settings.html](https://manual.lubuntu.me/lts/3/3.2/3.2.11/openbox_settings.html)

Hotkey shortcuts - [https://manual.lubuntu.me/lts/F/keyboard_shortcuts.html](https://manual.lubuntu.me/lts/F/keyboard_shortcuts.html)

(ie. I hold down ALT then use right-click & drag to resize, or is that what you no longer have working?)

---


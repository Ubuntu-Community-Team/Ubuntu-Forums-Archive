---
title: "Firefox icon disappeared from the dock"
date: 2022-08-21
forum: Desktop Environments
---

### Post by esso10 on 2022-08-21
Firefox icon disappeared from the dock after I did that:
sudo snap remove firefox
sudo add-apt-repository ppa:mozillateam/ppa
sudo nano /etc/apt/preferences.d/mozillateamppa # Add the following lines and save using [Ctrl]+[X] Package: firefox* Pin: release o=LP-PPA-mozillateam Pin-Priority: 501
sudo apt update
sudo apt install firefox

---

### Post by grahammechanical on 2022-08-21
We are guessing that you are using Ubuntu 22.04. The snap packaged version of Firefox is default in Ubuntu 22.04. That is why its icon is on the dock without the user having to do anything. Remove Firefox and you remove the icon also.

Do you now have a version of Firefox installed? Is it the deb packaged version? Does it load? Does the icon appear in the dock? If so, then right click the icon and select Add to Favourites

Regards

---

### Post by esso10 on 2022-08-24
> **grahammechanical said:**
> We are guessing that you are using Ubuntu 22.04. The snap packaged version of Firefox is default in Ubuntu 22.04. That is why its icon is on the dock without the user having to do anything. Remove Firefox and you remove the icon also.

Do you now have a version of Firefox installed? Is it the deb packaged version? Does it load? Does the icon appear in the dock? If so, then right click the icon and select Add to Favourites

Regards

Do you now have a version of Firefox installed? Is it the deb packaged  version? Does it load? YES
Does the icon appear in the dock? NO

It's on the dock but with a blank icon. I mean it has a place in the dock, but doesn't appear!

Thank you in advance, man!

---

### Post by Frogs Hair on 2022-08-24
Try removing the blank icon from the dock and adding it again.

---

### Post by esso10 on 2022-08-24
> **Frogs Hair said:**
> Try removing the blank icon from the dock and adding it again.
 


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290917&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=290918&stc=1[/IMG]

---


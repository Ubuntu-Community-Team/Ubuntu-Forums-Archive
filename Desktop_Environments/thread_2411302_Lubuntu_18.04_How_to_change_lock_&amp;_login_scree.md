---
title: "Lubuntu 18.04 How to change lock &amp; login screen backgrounds"
date: 2019-01-28
forum: Desktop Environments
---

### Post by Norman_Price on 2019-01-28
An old post for a previous version of lubuntu mentioned this method - and it is still good for lubuntu 18.04.
(NB This uses a different conf file to that mentioned elsewhere online (/etc/lightdm/lightdm-gtk-greeter.conf) - editing that file now has no effect)

Put a suitable image (eg x.jpg) in a chosen folder eg /home/norman/Pictures/Backgrounds/. Ensure its permissions allow Anyone read access.

Edit this file like this:
sudo nano /etc/lightdm/lightdm-gtk-greeter.conf.d/30_lubuntu.conf

Comment out the following line by putting a # at the start of the line:
# background=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png

Insert this line to point to your image eg:
background=/home/norman/Pictures/Backgrounds/x.jpg

Exit nano, saving the file.
Try a Lock Screen - the image should appear as background when screen unblanks for unlocking

---


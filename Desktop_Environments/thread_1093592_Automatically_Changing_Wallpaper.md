---
title: "Automatically Changing Wallpaper"
date: 2009-03-11
forum: Desktop Environments
---

### Post by 18zela on 2009-03-11
Hello to everyone and how do you do. I was wondering if there is anyone out there who knows a good automatic desktop background changer. I did some research and did find some but they didn't work well with my version of ubuntu ( I use gutsy gibbon because it works very well with my laptop, i recently tried intrepid ibex but it kept crashing and feisty fawn as well but 7.10 so far has been very stable ). I am fairly new to ubuntu so I would really appreciate detailed steps if any. Thank you.:D

---

### Post by phaze_1 on 2009-03-12
Hey doing just fine how are you. Yes I currently have an animated wallpaper set on my desktop right now and it runs great! you can find it at gnome-look.org and search animated wallpaper well here is the link [http://www.gnome-look.org/content/show.php/All+Day+Long+(Animated+Wallpaper)?content=83443](http://www.gnome-look.org/content/show.php/All+Day+Long+(Animated+Wallpaper)?content=83443) hope it works out for you!:KS

---

### Post by linuxuser21 on 2009-03-12
Try Wallpaper Tray.  You can set a time for it to change and/or change when you log on.

---

### Post by dusan.saiko on 2009-03-12
hava you seen this ?
[http://ubuntu.wordpress.com/2005/12/01/random-wallpaper-in-gnome/](http://ubuntu.wordpress.com/2005/12/01/random-wallpaper-in-gnome/)

or you can write your own script and settign the wallpaper using 

gconftool-2 -t string -s /desktop/gnome/background/picture_filename image_filename
(have not tried that but should work)

---

### Post by linuxuser21 on 2009-03-12
```
sudo apt-get install wallpaper-tray
```
This is how to install Wallpaper Tray.

---


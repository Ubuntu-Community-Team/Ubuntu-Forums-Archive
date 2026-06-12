---
title: "Cairo-Clock and Icon Themes - how to install these?"
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by Osvaldas on 2007-05-21
Stupid and lame question from linux newbie: how to install [Cairo-Clock Themes]("http://www.gnome-look.org/index.php?xcontentmode=186") and [Icon Themes]("http://www.gnome-look.org/index.php?xcontentmode=120")?

Thanks a lot.

---

### Post by Ub1476 on 2007-05-21
Allright, I never used the Clock, but I know of Icon Themes:)

First you need to download the file. Should be something like: iconthemes.tar.gz. 

Now go to System>Preferences>Themes.

Customize>Icons>install

Navigate to where you downloaded the package, click on it and Ubuntu should install it. Now just pick it from the list:)

---

### Post by ericallen on 2007-05-21
firstly open the terminal and type
```
sudo apt-get install cairo-clock
```
then you can go to  'Accessories' then to 'MacSlow's Cairo Clock'
right-click the clock, go to properties and you can select from the default themes

to install your own theme, download it to your desktop
right-click the file and click 'extract here'
then open the terminal and type
sudo mv /home/<username>/Desktop/<filename> /usr/share/cairo-clock/themes
(replace <username> with your username; and <filename> with the name of the extracted file)
then open the clock, go to properties and select your theme from the list

---

### Post by Osvaldas on 2007-05-21
Thanks for helping guys!
Just a one minor thing I would like to know: how to remove a black background that appears around the clock?

Thanks!!!

---

### Post by Ub1476 on 2007-05-21
Um, I'm not so sure but it might be that the clock request 3d enabled? If it do then you need to install correct drivers for your graphic card, so the code:

```
grep direct

```

..will turn out like : direct rendering: Yes (no means that 3d is not working) (yet)

---


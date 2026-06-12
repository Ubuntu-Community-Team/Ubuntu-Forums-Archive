---
title: "No titlebar when window is maximized"
date: 2015-02-25
forum: Desktop Environments
---

### Post by Barteks2x on 2015-02-25
Today after reboot all windows have no titlebars but only when maximized. it happens also on other user accounts. I found [this thread]("http://ubuntuforums.org/showthread.php?t=2254521"), but in this case it was fixed by reinstall (reinstalling what? xfce? linux?,  I don't want to reinstall linux but if there is no other wa to fix it - I can do that). I reinstalled xfce (*sudo apt-get install --reinstall xfce4*, I'm not sure if it's enough) and rebooted, but it didn't change anything.
I rebooted it because after I turned on my laptop today all files were readonly, after reboot it worked, but titlebars disappeared. Is it possible that this is related to my issue?

Xubuntu version: 14.04.2 LTS
XFCE version: 4.10

//EDIT:
I fixed it. After some more googling I found [this]("http://comments.gmane.org/gmane.comp.desktop.xfce.devel.version4/20834"). Someone thought it's a good idea to add to add titleless_maximize option. Strangely, I couldn't find this option anywhere. I had to edit it using settings editor (or whatever it's called in english version of Xubuntu). It's xfwm4 --> titleless_maximize.

---

### Post by raptir on 2015-02-26
Interesting, when I updated today the option was added but defaulted to false.

Edit: Also, in the 15.04 beta the option can be found under Window Manager Tweaks -> Accessibility -> Hide title of window when maximized.

---

### Post by s-breedveld on 2016-02-03
Thanks! This has been bugging me for days. Title bars often show necessary information from the application, so it really puzzles me why this option was turned on by default...

---


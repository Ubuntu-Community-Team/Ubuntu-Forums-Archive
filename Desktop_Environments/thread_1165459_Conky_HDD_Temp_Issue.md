---
title: "Conky HDD Temp Issue"
date: 2009-05-20
forum: Desktop Environments
---

### Post by bLiZz247 on 2009-05-20
Hello All,
I wanted to change the look/style of my conky configuration and liked what I found here: [[COLOR="RoyalBlue"]http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/[/COLOR]]("http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/")

I have everything working great to where I want it except the HDD temp. I get "[COLOR="Red"]localhost [127.0.0.1] 7634 (?) : Connection refused[/COLOR]" in the terminal when it is trying to grab the temp. I am guessing this is because it is not root because when I type [COLOR="Red"]sudo hddtemp /dev/sda[/COLOR] I get [COLOR="Red"]/dev/sda: ST9320421AS: 33°C[/COLOR]

The script it runs contains this:
[COLOR="red"]#!/bin/bash
echo "$(nc localhost 7634 | cut -d'|' -f4)"[/COLOR]

Is there any way I can fix this?

I have a daul hard drive setup in an ASUS g50vt-a2. None in RAID.

---

### Post by bLiZz247 on 2009-05-21
Fixed:

[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=282353&page=10[/COLOR]]("http://ubuntuforums.org/showthread.php?t=282353&page=10")

---


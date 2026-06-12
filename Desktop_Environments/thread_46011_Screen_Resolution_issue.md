---
title: "Screen Resolution issue"
date: 2005-07-02
forum: Desktop Environments
---

### Post by filemanager on 2005-07-02
I am new to Linux. I just installed it with all the 'default' settings if you will, but once I loaded it I realized I wanted my screen resolution to be 1400x1024 (or whatever the setting is, I can't remember the 2nd number), but the highest resolution Linux will allow is 1024x748. Is there anyway to make it bigger?

---

### Post by Xian on 2005-07-02
This topic has been frequently discussed.
Do a [[color=red]search[/color]](http://www.ubuntuforums.org/search.php?searchid=1072603) of the forum and you should find some solutions.

---

### Post by darkpark on 2005-07-03
and if you don't feel like doing a search than edit the file xorg.conf which is located in /etc/X11/  .

scroll down to the bottom of the file and insert the resolution(s) that  you'd like to use.

---

### Post by Teroedni on 2005-07-03
Open a terminal
 right click -> choose terminal

copy this and paste in terminal

cd /
cd etc/X11
sudo gedit xorg.conf

post the result here and i will tell you what to do
Hope this helps
Regards Me :grin:

---


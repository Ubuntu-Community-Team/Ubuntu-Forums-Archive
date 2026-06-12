---
title: "Increase space between notification area icons"
date: 2014-05-18
forum: Desktop Environments
---

### Post by Inoki on 2014-05-18
Hi all,

I was hoping someone could help me out a bit with this: [http://qandasys.info/increase-space-between-icons-in-xfce-notification-area/](http://qandasys.info/increase-space-between-icons-in-xfce-notification-area/)

and point me to a working guide on how to customize the tray by adding more space between icons in the notification area.

Thank you.

---

### Post by Elfy on 2014-05-18
use seperators - then can be set to expand

that panel is set to 100% - change that value to suit

---

### Post by Inoki on 2014-05-18
Thank you Elfy but that's not what I asked for. You can't put separators between notification icons in the tray, indicators. Those need to be changed somewhere in the code of the panel AFAIK.

Please see attachment. I'm having in mind putting spaces between those indicators.

---

### Post by Elfy on 2014-05-18
changed the thread title

---

### Post by egeezer on 2014-05-18
Go to Settings>Settings Manager>Panel, click on the Items tab, click on + in the right-hand column, and choose Separator.  Then use the up and down arrows to put them where you want them.

---

### Post by Inoki on 2014-05-18
@egeezer that's not what I meant. I mean increasing the space between each of the icons in the tray. The indicator/notification icons. Look here: [http://i.imgur.com/YtPEQ2O.png](http://i.imgur.com/YtPEQ2O.png)

---

### Post by egeezer on 2014-05-18
The method I described will work in the panel you're talking about.  You can move separators up and down (which corresponds to back and forth) as well as notifications and launchers.

---

### Post by Inoki on 2014-05-19
@egeezer yer, that works, but not for the plugin of the notification area/indicator, the indicator applet/notification area group icons, so if you try to  move a separator in between you can't, it's added before or after.

From what I've heard/read this has to be modified in the gtk file of the given theme or in the panel config itself, to increase spacing of elements, I just don't know which string to edit.

I've tried to look it up but couldn't find any tutorial.

---


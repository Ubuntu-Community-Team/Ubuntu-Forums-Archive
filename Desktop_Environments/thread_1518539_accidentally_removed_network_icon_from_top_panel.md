---
title: "accidentally removed network icon from top panel"
date: 2010-06-26
forum: Desktop Environments
---

### Post by Honza007 on 2010-06-26
Hello,
I accidentally removed network and sound icon from top panel. Is there any way how to put it back? I've read several howtos that I've to add notification area but it doesn't really work.
I know that if I delete this user and create a new one the icons will be there again but I'd like to do it cleaner way.
This is how it should look like (untouched user account):
[[IMG]http://img690.imageshack.us/img690/5971/correct.png[/IMG]](http://img690.imageshack.us/i/correct.png/)

And this is what I've done :-/
[[IMG]http://img192.imageshack.us/img192/5030/wrongm.png[/IMG]](http://img192.imageshack.us/i/wrongm.png/)

Network icon is missing in both accounts (removed by accident while trying to remove something else :-/ in user "tata" it at least shows sound button.

Running Ubuntu 10.04 LTE x64 final

Any help will be greatly appreciated.
Thank you.

---

### Post by TheDesertDragon on 2010-06-26
Absolutely. Right-Click anywhere on the panel, then click Add To Panel. Find the Notification Area applet, then add it.

Poof!

---

### Post by vince2678 on 2010-06-26
Use synaptic (System Menu >> Administration >> Synaptic Package Manager) [ATTACH]161656[/ATTACH] to check if networkmanager and the indicator for indicator-applet are installed or if it is made to start automatically at bootup ( System Menu >> Preferences >> Startup Applications) [ATTACH]161657[/ATTACH] and then finally check to see if the indicator applet is on the panel.[ATTACH]161655[/ATTACH] [ATTACH]161654[/ATTACH]

---

### Post by Honza007 on 2010-06-27
Thank you guys both.
I was finnaly able tu put volume icon back. but I've still trouble putting back the network icon. Any ideas?
Thank you very much.

---

### Post by XSAlliN on 2010-06-28
Same as above **Add "Notification Area"** - and you should get Volume sticked to NW icon (+UPS if you have one).

---


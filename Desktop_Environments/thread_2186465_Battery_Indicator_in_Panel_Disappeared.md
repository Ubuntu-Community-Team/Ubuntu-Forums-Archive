---
title: "Battery Indicator in Panel Disappeared"
date: 2013-11-07
forum: Desktop Environments
---

### Post by mathiashu on 2013-11-07
Hi. Today, not sure when, my battery indicator on the panel magically  disappeared. This also happened when I was using XFCE (on Xubuntu). I  installed the OS today, so I'm not sure what happened. I haven't  customized it at all because I like the way it looks by default. Here's  how it looks: [IMG]http://i.imgur.com/YH7TupT.png[/IMG]. The only battery indicator I can find in the preferences is this: [IMG]http://i.imgur.com/Xfo41Lq.png[/IMG]. How can I get the default battery indicator back? Thanks in advantage.

---

### Post by Rex Bouwense on 2013-11-07
Navigate to Main Menu->Preferences->Power Manager.  Under General Options, choose Always show icon.  Then close.  Not sure if you have to relaunch the LXPanel, but if you do just enter
```
lxpanelctl restart
```
in terminal or reboot the computer.  That should do it for you.

---

### Post by mathiashu on 2013-11-07
Thank you so much! I just clicked on Power Manager, then I clicked run, and now it's back! Thanks again!

---

### Post by Rex Bouwense on 2013-11-07
Great.  Just make sure that you have Always show icon as your option other wise after you reboot or restart it may revert.

---

### Post by mathiashu on 2013-11-10
Now I have another problem, every time I shutdown the computer it will dissappear again next time I start it, **even though** I have Always show Icon enabled. Any ideas?

---

### Post by newbasford on 2013-12-06
> **mathiashu said:**
> Now I have another problem, every time I shutdown the computer it will dissappear again next time I start it, **even though** I have Always show Icon enabled. Any ideas?

There is a new feature in 13.10 to autostart gizmos like this. From the Menu go to Preferences - Default applications for LXsession. Then click the tab 'Autostart'. In the box next to '+Add' type "xfce4-power-manager" (without the quotes) and then click the +Add button. Then you can just close it down - there's no save button or anything. You can open it up again if you want to check its still there.

(this is also a good place to turn off trackpad tapping by similarly adding "synclient MaxTapTime=0" if you want)  

Next time you boot the lovely battery icon will be where it should be.

---


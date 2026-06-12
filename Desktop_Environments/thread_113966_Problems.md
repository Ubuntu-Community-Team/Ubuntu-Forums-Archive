---
title: "Problems"
date: 2006-01-07
forum: Desktop Environments
---

### Post by hawking on 2006-01-07
Hi friends, I have an Asus A3500E laptop with kubuntu 5.10 (2.6.14ck1 kernel) installed.I have an external usb mouse so I want to disable my synaptics touchpad.I have googled it and searched here and everyone says to change the /etc/X11/xorg.conf file. No matter how I changed it and restarted x several times no change has occured in the configuration of the touchpad... What may be the problem?
    Another problem is as I am on KDE often I get pop-up windows saying "Display Mode : LCD On" and "Display Mode: LCD Off" ... I think this is because my hotkeys aren't configured correctly. Are there any programmes to configure the hotkeys?


    Thanks and Regards,

---

### Post by hawking on 2006-01-08
By the way I use KDE 3.5... May that be the reason of the problems? I mean does it have lots of bugs lately?

---

### Post by Divan Santana on 2006-01-09
try install ksynaptics and see if that can do it for you?

You can set laptop keys using the following:
Not sure, man the below commands.

xev
xmodmap -e "keycode 30 = XF86AudioMute"

---


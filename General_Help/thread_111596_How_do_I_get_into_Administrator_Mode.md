---
title: "How do I get into Administrator Mode?"
date: 2006-01-02
forum: General Help
---

### Post by Brinstar on 2006-01-02
I'm having problems with using my WLAN card. It has been detected (or so it seems) and even the AP looks like it has been recognised, but the WLAN card is disabled (I think this is because I chose not to configure the network at setup time).
 
I don't think it should be too hard to re-enable (I found a 'device sheet' in System Settings) but I can't reconfigure it because I need to be in 'Administrator mode'. It says there should be a button but I've looked on all the menus and I can't see it anywhere.

edit: solved by changing distro to Zenwalk :)

---

### Post by Omnios on 2006-01-02
If I remember correctly when you go into networks there is a admin mode button on the botton, Not on Linux right now so can not check

---

### Post by Brinstar on 2006-01-02
[QUOTE=Omnios]If I remember correctly when you go into networks there is a admin mode button on the botton, Not on Linux right now so can not check[/QUOTE]

I just checked there but couldn't find it. Boy, am I glad I kept my WinXP install, since I have no other way of connecting to the net.

---

### Post by Omnios on 2006-01-02
K logged into Linux KDE and theres a trick to it or rather a feature bug. If you open settings from the taskbar it will not give you a admin option. However if you open the menu then system settings network settings will give you the admin button option

---

### Post by Brinstar on 2006-01-02
[QUOTE=Omnios]K logged into Linux KDE and theres a trick to it or rather a feature bug. If you open settings from the taskbar it will not give you a admin option. However if you open the menu then system settings network settings will give you the admin button option[/QUOTE]

Strange, thats exactly what I did. I'm going to double-check just to make sure...

---

### Post by Lord Illidan on 2006-01-02
How about.....
entering
```
kcontrol
``` in a terminal? Don't use sudo kcontrol, because it can muck up permissions, however.

---

### Post by Brinstar on 2006-01-03
[QUOTE=Omnios]K logged into Linux KDE and theres a trick to it or rather a feature bug. If you open settings from the taskbar it will not give you a admin option. However if you open the menu then system settings network settings will give you the admin button option[/QUOTE]

I double-checked it, and there is no such button. 

What is odd is that there is an Administrator mode button in 'Users and Groups' but when I click on it, it asks for the password, I enter it, the white box then has a red outline around then it looks like the Admin mode turns itself back off after 5 secs or so.

---

### Post by GeneralZod on 2006-01-03
The Kubuntu control panel is horrendously buggy - I'd suggest just running 

```

kdesu kcontrol

```

from the command-line if you want admin priviledges.

---

### Post by BradChandler on 2006-01-03
On my laptop, I have to maximize the network settings control panel before I can see the Administrator mode button. It's at the very bottom so it can't be seen if the window is small. It ony seems to be that way in the network settings.

---

### Post by Brinstar on 2006-01-03
Ok, thanks to everyone who replied, but I have tried each suggestion and I still haven't got the WLAN up yet.

When i tried the 'kdesu kcontrol' I did get the Administrator mode button, but when I re-enabled the card, it enabled for about a second and turns itself back off again, which was incredibly annoying.

Anyway, looks like I'm going to admit defeat and try out either Ubuntu (Gnome) or Mandrake '06 which is supposed to the first distro that is Centrino Certified (or something), so hopefully I'll have more success there.

---

### Post by Omnios on 2006-01-03
Last didtch you might want to try this forum

[http://www.kubuntuforums.net/index.php]("http://www.kubuntuforums.net/index.php")

 Another thing you can do is install Ubuntu and add Kubuntu desktop to it.

---


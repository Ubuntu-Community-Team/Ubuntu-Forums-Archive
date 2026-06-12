---
title: "beryl won't autostart"
date: 2007-05-04
forum: Desktop Effects &amp; Customization
---

### Post by Bashed on 2007-05-04
I switched to 64bit ubuntu feisty fawn and now bery won't auto start as it used to.

I added to session (and saved) beryl-manager, restarted gnome and it won't auto start, even after reboot. It disappears from session after I reopen it too.

What should I do?

Also, segoe UI font is bolder in 64bit than 32bit.  Odd but true. In 32bit I had the same settings I have now for all fonts I selected segoe ui 9pt, regular (no bold). but here in 64bit it shows bolder, on regular setting (same hinting, etc settings on 96dpi as was in 32bit).

Any hints why?

---

### Post by Pox on 2007-05-04
Try starting a terminal and doing this:
```
cp /usr/share/applications/beryl-manager.desktop ~/.config/autostart/
```

I _think_ that's where GNOME keeps autostart apps, not sure... I know it's true for XFCE, anyway.

---

### Post by anthortic on 2007-05-05
i had the same problem but with the 32 bit version. as far as i can tell it was because i installed beryl with automatix instead of add/remove programs :confused: . anyway i resolved this problem by opening the file browser and clicking to
 [B]
/usr/share/applications/[/B]

then copying the berylmanager file in that folder

next up i opened the terminal and typed

**sudo nautilus**

then when the file browser opened i clicked to 

/etc/xdg/autostart

and pasted into that folder. 
Job Done!!

or more quickly, press ALT+F2 paste the following command and click on run in terminal

```
sudo cp /usr/share/applications/beryl-manager.desktop /etc/xdg/autostart
```

---


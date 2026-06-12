---
title: "kde double click?"
date: 2006-02-08
forum: Desktop Environments
---

### Post by ESPOiG on 2006-02-08
is there a way to get everything to open with a double click instead of a single click.... cuz i tryed knoppix the other day and kde looks all good but suks with the single click option

so im gunna stik with gnome

---

### Post by GeneralZod on 2006-02-08
Yeah, but it's not where you'd expect it - took me ages to find it!

Bring up the KDE Control Centre - I'm not sure how to do this in Knoppix, but it's bound to be in the main menu somewhere.  In Kubuntu, it's in the K-Menu under "System Settings".  Go to Peripherals, then Mouse, and you should see the option there.

---

### Post by ESPOiG on 2006-02-08
k thx

---

### Post by Irish J on 2006-02-14
I've ran Kcontrol and set the option, but it doesnt seem to work.  Help?

---

### Post by tagg3rx on 2006-02-14
Thanks Been looking for this

I set it using the menu (as opposed to opening kcontrol from the terminal and it worked) Wouldent imagine there should be a diffrence.  Perhaps you need to 

sudo kcontrol

Just a thought

---

### Post by Irish J on 2006-02-14
[QUOTE=tagg3rx]Thanks Been looking for this

I set it using the menu (as opposed to opening kcontrol from the terminal and it worked) Wouldent imagine there should be a diffrence.  Perhaps you need to 

sudo kcontrol

Just a thought[/QUOTE]
It worked in the menu, cheers.

```
kdesu kcontrol
```
loaded okay, and prompted me for my password, but when i changed the double-click in there it had no efect on the desktop.

same for
```
sudo kcontrol
```

If anyone finds this in future :D

---

### Post by ShanghaiTeej on 2006-02-14
I remember that the double click option (when activiated) doesn't work in kcontrol for some reason.  But double clicking works everywhere else perfectly fine.

---

### Post by FlakJacket on 2006-02-14
you can't use sudo because that will only change it for root user which you probably aren't logged in as.  try just running kcontrol.

Hope that helps,
Flak

---


---
title: "Erratic Desktop Behavior"
date: 2018-07-18
forum: Desktop Environments
---

### Post by paleophyte on 2018-07-18
Hardware: Asus U46E Laptop with i7-2640M 2.8 GHz quad-core processor

OS: Lubuntu 16.04.4 (Kernel Linux 4.15.0-24-generic (x86_64) with LXDE)

Issue: None for months, then a few days ago desktop behaviour became strangely erratic:
 - Minimize, Maximize, and Close buttons cease working. Right-Click ---> Close Window works.
 - Clicking does not deselect last selection, just adds latest selection.
 - Clicked links spawn new windows in both Firefox and Chrome.
 - Keyboard sometimes locks case. If uppercase, number and punctuation keys yield their associated symbols ( "@" instead of "2" and ">" rather than "."). Neither Shift nor Caps Lock affects this.

Cold boot restores normal functionality. Erratic behaviour begins again unpredictably.

I'd be concerned that I had a virus but apparently Linux doesn't do viruses. I'd be concerned that I had a rootkit but haven't installed anything in months and only generic stuff even then. The only recent changes have been installation of automatic updates.

Any help would be greatly appreciated.

---

### Post by paleophyte on 2018-07-23
OK, so after digging around a bit it looks like this is being caused by a sticking key, likely scroll lock or num lock. The original keyboard is twitchy as all hell, so I use a USB keyboard. Can anybody please tell me how to disable the keyboard that's built into the laptop without disabling the USB keyboard?

---

### Post by Rex Bouwense on 2018-07-24
You can start your research here.  [https://askubuntu.com/questions/160945/is-there-a-way-to-disable-a-laptops-internal-keyboard](https://askubuntu.com/questions/160945/is-there-a-way-to-disable-a-laptops-internal-keyboard)

---

### Post by paleophyte on 2018-07-24
Thanx. 

> xinput list
> xinput float whatever value the keyboard ID is

seems to have disabled the keyboard.

Is there a way to implement that so that I don't have to do it manually every time I reboot this silly thing?

---


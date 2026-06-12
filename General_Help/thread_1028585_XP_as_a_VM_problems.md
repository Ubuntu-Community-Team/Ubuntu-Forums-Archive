---
title: "XP as a VM problems"
date: 2009-01-02
forum: General Help
---

### Post by ahounsome on 2009-01-02
Hi Guys, can anyone help with my problem with running XP as a VM on Hardy. Necessity requires me to use windows for Photoshop CS4. Unfortunately, I can't get the XP session to pick up CD or USB devices. If I plug in my digital cameras I get Ubuntu kicking in and XP doing nothing. Is there a way to get around this or am I going to have to invest in another machine just for windows?

---

### Post by Jammanuser on 2009-01-02
> **ahounsome said:**
> Hi Guys, can anyone help with my problem with running XP as a VM on Hardy. Necessity requires me to use windows for Photoshop CS4. Unfortunately, I can't get the XP session to pick up CD or USB devices. If I plug in my digital cameras I get Ubuntu kicking in and XP doing nothing. Is there a way to get around this or am I going to have to invest in another machine just for windows?

If all else fails, you can always install XP on a separate partition...;) And then you will have a normal dual boot of XP and Ubuntu, with less hassle and more coolness! :lolflag:

-Jam man

:guitar:

---

### Post by my_key on 2009-01-02
Using virtualbox? You need the proprietary version from sun, the open source version doesn't support accessing usb devices.

It's free for personal use and can be downloaded here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
You can also add the apt line to your repo's.

Follow this guide to get usb working: [http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04](http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04)

---

### Post by ahounsome on 2009-01-02
Thanks Guys! I think I'll opt for the dual boot option.

---

### Post by dagnabit dang doohickey on 2009-01-02
I recently had to mount a USB stick on a VirtualBox XP VM (but on a Windows host.)

Plug in the USB device and change the USB settings for your VirtualBox VM:
1. Check the "Enable USB Controller" checkbox.
2. Check the "Enable USB 2.0 Controller" checkbox.
3. In the USB Device Filters section, on the right hand side, click the second button down. (The button has a plus sign on it and a tooltip that reads "Add Filter From Device")
4. Click OK

If I'm remembering correctly, that's all that was needed.

For the CD, go to the CD/DVD ROM section of the VirtualBox VM settings. After going through the process of setting up USB, the CD/DVD ROM section will probably be self-explanatory.

---


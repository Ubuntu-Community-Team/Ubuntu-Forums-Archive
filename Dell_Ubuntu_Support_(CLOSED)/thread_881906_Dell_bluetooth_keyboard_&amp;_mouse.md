---
title: "Dell bluetooth keyboard &amp; mouse"
date: 2008-08-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cduffner on 2008-08-06
Not sure if this is so much a Dell issue as it is a bluetooth issue.  My Dell bluetooth peripherals work nicely in the bios & boot screen but when I boot into Ubuntu, I have to pull out my bluetooth dongle and re-plug it in to get them to work.  Any reason why this might be happening or how to fix it?

---

### Post by superm1 on 2008-08-06
> **cduffner said:**
> Not sure if this is so much a Dell issue as it is a bluetooth issue.  My Dell bluetooth peripherals work nicely in the bios & boot screen but when I boot into Ubuntu, I have to pull out my bluetooth dongle and re-plug it in to get them to work.  Any reason why this might be happening or how to fix it?
This is because your dongle is most likely switching to HCI mode.  If you aren't intending on using the dongle with anything else but the keyboard and mouse, change /etc/default/bluetooth

There is an option HID2HCI_ENABLED=1 in there.  Switch it to 0 and reboot.  Your device should always stay in HID mode.

---

### Post by cduffner on 2008-08-06
thank you!  I'm pretty new though.  I got into the folder and found the file, how do I save the changes I make to it?  It won't let me.  Sorry if this is a dumb question.

---

### Post by superm1 on 2008-08-06
> **cduffner said:**
> thank you!  I'm pretty new though.  I got into the folder and found the file, how do I save the changes I make to it?  It won't let me.  Sorry if this is a dumb question.
You have to edit it as a superuser.

You can do something like this:

```
sudo gedit /etc/default/bluetooth
```

---

### Post by karasuman on 2008-08-07
I had this problem with my Inspiron 1525 n.  Here's how I fixed it.

Open up a terminal and type the following:

```
sudo hidd -s
```

At this point, you'll be asked for your password.  Hold down the bluetooth button on your mouse/keyboard until the blue light on the peripheral flashes, then enter your password and hit enter.  After a few moments, the peripheral should be connected.  You may have to do this again from time to time, but, for the most part, it just works for me.

EDIT:  Actually, I misread your original post; this does work for use with the dongle, but if your laptop has internal bluetooth (as mine does), you won't need to connect the dongle anymore to use the mouse/keyboard.

---

### Post by superm1 on 2008-08-07
> **karasuman said:**
> I had this problem with my Inspiron 1525 n.  Here's how I fixed it.

Open up a terminal and type the following:

```
sudo hidd -s
```At this point, you'll be asked for your password.  Hold down the bluetooth button on your mouse/keyboard until the blue light on the peripheral flashes, then enter your password and hit enter.  After a few moments, the peripheral should be connected.  You may have to do this again from time to time, but, for the most part, it just works for me.

EDIT:  Actually, I misread your original post; this does work for use with the dongle, but if your laptop has internal bluetooth (as mine does), you won't need to connect the dongle anymore to use the mouse/keyboard.
Hidd isn't the right way to pair anymore.  it's only there for people who have trouble with the "proper" way.  You should try to pair using the little applet instead.

---

### Post by cduffner on 2008-08-07
I actually resolved the issue with superm1's suggestion, but thank you just the same to karasuman!  Ubuntu has been such a good experience so far and this forum has been so helpful!

---

### Post by shinjimx on 2008-09-03
> **karasuman said:**
> I had this problem with my Inspiron 1525 n.  Here's how I fixed it.

Open up a terminal and type the following:

```
sudo hidd -s
```

At this point, you'll be asked for your password.  Hold down the bluetooth button on your mouse/keyboard until the blue light on the peripheral flashes, then enter your password and hit enter.  After a few moments, the peripheral should be connected.  You may have to do this again from time to time, but, for the most part, it just works for me.

EDIT:  Actually, I misread your original post; this does work for use with the dongle, but if your laptop has internal bluetooth (as mine does), you won't need to connect the dongle anymore to use the mouse/keyboard.

Worked fine for me, and it pairs everytime I start my machine. Thanx!

---

### Post by Crafty Kisses on 2008-09-05
Post the results of > lsusb

---


---
title: "No Wifi light on my Inspiron 6400"
date: 2011-07-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by park_ridge_dave on 2011-07-02
I just wiped all vestiges of Windoze 7 off my trusty Dell Inspiron 6400.

I did a complete install of Ubuntu 11.04. After I did this, I couldn't get my machine to recognize the wifi card at all.

Using Fn-F2 only lit up the BT lite. No wifi indicator. Since I no longer had Windoze to Kludge the activation of the wifi card before I went to Linux I had to fix it.

I used eth0 (wired) to search the web. The solution was right here on this forum.

A poster said to go to the synaptic package manager and set the quick filter to "B43"

[ System>Administration>Synaptic Package Manager ]

I then marked "firmware-b43-installer" and "b43-fwcutter" for re-installation.

I applied the changes, restarted the machine and when I hit Fn-F2 the wifi lite and the BT lite both lit up.

The wifi proceeded to work flawlessly.  And there is no need to do a bunch of crazy things (e.g. boot windows etc.) to get it working each time.

My version of the broadcomm card is a BCM4311, There is a listing on the installer package that says exactly which cards are covered by this set of drivers/firmware.

The big clue, to me, was the wifi lite that didn't work.

Thanks to all those forum members who made this relatively painless. 

This forum is great!

Dave

---

### Post by MARP1961 on 2011-08-16
Glad this is sorted! However, I can't understand why the 'Additional Drivers' application lists STA and B43 driver for this card in Lucid Lynx when Natty Narwhal only lists STA, which just doesn't seem to work with your Broadcom card (I have a Dell Inspiron 6400 with the same card). Why does Natty not allow a more straight forward activation of B43?

---


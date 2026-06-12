---
title: "X61 LCD Brightness will not adjust"
date: 2009-02-15
forum: General Help
---

### Post by madhatter563 on 2009-02-15
Hey everyone,

I'm running an x61 laptop on ubuntu (8.10), and all was working just fine, but a few days ago the brightness adjustment no longer works.  The menu comes up still when I hit the brightness keys, and the bar goes up and down, but there is no actual adjustment to the brightness.. Any ideas?  

I have tried messign with all the power management settings within that menu that deal with dimming, or brightness.  This is really reducing my battery life significantly :(

---

### Post by hogancool on 2009-02-16
I've got the same problem on my Lenovo R61i...

I tried xbacklight but it doesn't work

---

### Post by maquina on 2009-03-05
Hi!

I had the same problem, however I followed this guide and it solved my problem!


[http://vntutor.blogspot.com/2007/12/brightness-buttons-in-lenovo-thinkpad.html](http://vntutor.blogspot.com/2007/12/brightness-buttons-in-lenovo-thinkpad.html)

If for some reason that guide is not available, here are the actual steps,

Open file:

    vim /etc/acpi/thinkpad-brightness-up.sh

Add this line before "exit"

    echo 4 > /proc/acpi/ibm/cmos

Open another file:

    vim /etc/acpi/thinkpad-brightness-down.sh

Also insert this line before "exit"

    echo 5 > /proc/acpi/ibm/cmos

Hope it helps,

---

### Post by snak3 on 2009-03-28
Hey! thank you so much for this,

i can confirm it working w/o probs on Ubuntu 8.10

2.6.27-14 kernel

cool :popcorn:

---

### Post by ecoxmit on 2009-04-10
thanks!! this works perfectly on my Lenovo Thinkpad X300

---


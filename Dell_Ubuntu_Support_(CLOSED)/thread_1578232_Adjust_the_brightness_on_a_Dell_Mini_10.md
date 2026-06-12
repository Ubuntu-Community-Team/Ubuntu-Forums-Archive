---
title: "Adjust the brightness on a Dell Mini 10"
date: 2010-09-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mr_frostee on 2010-09-20
Hello, I'm hoping somebody can help me with this.  I have a Dell Mini 10 on which I have installed Ubuntu 10.04 Netbook edition.  I have installed the Poulsbo drivers (thanks, Intel, for that bucket of fail!) and everything seems to be working fine.

Except for the brightness keys.  I don't even really care that much about the brightness keys per se, I just want SOME way to adjust the brightness of the screen.  I am wanting to mostly use the netbook for web browsing and reading comics, so I don't want it very bright.

Can anybody offer a solution?  Please?

---

### Post by garvinrick4 on 2010-09-20
Right click the upper panel and choose add to panel then add the brightness applet.
SORRY thought gnome and not netbook, my mistake. Disregard please

---

### Post by mr_frostee on 2010-09-20
The Netbook Edition doesn't seems to allow adding applets to the panel.  Those options are greyed out.  Is there another way to access its functionality?

---

### Post by mr_frostee on 2010-09-20
I have installed the "Monitor Settings" app from the Software Center and it gives me the following error message:

"No monitor supporting DDC/CI avilable.

If your graphics card need it, please check all the required kernel modules are loaded (i2c-dev, and your framebuffer driver)."

I don't know if that info is relevant or not.

---

### Post by mr_frostee on 2010-09-20
I just tried selecting GNOME at the login screen, added the brightness applet to the panel and it did nothing.

---

### Post by garvinrick4 on 2010-09-20
In 10.10 it is in power configuration now. Either thru Screen saver to power management
or power configuration. Must be about same in 10.04 because no applets in taskbar setup
as you have found out.

---

### Post by mikewhatever on 2010-09-20
Adding the applet to the panel does nothing at all, but there is another workaround.
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/503577/comments/5](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/503577/comments/5)

---

### Post by mr_frostee on 2010-09-20
mikewhatever: Thankyouthankyouthankyouthankyou!

Worked perfectly!  Off to make a new remastersys image!

---

### Post by mikewhatever on 2010-09-20
Welcome. You can also automate things by adding the command to /etc/rc.local.

---

### Post by yerayenrique on 2010-09-23
Weird, my Mini1018 bright keys worked out of the box.

However, I got another solution.

$ sudo apt-get install xbacklight

Then, to change it:

$ xbacklight -set X (where X, is the value you want, from 0 to 100).

That's what worked for me the best on my previous computer, where bright keys wouldn't work.

---


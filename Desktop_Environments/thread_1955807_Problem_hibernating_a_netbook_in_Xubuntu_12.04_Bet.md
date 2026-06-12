---
title: "Problem hibernating a netbook in Xubuntu 12.04 Beta 2"
date: 2012-04-10
forum: Desktop Environments
---

### Post by sfang on 2012-04-10
Whenever I try to do so, a window shows up with the message "Failed to hibernate the session - not authorized" (I'm not sure what is the exact wording in a English language system) and sends me to the Xscreensaver screen, in which I need to type my password to return to the desktop. I also can't set hibernate in the Power Manager.

I'm running a up-to-date Beta 2. Not sure if it's revelant, but the netbook has a 2gb swap partition. Curiously the hibernate function worked fine in 11.10. 

Thanks.

---

### Post by Lemuriano on 2012-04-11
It could be a bug. I ´m using 2g swap on a htpc and shows the error.

---

### Post by jbernardo on 2012-04-23
Unfortunately it isn't a bug, its a "feature". At least in xubuntu you get a warning, in kubuntu nothing happens when you select "suspend to disk" in the shutdown menu.
What happens is that hibernate has been disabled by default in ubuntu. You need to edit a obscure policy file to get it to work. See the discussion [here]("http://www.ubuntuvibes.com/2012/04/hibernation-disabled-by-default-in.html") and the "bugs" [here]("https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/812394") and [here]("https://bugs.launchpad.net/ubuntu/+source/kde-systemsettings/+bug/976654").

For me, this decision is one of the WTF moments of the year, but the  ubuntu devs seem set on watering down ubuntu, and unfortunately that  path also breaks kubuntu, xubuntu and all the other derivatives.

---

### Post by Lemuriano on 2012-04-23
Thanks for clarifying. The ability to hibernate comes handy in my systems and is used every single day. Also will try to follow your links so I get it to work on the HTPC that is running Xubuntu 12.04.

I´m sorry to said that regarding choice and customization, Ubuntu and Gnome3 are working hard on trying to prevent users to make their own decisions on how to run our systems. 

One of the things that attract me to Gnu/Linux is the fact that we freely choose what we want, and when I try to look forward in time let said 10 years from now, what I see in that future environment at least in Ubuntu, is the lack of that freedom. 



Regards.

---

### Post by sfang on 2012-05-02
Thanks, jbernardo. I don't keep up with the news, so wasn't aware of this "feature".

Followed these [setps]("https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html") and I now hibernation is working properly.

---

### Post by GOwin on 2012-05-05
Hibernate works fine in 10.04, my last version installed in this computer. Now it doesn't work, even after following this page: [https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html)

Any idea who got this working?

---

### Post by linuxmatt7 on 2012-05-05
Most likely you downloaded the beta to beat the crowds to avoid slow specs when updating to Xubuntu 12.04.
Now I recommend that you update to the final version this way it might fix your problem. If not you can go into settings under power management and enable Hibernate and Sleep mode. This is what I had to do on my Xubntu 12.04 LTS Laptop.

---


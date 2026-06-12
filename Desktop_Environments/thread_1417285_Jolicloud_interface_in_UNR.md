---
title: "Jolicloud interface in UNR"
date: 2010-02-27
forum: Desktop Environments
---

### Post by emulator-guy on 2010-02-27
I tried jolicloud, loved the netbook-launcher settings, but didn't think much of the OS after that.
 I am still using jolicloud for now.
 My question is, is there a way to make the Ubuntu Netbook Remix launcher look like that of jolicloud?
 Do I add the jolicloud repository and install jolicloud-netbook-config?
 Do I find the config file and replace the existing one?
 Is it impossible?

 I tried finding the config files but only found the artwork for the launcher.](*,)

  Thanks in advance.:wink:

PS this is the jolicloud interface:
[http://img695.imageshack.us/img695/2333/screenshotfz.png](http://img695.imageshack.us/img695/2333/screenshotfz.png)
And the UNR:
[http://img651.imageshack.us/img651/4686/screenshot0a.png](http://img651.imageshack.us/img651/4686/screenshot0a.png)

---

### Post by mantisdolphin on 2010-03-08
How do I get the Jolicloud launcher back after it has, somehow, been lost?  I just have a desktop with a couple of launchers on it, a blue house in the upper left corner and the usual items (dropbox icon, wifi agent, battery indicator, volume control, etc.), in the upper left panel.

thanks!

---

### Post by mikewhatever on 2010-03-08
> **mantisdolphin said:**
> How do I get the Jolicloud launcher back after it has, somehow, been lost?  I just have a desktop with a couple of launchers on it, a blue house in the upper left corner and the usual items (dropbox icon, wifi agent, battery indicator, volume control, etc.), in the upper left panel.

thanks!

A reboot might fix it, and if not, press **alt+f2**, and type **netbook-launcher** to launch it manually.
Although JoliCloud is base on Ubuntu (Jaunty, I guess), it might not be the same. What I am driving at is, you might get better help at the JoliCloud's own forums, rather then here.
Last but not least, start you own thread, instead of hijacking another.

---

### Post by ascariz on 2010-07-15
try this...
edit /etc/apt/sources.list and add the  following:
  deb [http://apt.jolicloud.org](http://apt.jolicloud.org) robby main directory jolicloud
deb-src [http://apt.jolicloud.org](http://apt.jolicloud.org) robby main directory jolicloud
 run these commands.
  sudo aptitude update
sudo aptitude install -R jolicloud-poulsbo
sudo aptitude install -R linux-image-jolicloud linux-image-jolicloud-atom
sudo /etc/jolicloud-netbook-config.d/poulsbo.sh

let me know if works..

---


---
title: "I want to try a minimal install."
date: 2009-05-12
forum: General Help
---

### Post by AllRadioisDead on 2009-05-12
Hi, I would like to try a minimal install and build my system from the ground up. I have the Debian installer, and the Ubuntu installer.
My questions are:
1. What is the difference between the two? I know one is Debian, and one is Ubuntu, but at such a basic level what differences can I expect?
2. Will my wireless work right out of the box? I have a D-Link WDA-2320. If not, how can I enable it? 

Thank you!

---

### Post by bodhi.zazen on 2009-05-12
A minimal install is a minimal install, you will not see much difference between Debian and Ubuntu.

What did you do to enable your wireless in Ubuntu ? If it worked out of the box it will likely work with a minimal install.

---

### Post by AllRadioisDead on 2009-05-12
> **bodhi.zazen said:**
> A minimal install is a minimal install, you will not see much difference between Debian and Ubuntu.

What did you do to enable your wireless in Ubuntu ? If it worked out of the box it will likely work with a minimal install.
Thank you.
I will probably go with Debian then.  My wireless worked right out of the box in Ubuntu, however I had to enable it via the network manager applet. Isn't the minimal install command line only? If I'm at a command line, and I want to install packages, will my wireless "just work"?

---

### Post by bodhi.zazen on 2009-05-12
I do not know =)

You may need to learn iwconfig :twisted:

---

### Post by kerry_s on 2009-05-12
try them both, start with debian testing it's more up to date than lenny:
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/)

that's the net installer, it can install all 4 desktops or server, uncheck everything for the base. i just did a debian base+xfce4 before that i had gnome, the thing i noticed the most is the move to policykit is a little incomplete, for example with gnome i had to add policykit-gnome, i had add to the policykit.conf in xfce4 to use the logout options, i think cause i'm not using a login manager, not sure if you would have to do that on a full install, i'll try a full xfce4 install later.

when doing the minimal install, make sure you do xorg first.
"apt-get install xorg" it will save you a lot of headaches down the line. 

have you decided what you was going to use for your minimal? desktop or window manager.

---

### Post by kerry_s on 2009-05-12
> **ihermit said:**
> Thank you.
I will probably go with Debian then.  My wireless worked right out of the box in Ubuntu, however I had to enable it via the network manager applet. Isn't the minimal install command line only? If I'm at a command line, and I want to install packages, will my wireless "just work"?

i very much doubt it, you have to configure it.
i suggest a hardwire for the net install till you get to the de/wm point.
you can try though it will ask you if it sees it, at least it did on mine, but i didn't have the firmware yet so it failed, mine uses the zd1211rw-firmware.

---

### Post by AllRadioisDead on 2009-05-12
Thanks for the reply.
I will be using a window manager, debating between openbox and awesomewm.

---

### Post by AllRadioisDead on 2009-05-12
Where can I find a guide to setting up wireless via iwconfig?

---

### Post by bodhi.zazen on 2009-05-12
> **ihermit said:**
> Where can I find a guide to setting up wireless via iwconfig?

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

don't let that post fool you, it is not really *that* hard, lol

---

### Post by AllRadioisDead on 2009-05-12
Great, that helps alot. So essentially, it's just:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
```Where "ESSID_IN_QUOTES" is my network name, and <interface> is the interface name?

---

### Post by kerry_s on 2009-05-12
if you go with openbox, you might want to try the lxde desktop on the installer, if you do it from the base> apt-get install xorg lxde

---


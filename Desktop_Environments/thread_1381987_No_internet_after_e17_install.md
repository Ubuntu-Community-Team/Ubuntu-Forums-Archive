---
title: "No internet after e17 install"
date: 2010-01-15
forum: Desktop Environments
---

### Post by Rule2 on 2010-01-15
Hi all,
I have just installed e17 on ubuntu karmic and i have found that the internet stopped working. I tried the commands sudo ifconfig eth0 up, it asks for my password and then nothing. But when I try sudo ifconfig wlan0 up, it is showing unknown error.
I am using an HP Pavilion dv6 with core 2 duo, if it helps. BTW, right after the packages downloaded for the installation, the internet connection got disconnected because of an unexpected power outage.
Thanks in advance.

---

### Post by Brandon Williams on 2010-01-15
Prior to running e17, were you using network-manager to manage your internet connectivity? If so, then the interfaces won't be defined in your /etc/network/interfaces file, so ifup/ifdown won't work.

If they _are_ defined in /etc/network/interfaces, then that won't be the problem ... but e17 shouldn't be the problem either. What does your /etc/network/interfaces file look like (sanitized for public posting, of course)?

---

### Post by Rule2 on 2010-01-16
I have only these 2 lines in the above mentioned file
   [FONT=&quot]auto lo
iface lo inet loopback
It looks like I am in serious trouble because the network-admin and network manager applet packages are not installed, when I checked.[/FONT]
[FONT=&quot]Also,my NTFS filesystem is automounted at start, it was not like that before.
[/FONT]

---

### Post by Brandon Williams on 2010-01-16
Did you see [this thread](http://ubuntuforums.org/showthread.php?t=1350575)? or [this one](http://ubuntuforums.org/showthread.php?t=1280189)? They both have some amount of discussion related to networking. It looks like a lot of people use wicd, some use network-manager, and a few use the e17 native app exalt.

If you can't get any of those to work, then you'll need to modify your /etc/network/interfaces file so that it will auto configure your wireless interface at startup. I suggest you try the other methods, and if they don't work out for you, the read [this out-of-date document](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) to get started figuring out how to do it with /etc/network/interfaces.

---

### Post by Brandon Williams on 2010-01-16
For exalt, if you installed from [these instructions](http://wiki.enlightenment.org/index.php/E17_on_Ubuntu), then just 'sudo apt-get install emodule-exalt'.

---

### Post by Rule2 on 2010-01-16
I did use the emodules-all as mentioned in one of them, and there is no internet connection. So, install exalt may not work.

---

### Post by Brandon Williams on 2010-01-16
Exalt is there, but I couldn't figure out how to get it to work. I was easily able to get nm-applet to work, though.

After installing network-manager and network-manager-gnome, reboot, login to your Enlightenment session, and start nm-applet from the command line. Make sure that you have the systray module loaded and displayed in your shelf so that you can see the nm-applet systray icon. You should be able to click on the icon in the systray to get a listing of wireless networks, just as you would in any other desktop environment.

If this works, then you just need to set up nm-applet as a startup application.

---

### Post by Rule2 on 2010-01-20
Thanks, this is working. I separately downloaded the files, and restarted, wired and wireless netwoorks started working.
Thanks.

---


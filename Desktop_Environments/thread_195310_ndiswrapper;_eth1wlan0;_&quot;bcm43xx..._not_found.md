---
title: "ndiswrapper; eth1/wlan0; &quot;bcm43xx... not found&quot;"
date: 2006-06-12
forum: Desktop Environments
---

### Post by Airjoe on 2006-06-12
I threw a copy of Dapper Drake on an old box. I set up ndiswrapper; it tells me my hardware and driver are present. Originally, upon doing "iwconfig", it listed my device as "eth1". I changed this by editing etc/iftab. However, things such as "iwlist wlan0 scan" still don't work. It says "Interface doesn't support scanning: no such device". dhclient wlan0 doesn't work. I just get "network is down".

It's a linksys WMP54G. In dmesg, there's a lot of "bcm43xx: Error: Microcode 'bcm43xx_microcode5.fw' not available or load failed". Does this have anything to do with it?

Thanks!

---

### Post by danns on 2006-06-12
My experience has show, and I have found in these forums also, that you should add the bcm43xx module to the /etc/modprobe.d/blacklist file.  Using a text editor, as an administrator, simply add this to the end of the file:

blacklist bcm43xx

or run this in a terminal:

sudo echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist

Be very careful with the latter command, make sure you use ">>" and not ">" as you will over write your blacklist file, and you don't want to do that.

After that change has been made, it is easiest to just reboot the system.  Your card should work better at that point.

The bcm43xx module does not seem to work with ndiswrapper.

---

### Post by Airjoe on 2006-06-12
Eek! I did that and now Kubuntu gets stuck on bootup at "Configuring Network Interfaces..."!

I don't believe I did anything wrong. Is there some way to get around this or will I have to format/reinstall?

---

### Post by Furry_Fighter_20x66 on 2006-06-12
hit Ctrl-C when it pops up while booting and it will not wait to timeout. You can setup your network once you login.

---


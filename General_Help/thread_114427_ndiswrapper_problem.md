---
title: "ndiswrapper problem"
date: 2006-01-08
forum: General Help
---

### Post by enderv on 2006-01-08
Hi,
I've managed to get my video card going, so I thought I'd try the harder thing with setting the WiFi... And it is proving to be so.
I have a USB 3Com device (3CRWE254G72), which doesn't seem to have a native driver (it's a prism I think but I couldn't find a USB prism driver anyway).

So I went, and at the ndiswrapper wiki found the driver I should use with ndiswrapper, downloaded it and followed the instructions. So far so good.

Unfortunately, after installing the driver with ndiswrapper, I still can't see the device in iwconfig :confused: 

I did (all sudo-ed):
ndiswraper -i ....inf
ndiswrapper -m
and rebooted. Nothing.
I now get:
:~/windriver$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

:~/windriver$ lsusb
Bus 002 Device 006: ID 0d7d:1900 Phison Electronics Corp.
Bus 002 Device 005: ID 0506:0a11 3Com Corp. 3CRWE254G72 802.11g Adapter
Bus 002 Device 001: ID 0000:0000

~$ ndiswrapper -l
Installed ndis drivers:
3c254g72        driver present, hardware present

The ndiswrapper is loaded, as both ndiswrapper -m and modprobe -l | grep ndiswrapper show...

Installing the *.sys drivers doesn't work, I get "invalid driver" or something like that.

Any/all help would be much appreciated.

While I'm at it, is there a way how to download the wpa_supplicant package outside ubuntu's package tools? I can access internet only through the wireless, so I'd have to dowload it to my win drive... 

Vlad

---

### Post by xxsiriusxburnxx on 2006-01-08
Now as for after you used ndiswrapper did you see that it was present with iwcofnig? or even checking your network? A couple things if you notice that you now have a wlan0 with present extensions, make sure you go into system/sys tools/ network settings, and activated the card create the settings such as it should list in range ssid's and set for dhcp. If then you notice it works still COMPLETELY shut down the computer, A very important step I did not find for a while in ndiswrappe documentation, for the most part if this works on the ubuntu load screen youll notice about 1/3 the way it gets stuck on configuring network settings, this sometimes takes a while even up to 5 min @ times I even notice it says it has failed, but after that, try to get on the net if not try something like GAIM. Dont use anything like wifi-radar for obtaining connection it will only freeze and you will have to log out. all I did to get this working for Ndiswrapper is as follows

ndiswrapper -i inffile
ndiswrapper -l "to check its present"
ndiswrapper -m
depmod -a "as read in some readme's"
modprobe ndiswrapper

and also seem as we were doing this on 2 laptops at the same time with different NIC cards one broadcom and one belkin, we noticed that on my laptop after using ndiswrapper it showed about 2 lines saying it was adding the info, on the second laptop we had tried 3 sets of drivers what we though to be the origional drivers for the belkin uses same as broadcom, then tried rt2500, and finally just used the same inf and sys file used by my laptops card and it worked fine

of course all with sudo access
Good Luck

---

### Post by enderv on 2006-01-10
[QUOTE=xxsiriusxburnxx]Now as for after you used ndiswrapper did you see that it was present with iwcofnig? 
[/quote]
it's not. See the output of iwconfig in my original post. :(
ndiswrapper says that the driver is installed, and hw present, modprobe shows ndiswrapper.ko loaded, ndiswrapper is in /etc/modules, but I still cannot see the interface.
So I don't even get to the point where I'd have wan0 or anything like that.. 

Is there any way how to get a debug output out of ndiswrapper?

V.

---

### Post by healychan on 2006-01-10
When you install a driver with ndiswrapper, you need both .inf and .sys file in the same directory. You need to install just the .inf file.

---

### Post by enderv on 2006-01-10
[QUOTE=healychan]When you install a driver with ndiswrapper, you need both .inf and .sys file in the same directory. You need to install just the .inf file.[/QUOTE]
Yep, that's what I did. 

If I even try to install the sys file, it will complain about invalid driver anyway (tried that in desperation too).

V.

---

### Post by healychan on 2006-01-10
Please do this.
```
sudo modprobe ndiswrapper
```
It will alias the wlan0 with ndiswrapper you installed.
Please let me know if it work!! Thx;)

---

### Post by enderv on 2006-01-11
[QUOTE=healychan]Please do this.
```
sudo modprobe ndiswrapper
```
It will alias the wlan0 with ndiswrapper you installed.
Please let me know if it work!! Thx;)[/QUOTE]

That has been all done when I had the problem :).

I found the problem/solution though! Hurrah.. 

The problem was with the ndiswrapper that comes with breezy (1.1) - it failed to talk to the card for some reason.
The was shown as loaded, but dmesg (doh, should have checked it earlier - the module being shown as loaded confused me...) showed that it failed to init the card.

Taking in a new version of ndiswrapper (1.7) helped, although I still can't get it going from automagically (it works for manual ifup/ifdown), and at shutdown the computer freezes (blank screen, monitor in power saving mode, no keyboard response, have to turn the main power switch off). 

V.

---

### Post by healychan on 2006-01-11
[QUOTE=enderv]Taking in a new version of ndiswrapper (1.7) helped, although I still can't get it going from automagically (it works for manual ifup/ifdown), and at shutdown the computer freezes (blank screen, monitor in power saving mode, no keyboard response, have to turn the main power switch off). 

V.[/QUOTE]
Surely shutdown by pressing power button is not a good idea. It may damage the filesystem and some device. NEVER NEVER do that. You should solve your problem as soon as possible if you cannot shutdown in a usual way.

---

### Post by enderv on 2006-01-11
[QUOTE=healychan]Surely shutdown by pressing power button is not a good idea. It may damage the filesystem and some device. NEVER NEVER do that. You should solve your problem as soon as possible if you cannot shutdown in a usual way.[/QUOTE]

You're right, it's not - but then, I don't have any real data on that partition, and I know now how to install the things I had problems with :).

I will have to figure why it's shutting down as it is, the bit of a problem is that I will have to use logs only (or maybe not boot to Gnome?), as it really just switches the videocard. It will probable take a few hard switches before I figure it out, but then I will (finally! :cool: ) have it all running and will be able double boot (hopefully with Win just for games).

V.

---


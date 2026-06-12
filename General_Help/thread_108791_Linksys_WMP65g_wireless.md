---
title: "Linksys WMP65g wireless"
date: 2005-12-27
forum: General Help
---

### Post by icksa on 2005-12-27
Hello:
I just bought a linksys wmp54g wireless card and installed it in my computer. Ubuntu is able to detect the card fine, but when I go to the network settings to try and activate the card my computer crashes (completely hangs, no keyboard/mouse response).

I tried setting the ssid using the terminal with iwconfig, and that worked fine, however when I tried to use ifconfig as so:

ifconfig ra0 up

I had the same response...any suggestions?

Thanks

---

### Post by icksa on 2005-12-27
If there isnt a solution to get the rt2500 driver working...can someone tell me how to remove the preinstalled driver?

I was thinking of trying ndiswrapper to see if there is any difference...

Thanks

---

### Post by icksa on 2005-12-27
I tried to stop using the rt2500 driver that comes with ubuntu, by just moving it to a different file name, which seems to keep it from loading...

But now I can't get ndiswrapper to work, when I install the windows driver, and try:

modprobe ndiswrapper

It just sits there, and never finishes running modprobe. If I type lsmod, it shows ndiswrapper, but dmesg says that there was a problem loading the ndiswrapper module.

Can somebody please help me...or tell me if this is hopeless, so I can try another distro

Thanks

---

### Post by Red Sand on 2006-01-08
I bought the same card (after looking at the hardware compatibility list first ;) ) and am having the same problem can you tell me how you fixed it?

---

### Post by kg6gfq on 2006-01-16
Yet another person over here having the same problem.  I've tried disabling SMP and PREEMPT, which are said to be problematic and often the cause of that, but to no avail.  Anyone with advice would be greatly appreciated!!

---

### Post by icksa on 2006-04-05
Hi:
Never managed to fix this problem. I was setting up a different card in gentoo that had this same problem...and found that using 4k kernel stack size was the problem. But I was using NDISWRAPPER for that card....

Anyway, I have no idea how to recompile the kernel in ubuntu yet, and dont even have access to the computer with the wmp54g card, but I was wondering if someone with this same card/problem could try changing the kernel stack size to 8K to see if it fixes anything, its a long shot, but I'm out of ideas, and have seen lots of other people with the same problem...

In anycase, if this doesnt work and there is no solution, is there anywhere I can file a bug report? What makes this situation worse, is that A LOT of people reccommend this card to others...

Thanks

---

### Post by SleepyHollow on 2006-04-05
Hi folks,

I'm using this script with breezy 5.10 Ubuntu, no probs. Only: You have to use the commands for the initialisation twice (therefore two "loops"), don't know why. I made it simple and copied the lines.

I changed nothing in Ubuntu. It works out of the box with this script. Don't use the network-gui. The gui doesn't work. This setting is for WPA with AES and DHCP. The passphrase must be in ascii-text. I don't like it but only this way works for me. Don't know why too.

<code>
#!/bin/sh
echo "WMP54G with rt2500-Driver"
ifconfig ra0 up
echo "network is starting"

iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=AES
iwpriv ra0 set WPAPSK="mypasswd"
iwpriv ra0 set SSID="myssid"

echo "First loop: waiting for connection"
sleep 5
dhclient -q ra0
iwlist scanning

echo "WMP54G with rt2500-Treiber"
ifconfig ra0 up
echo "network is starting"

iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=AES
iwpriv ra0 set WPAPSK="mypasswd"
iwpriv ra0 set SSID="myssid"

echo "Second loop: waiting for connection"
sleep 5
dhclient -q ra0
iwlist scanning
</code>

---

### Post by SleepyHollow on 2006-04-13
no posts anymore, after one week. It seems to help.

Maybe someone should put it to a howto.

:mrgreen:

---

### Post by Herodotus on 2006-07-08
Could you please explain where to put or save this script and how to set it up to run at boot?

Thank you.

---


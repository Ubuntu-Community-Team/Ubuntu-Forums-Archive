---
title: "wireless not working on my dell laptop"
date: 2010-03-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lavy on 2010-03-06
Hi,

I bout a Dell with Ubuntu. I've installed a newer version OS Kubuntu 9.10.
When I open the KDE Control Module It doesn't recognize my wireless ( the wireless tab is disabled). I tried to activate the wireless using the keyboard shortcuts, but that didn't helped.

I mention that the wireless was working fine when I bought the laptop. The wired connection works. Another thing I've inserted a Kununtu live CD (the same I've installed) and it noticed that I need wireless drivers so I typed:
$lspci | grep Broadcom
 Output: 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Then I tried to install the drivers:
$sudo apt-get install b43-fwcutter.

That didn't work.
So how can I enable my wireless?
Tx

---

### Post by vprajapati on 2010-03-06
> **lavy said:**
> Hi,

I bout a Dell with Ubuntu. I've installed a newer version OS Kubuntu 9.10.
When I open the KDE Control Module It doesn't recognize my wireless ( the wireless tab is disabled). I tried to activate the wireless using the keyboard shortcuts, but that didn't helped.

I mention that the wireless was working fine when I bought the laptop. The wired connection works. Another thing I've inserted a Kununtu live CD (the same I've installed) and it noticed that I need wireless drivers so I typed:
$lspci | grep Broadcom
 Output: 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Then I tried to install the drivers:
$sudo apt-get install b43-fwcutter.



That didn't work.
So how can I enable my wireless?
Tx




Hi,
go to system>admin>hardwre drivers
u will find the wireless driver
activate and restart the machine
if this seems to not work try sudo linux-backport-modules-(ur linux kernel)
after that restart the machine

Vijay Parajapati
Gemstone Acer,
3 gb ram, 2 ghz
[IMG]http://ubuntuforums.org/images/icons/icon12.gif[/IMG]

---

### Post by mikewhatever on 2010-03-06
It's a known issue, hope it's OK that I just googled the solution for you.;)

[http://lmgtfy.com/?q=karmic+BCM4312](http://lmgtfy.com/?q=karmic+BCM4312)

---

### Post by lavy on 2010-03-12
Thank you both, know it works.

---


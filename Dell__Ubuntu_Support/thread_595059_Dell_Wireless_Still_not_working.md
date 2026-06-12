---
title: "Dell Wireless Still not working"
date: 2007-10-28
forum: Dell  Ubuntu Support
---

### Post by zeroenna on 2007-10-28
Hi so i've tried everything from uninstalling ndiswrapper to re-installing, i've blacklisted the bcm43xx, i have my new drivers and i just can't get my wireless to work

---

### Post by ÜbuntuMensch on 2007-10-28
what card are you using?

My iinspiron came with the Dell 1390 wireless card. I dithered around with it for a couple of weeks, then got an Intel Pro/wireless 3945ABG for under $30 from one of the big named online retailers. Actually lifting the keyboard off the laptop and installing a new wireless card was easier than any of the solutions I found on the forums. And it worked the first time.

---

### Post by SeanBlader on 2007-10-29
ÜbuntuMensch I have the 1390 as well, and it's using the Broadcom BCM4306 chip. I didn't think a replacement wireless board was an option. I know exactly where to find it in my Inspiron 8500, and if the broadcom was replaceable I'd do it in a heartbeat. Any pictures of the box or model number of the wireless card, and what's your Inspiron model number?

---

### Post by saru411 on 2007-10-29
i have a vostro 1500 with a 1390 wireless card. this link installed my wireless card drivers([http://ubuntuforums.org/showthread.php?t=405990&highlight=1390](http://ubuntuforums.org/showthread.php?t=405990&highlight=1390))

it was as easy as point and click. the only isssue i have is that sometimes it does not want to connect to a wireless network eventhough it sees it. if i manually try to connect to a new network(i use other or abc as the name) then switch back to the real netowrk it connects just fine.

hope that helps

---

### Post by SeanBlader on 2007-10-30
> **saru411 said:**
> i have a vostro 1500 with a 1390 wireless card. this link installed my wireless card drivers([http://ubuntuforums.org/showthread.php?t=405990&highlight=1390](http://ubuntuforums.org/showthread.php?t=405990&highlight=1390))

it was as easy as point and click. the only isssue i have is that sometimes it does not want to connect to a wireless network eventhough it sees it. if i manually try to connect to a new network(i use other or abc as the name) then switch back to the real netowrk it connects just fine.

Didn't work in Gutsy I'm afraid.

---

### Post by saru411 on 2007-10-30
are you doing this on a fresh install? did you un-blacklist the card? i have done this on multiple machines with 1390 and i would think something you did previously has caused the issue. im not saying it did but i would try a fresh install and see where it got me. normally finding out where all of my previous errors were and then starting from a fresh install yields a perfectly running machine. thats my personal experience.

---

### Post by ~chinook~ on 2007-10-30
I have a broadcom on my Dell Vostro 1500. I just installed the restricted drivers and it worked fine.

---

### Post by ÜbuntuMensch on 2007-11-03
[QUOTE=SeanBlader;3662631]ÜbuntuMensch I have the 1390 as well, and it's using the Broadcom BCM4306 chip. I didn't think a replacement wireless board was an option. I know exactly where to find it in my Inspiron 8500, and if the broadcom was replaceable I'd do it in a heartbeat. Any pictures of the box or model number of the wireless card, and what's your Inspiron model number?[/QUOTE


I've got a 1420, and the 1390 Mini-PCI card is located under the keyboard. It's not such a difficult replacement. If you have a mini-pci card, I don't see why you wouldn't be able to get an Intel one rather than the Dell. But Googling it, I didn't immediately see a connection, or even really clearly what wireless cards were compatible with the 8500. But I guess the big thing is if you have a card or the WLAN is soldered to your motherboard. If the latter, then you've got a more ambitious project on your hands than I would undertake. If it's a card, then you're almost certainly going to be able to upgrade it.

---

### Post by Pichie on 2007-11-04
I just followed the instructions I found on one of the forums. It worked like a charm on my Dell Inspiron 1520 with a 1390 Mini-PCI card.
Here is the link: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by Mud.Knee.Havoc on 2007-11-07
When trying to get your wireless to work, it's easiest to remove all of the fancy stuff like WPA, WEP, etc.  Just open it right up. :)  This will ensure that the problem isn't related to authentication.

Also, if you've got a little WIFI light on your laptop, it'll turn on when your card is recognized.  If you see this light, but still can't connect, it's usually a password/setting-of-some-sort problem.  If you can't see the light, you've got to take other steps - Gutsy makes it a one or two click affair now with the BCM43xx.

---


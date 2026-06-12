---
title: "Lightest weight flavor for old Asus Netbook"
date: 2016-04-10
forum: Desktop Environments
---

### Post by Odyssey1942 on 2016-04-10
I have an Asus Netbook (Atom processor 1 GB RAM) on which I installed Lubuntu 12.04 some time ago, but don't use much partly because, if I remember correctly it is a bit slow, and partly because I didn't use it enough to get familiar with Lubuntu.

Having opened it to play around, I decided to upgrade to Lubuntu 14.04 on a bit of a whim while I was doing an update. 12,04 is a bit long in the tooth so it seemed a reasonable thing to do. It is taking a very long time to upgrade however and this makes me think about the best flavor of Ubuntu to put on this rather underpowered device.

I have recently put Ubuntu Mate on a not-current desktop and it runs very well indeed. So I am asking first if UM is more resource hungry than Lubuntu, and secondly what would you recommend for this little netbook.

Edit: Forgot to add that I do not want any type of Unity (which is probably way too resource intensive anyway). Strongly prefer old Gnome 2 desktop.

---

### Post by him610 on 2016-04-10
Hello Odyssey1942. 
I have a similar netbook, though mine is an Acer, that I run 32bit Chromixium on reasonably well, after all it's an early Atom.  I still use it as my travel machine. The guy who is the lead developer has since rebranded the distro name to Cub Linux after receiving some correspondence from the company with a similar product name.  
Cub Linux is in its release candidate phase. It is a lightweight distribution based on the Ubuntu 14.04 repositories. You might want to give it a try.
Here is the link to the download site.
[https://cublinux.com/download/#]("https://cublinux.com/download/#")

---

### Post by kurt18947 on 2016-04-10
I've installed LXLE which uses Lubuntu as a  base on a core2duo notebook. It works quite well but if you prefer the gnome2 vibe MATE is going to be hard to beat. I had an issue with a USB device on Ubuntu-Mate 15.10 that I didn't have with Xubuntu15.10. I'm not sure if that was bad luck or an issue with Ubuntu-Mate.

---

### Post by Odyssey1942 on 2016-04-11
hgh9mrp, thanks. Perhaps not coincidentally, I had planned to ask about ChromiumOS if no one mentioned it. As a result of yours, have done a bit of reading about Cub and have yet to figure out exactly what the ChromiumOS/Ubuntu element or commonalities are, but it sure looks interesting. Edit: in [http://ubuntuforums.org/showthread.php?t=2244889&page=3&highlight=Cub+Linux]("http://ubuntuforums.org/showthread.php?t=2244889&page=3&highlight=Cub+Linux"), there is mention of a "Dock" Cub does not have a Unity type GUI does it?

kurt18947, thanks. I am very happy with Ubuntu Mate 14.04, but plan to upgrade very soon to an "official" flavour of UM, probably 15.10 then 16.04 for an LTS version which will keep me working productively for years. Which versions of UM have you used, and if either 14.04 or 14.10 AND  15.04 (which I believe is the first "official" versions or 15.10, how would you summarize the differences (hopefully improvements in the later versions) between them? Which version would you recommend for this 1GB/old Atom machine?

I think I need to add 1GB or 3GB of RAM if it is cheap enough. Anyone done this?

---

### Post by Jon_Thomas on 2016-04-12
> **Odyssey1942 said:**
> hgh9mrp, thanks. Perhaps not coincidentally, I had planned to ask about ChromiumOS if no one mentioned it. As a result of yours, have done a bit of reading about Cub and have yet to figure out exactly what the ChromiumOS/Ubuntu element or commonalities are, but it sure looks interesting. Edit: in [http://ubuntuforums.org/showthread.php?t=2244889&page=3&highlight=Cub+Linux](http://ubuntuforums.org/showthread.php?t=2244889&page=3&highlight=Cub+Linux), there is mention of a "Dock" Cub does not have a Unity type GUI does it?

kurt18947, thanks. I am very happy with Ubuntu Mate 14.04, but plan to upgrade very soon to an "official" flavour of UM, probably 15.10 then 16.04 for an LTS version which will keep me working productively for years. Which versions of UM have you used, and if either 14.04 or 14.10 AND  15.04 (which I believe is the first "official" versions or 15.10, how would you summarize the differences (hopefully improvements in the later versions) between them? Which version would you recommend for this 1GB/old Atom machine?

I think I need to add 1GB or 3GB of RAM if it is cheap enough. Anyone done this?

I have an eMachines E-250, made by Acer for eMachines.  I had the same specs originally as your system (Atom, 1GB of RAM).  I had been running Crunch Bang Linux for a number of years, then decided to try Ubuntu Mate 16.04 Beta on it.  So far it works quite well.  

One thing I did was to install a 256Gb Toshiba solid state drive in place of the original 160Gb rotating drive. Caught the SSD on sale at BestBuy for like $59.00. Makes a BIG difference for disk I/O's to help that older Atom processor. Another thing to keep in mind is most Atom chip sets of that age were only able to use 2Gb RAM maximum. It was a condition from Microsoft to let them use Windows 7 Starter with the Intel Atoms. Might be something you want to check out.

Hope this helps.

---

### Post by Odyssey1942 on 2016-04-13
Very helpful indeed and confirms exactly what I was thinking about (i.e., a SSD). Did you increase your ram and if so, was it a fairly easy addition? In any case would this be ordinary sodimm?

---

### Post by kurt18947 on 2016-04-14
I'm not familiar with the Asus netbook. The HP Mini 1000 I had accepted a 2nd standard SODIMM Maximum 1 GB for a total of 2 GB like Jon_Thomas' machine. The hard drive was a different story on the HP. It was a internal 1.8" PATA using a ZIF cable connector rather than the 'slide it into a bay' hard drive. I could have gotten an SSD that would have worked but decided to sell the machine instead. Something to check into before purchasing an SSD.

---

### Post by Jon_Thomas on 2016-04-14
Yes, my system had two SODIMM slots like kurt18947 mentions above, if I remember right. Been a while since I swapped them out.  Added an additional 1Gb stick, which made a LOT of difference.

kir18947 is right about the SSD.  Open you system up and verify whether a it's a 2.5" SATA drive like mine or a 1.8" PATA drive like his was.  2.5" SATA drives you can get at about any computer store.  PATA drives are a lot less common now compared to a few years ago.

Biggest thing I have to deal with is heat buildup.  Linux takes some tuning to get cooling fans working on Acer netbooks.  It has to do with the bios used.  Read up on acpi, lm-sensors, and fan-control programs for configuring power  and fan management on Atom processors.

---

### Post by Bucky Ball on 2016-04-14
Lubuntu-core is an option. [Xubuntu-core]("http://xubuntu.org/news/introducing-xubuntu-core/") may also work. I use the latter for all my installs now. Both are even lighter than their relations. All the basics are there, desktop environment and file manager, etc., you add everything else like web browser, email client, so you can make it light or heavy.

---

### Post by Jon_Thomas on 2016-04-14
> **Bucky Ball said:**
> Lubuntu-core is an option. [Xubuntu-core]("http://xubuntu.org/news/introducing-xubuntu-core/") may also work. I use the latter for all my installs now. Both are even lighter than their relations. All the basics are there, desktop environment and file manager, etc., you add everything else like web browser, email client, so you can make it light or heavy.

Hmmm, haven't seen those before. May have to check them out. Thanks for the info.

---

### Post by Bucky Ball on 2016-04-14
> **Jon_Thomas said:**
> Hmmm, haven't seen those before. May have to check them out. Thanks for the info.

Just do a web search for Lubuntu-core and you'll find it. I think you choose it as a machine profile during the tasksel section of a Ubuntu minimal install. I believe Xubuntu-core can be selected and installed the same way but the 15.10 and 16.04 LTS ISO images are available from a link on the link I posted earlier for Xubuntu-core which can be installed in the regular way(s), via USB or disk.

---

### Post by him610 on 2016-04-14
> Cub does not have a Unity type GUI does it?
No, but it does have a dock at the bottom of the display. I will see if I can attach a screenshot. (
Haven't done this so it may take a couple of tries. 
[ATTACH=CONFIG]268386[/ATTACH]

---


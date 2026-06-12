---
title: "Dell XPS 15 Nvidia proprietary driver error."
date: 2011-02-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by blazerin05 on 2011-02-05
I've been using ubuntu for nearly 5 years now on my old Dell 600M and loving it, I finally got a new laptop today and ran into a HUGE problem. I now have a Dell XPS 15 with the Nvidia GeForce 420 card with optimus. I ran the usual install song and dance (64 bit iso burned onto a disc, boot from disc select install, click, click etc). The install finished and I rebooted into a nice fresh ubuntu install. Shortly after a notification told me I needed to activate proprietary drivers for my nvidia card for it to work properly. I followed the instructions and rebooted as suggested. After the reboot, ubuntu booted into COMMAND LINE ONLY! I have little knowledge of working with bash commands and the only thing I could think of was to try and run firefox (probably a dumb idea but I panicked). I typed in the command and it gave me an error indicating that there was no display. Thinking I had made some huge mistake on the way I wiped the partition and reinstalled, only to get the same error after installing the prop driver. I've read that there are some issues with the 420m in linux, so my questions are...

1. Is there a way to fix the install I have now or is a reinstall my best option (haven't done any configuring or anything it's an otherwise clean install)

2. Is there another driver for the 420m that won't give me the same problem?

3. If I don't install the prop driver what will I be missing?

P.s. I'm writing this from my Windows 7 partition and I'm feeling the linux withdrawl starting already help fast please!

---

### Post by Teg_Navanis on 2011-02-05
Nvidia doesn't support Optimus under Linux. For the new XPS systems with Optimus (i5 processors), this means that the Nvidia card doesn't work at all: [http://ubuntuforums.org/showthread.php?t=1645074]("http://ubuntuforums.org/showthread.php?t=1645074")

The Intel chip is fine for most purposes. For me, the biggest drawback is that HDMI output is unsupported under Linux. DisplayPort works, however.

---

### Post by svast on 2011-02-06
For HDMI output, did you consider using a mini-DisplayPort to HDMI adapter?

---

### Post by rasos on 2011-10-26
The ubuntu community is now providing a suitable driver for NVIDIA optimus :)

To download, add the following repository:
> **[B]ppa:mj-casalogic/ironhide**[/B]reload all repositories:
> sudo apt-get updateinstall the driver:
> sudo apt-get install ironhideYou will be guided through the configuration. Select a template, then choose XV. 

Find all packages here: [https://launchpad.net/~mj-casalogic/+archive/ironhide/+packages]("https://launchpad.net/%7Emj-casalogic/+archive/ironhide/+packages")

--rasos

---

### Post by moldaviax on 2011-10-28
thanks rasos I had missed ironhide

:)

M.

---


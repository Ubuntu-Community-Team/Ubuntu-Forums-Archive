---
title: "installing???"
date: 2009-04-23
forum: General Help
---

### Post by bahawks2 on 2009-04-23
Hey I was wondering if I install ubuntu will it run? I am only asking this because I can't get the live sessions to work on my computer. I have tried using the CD that I made and the usb both with ubuntu 8.10. My computer has 2.67GHz intell CPU with 1 GB of ram and two hard drives one 40Gb and the other 19 GB. One CD drive and one DVD drive. I also have an external hard drive 250 GB. I also have a Nvidia PCI graphics card.

---

### Post by ddrichardson on 2009-04-23
Need more information to help - what doesn't work, does it get to a graphical interface or does it have any error messages?

---

### Post by kanikilu on 2009-04-23
When you boot from the CD, can you see if it works if you select safe graphics mode from the boot options?

Anyways, there's nothing about your computer specs that say it *shouldn't* work.

On a couple installs that I've done, I've had to use the Alternate CD, which uses a text-based installer...

eh...I just realize here that I'm *assuming* that it's a graphics problem, which it might not be. Can you describe in more detail what the problem is? Do you even get to the menu that asks if you want to try before installing, install, memtest, etc?

---

### Post by bahawks2 on 2009-04-23
Well I get error-110. So when I load up the CD/USB I select English and boot up a Live session. The bar bounces back and forth a bit and then starts to load. It loads about 1/10th of the way and then freezes. 

It also says things about splash error and something about probing error.
(sorry about the lacking of info not at home at the moment, also it has been a while since I have tried a live session)

---

### Post by ajgreeny on 2009-04-23
Make sure your install CD is a good one by using the check CD option in the menu that appears.  You can also check the iso file you downloaded for its md5 checksum to ensure that it is a good download.  If you only have windows available, I have no idea how to do that, but a google search will turn up the answer to that, I'm sure.  You can find the md5sums that you need [here]("https://help.ubuntu.com/community/UbuntuHashes").

---

### Post by bahawks2 on 2009-04-23
Well I know both work because I have tried both on other computers. But there was one wired thing that I noticed. When I did the memory test at about 75% of the way through the computer just shut off.

---

### Post by ddrichardson on 2009-04-23
> **bahawks2 said:**
> Well I know both work because I have tried both on other computers. But there was one wired thing that I noticed. When I did the memory test at about 75% of the way through the computer just shut off.
On the currently installed OS do you experience any problems, if its Windows I'm thinking BSOD and random resets?

---

### Post by bahawks2 on 2009-04-23
Well some times when I go to boot up my computer it will freeze up, but that is only if I turn the computer off and try and boot it back up again like 10-20 min after I turned it off. That is just with my windows xp home ed OS. Maybe it is my computers hardware or something. I am planning on getting a laptop some time soon. I am just tired with windows.

---

### Post by ddrichardson on 2009-04-23
It could be a memory failure - if you have two sticks of memory fitted, transpose them and run the test again, if it fails earlier then you've a bad stick.

It sounds more like overheating though, check the obvious - like cabling getting spaghetti like and blocking vents, dust build up and positioning for best air flow.

---

### Post by bahawks2 on 2009-04-23
> **ddrichardson said:**
> It could be a memory failure - if you have two sticks of memory fitted, transpose them and run the test again, if it fails earlier then you've a bad stick.
So by transpose them you mean switch there places?
Ok i will give it a try and give an update after the trial.

---

### Post by bahawks2 on 2009-04-24
all right so i tried switching up the ram also tried safe graphics mod but no sucsses.
I have attached photos of errors and how far my ubuntu loads.

---

### Post by ddrichardson on 2009-04-24
There were a handful of bugs in 8.04-8.10 that could exit with this message, can you try an 9.04 disc?

---


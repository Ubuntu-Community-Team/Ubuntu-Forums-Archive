---
title: "Can't log in from Hibernation status"
date: 2011-03-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mingkai.hu on 2011-03-14
DELL latitude d630 laptop with Ubuntu 10.04.

When power on the laptop from Hibernation status, the mouse and the keyboard don't work, so I have to push the power button to power down the laptop. When I power up it again and input the password, it will return to the login dialog again. but I can log in to the command line mode under recovery mode. I suspect the hibernation status don't remove because I powered down the laptop directly.

So I want to log in to the command line mode to remove the hibernation status, cant I? If yes, where can I find the hibernation status info? Thanks in advance.

---

### Post by Niedzwiedz on 2011-03-16
I really not have an answer, maybe a guess. As I was browsing, I seen no one respond.
I think you need a certain amount of Swap File for hibernation. It depends on the amount of RAM you have.
I have a Dell latitude 610, but, the RAM is like 1 GB, I would have to look to tell the truth, but, I run Puppy Linux on it and not have a swap or have tried to hibernate.
What you could try and I think it would work, depending on your RAM, close all programs and then; System > Adminisration > System Monitor > Resources; look at your memory and swap history??
My Memory now with FireFox and me typing and System Monitor open it using 302.8 MiB, just say 305 MiB (11% of avaliable RAM) so, I may be wrong, but, I thought to hibernate you would need at least 305 MiB of swap or really more like 500 MiB to be realistic, but, as my signature say, I not lie, but, I may not be telling the truth? Sorry.
But, knowing what your memory usage is, and knowing it below what your Swap File is, try hibernation and see if it work.

As far as removing, again I not have this, maybe because I did not make a Swap Partition??

This is a quick find for general information so be real sure it pertain to 10.04;
Why do I need swap?
Hibernation (suspend-to-disk) The hibernation feature (suspend-to-disk) writes out the contents of RAM to the swap partition before turning off the machine. Therefore, your swap partition should be at least as big as your RAM size. The hibernation implementation currently used in Ubuntu, swsusp, needs a swap or suspend partition. It cannot use a swap file on an active file system. 
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---


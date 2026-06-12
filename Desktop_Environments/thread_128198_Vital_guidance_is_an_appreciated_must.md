---
title: "Vital guidance is an appreciated must"
date: 2006-02-10
forum: Desktop Environments
---

### Post by anton123 on 2006-02-10
Hi,

I am considering building my own computer from scratch. Currently, I have an Athlon 64 3500+ with Asus Amberine M motherboard. When installing Ubuntu 5.10, 32 bit edition, the clock runs 2 to 3 times faster than normal and that affects nearly everything (sound plays too fast, frequent buffering for streaming media, etc) Looking on the forums, I acknowledged that other users with some Asus motherboards for Ahtlon 64 CPUs experience the same issue. I installed the the 64 bit edition and that clock symptom is gone but I have compatibility issues with some applications. For instance, xine 1.1.1 compiled by me on this platform, installs but too often quits some seconds after it starts to play a media file. There are several other issues with many programs also. Which leaves me to build my own system from scratch.
Here are the options I am looking at:

Option 1

Asus A7V880 motherboard
Athlon XP 3200+ CPU
1 GB Kingston RAM
300 GB Maxtor SATA hard drive
256 MB Asus GeForce 6200

Option 2

Asus A8V motherboard
Athlon 64 4000+ CPU
1 GB Kingston RAM
300 GB Maxtor SATA hard drive
256 MB Asus GeForce 6200

1) Which option do you trully recommend? Please, understand that we are talking about good $$$ here and I do not want to waste them on the option that will bring me again the double clock speed symptom when running Ubuntu 32 bit on a system with certain Asus motherboards and Athlon 64 CPU. Ubuntu 64 is out of question; too many issues with it. I will stick to Ubuntu 5.10 32 bit edition.
2) Who can attest from daily experiences that A7V880 for Athlon XP and A8V for Athlon 64 CPUs motherboards behave excellently with 32 bit editions of Ubuntu 5.10 even 5.04?
3) Is Athlon 64 4000+ processor compatible with Ubuntu 5.10 32 bit edition?
4) If both options are proven to be reliable, should I opt for Athlon XP/A7V880 of for Athlon 64/A8V?
5) Is Asus GeForce 6200 256 MB RAM video card a good choice since I consider installing Cedega to run some Windows games?

Thank you

---

### Post by cdhotfire on 2006-02-10
I can tell you AMD 64 is the best option, I have that motherboard, well sorta alike, and it works fine, but make sure when your gonna install Ubuntu and you pop in the cd and it shows "boot:" type in "linux noapic acpi=off", it will most likely freeze during install or when you log into Gnome. I don't know about the video card, but from what I have seen Nvidia is very well supported on Linux so you should have no problems.

---

### Post by anton123 on 2006-02-10
So, what exactly are you trying to say? You say that the motherboard works fine with Ubuntu 5.10 and yet, it does not unless one must type "linux noapic acpi=off" at boot prompt? Then how can it work fine? Also, you state that you have a motherboard similar to Asus A8V but I am interested specifically in Asus A8V and the interaction with the 32 bit version of Ubuntu 5.10

---

### Post by cdhotfire on 2006-02-10
[QUOTE=anton123]So, what exactly are you trying to say? You say that the motherboard works fine with Ubuntu 5.10 and yet, it does not unless one must type "linux noapic acpi=off" at boot prompt? Then how can it work fine? Also, you state that you have a motherboard similar to Asus A8V but I am interested specifically in Asus A8V and the interaction with the 32 bit version of Ubuntu 5.10[/QUOTE]

Like I said, it works fine with those options present, its a bug with the kernel I guess, because Im now using Arch Linux and I do not have to put these options.  Maybe you would not even need to because that motherboard is more recent than mine, all I was trying to get across, is that if you have any problems you should use those options.  But back to the point, you will get more out of your machine with an AMD 64, oppose to Athlon XP.

---

### Post by anton123 on 2006-02-11
Thank you. What does the community state with regard to what should be done  based on experience with both boards and CPUs?

---

### Post by anton123 on 2006-02-12
I have been thinking about an Asus A8V-E SE motherboard. If I recall well, I saw someone running Ubuntu 5.10 32 bit on a A8V model without the double clock symptom... but I might be mistaken. Is A8V-E SE motherboard with an AMD 64 or AMD 64 X2 free of this symptom? I don't want to waste my money if I will run  into the same problem I currently have with my Asus Amberine M motherboard. Again, Ubuntu 64 bit edition is out of question. Not quite ready yet.

---

### Post by cdhotfire on 2006-02-12
You might want to maybe wait for dapper, because their new kernel should fix this, like I said, im currently running Arch, and I do not have this problem.  But if I run Ubuntu with those options, everything runs fine, atleast till now.

---

### Post by anton123 on 2006-02-17
I just bought the Asus A8V-E SE motherboard. Has anyone attempted to run dapper alpha 3 32/64 bit or ubuntu 5.10 32/64 bit on this model? Is radeon x550 video card compatible with xorg 6.8.2/7.0? This is important people! I hope I have not wasted money. I was originally looking for an asus a7v880 motherboard with athlon xp 3200 but they are just absent from stores! I don't understand this.

Thank you

---

### Post by anton123 on 2006-02-17
I just bought the Asus A8V-E SE motherboard. Has anyone attempted to run dapper alpha 3 32/64 bit or ubuntu 5.10 32/64 bit on this model? Is radeon x550 video card compatible with xorg 6.8.2/7.0? This is important people! I hope I have not wasted money. I was originally looking for an asus a7v880 motherboard with athlon xp 3200 but they are just absent from stores! I don't understand this.

asus a8v has the Marvell 88E8001 Gigabit Ethernet Controller. I presume it is supported by ubuntu 5.10 32/64 bit since someone with the 32 bit version of ubuntu 5.10 was using such motherboard as that person stated in a post on the ubuntu forums. He also seems to not have the double clock speed symptom.

asus a8v-e se has the Marvell 88E8053 GbE Gigabit Lan PCI Controller. Is this controller supported by ubuntu 5.10 32/64 bit?

[http://www.linux-tested.com/results/asus_a8v-e_se.html](http://www.linux-tested.com/results/asus_a8v-e_se.html)

The tests were done with suse 9.2, fedora 3.0 and redhatws 3.0. Since ubuntu 5.10 is newer than these operating systems, does it support this lan pci controller?
Since a8v and a8v-e se are closely related, with a8v free of the double clock speed issue, is a8v-e se also free of this issue?

Thank you

---


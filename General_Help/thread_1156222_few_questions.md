---
title: "few questions"
date: 2009-05-11
forum: General Help
---

### Post by DeViLDuD3 on 2009-05-11
well I have few questions regarding Ubuntu 8.10
 
1, I first booted my pc for demo ver of Ubuntu, and saw how things were there, the boot option for Ubuntu stayed there. sometime later I Inserted ubuntu cd into the drive using windows and selected to install Ubuntu along with windows, so it copied files on E which was FAT32 partition total 17gb which was almost free, then it rebooted the system and started the Ubuntu environment from the boot, there it asked me 7 questions, 1 was time and stuff, 2 or 3 was like partition manager I have two hard drives, one is 40 gb and other is 80 gb, my windows is Installed in this 80 gb drive in partition C: which is 40 gb, the rest 40 gbs are distributed with two partitions one is in use and the other is E: and had like 200 mb free space on 80 gb drive.
The problem is that, though I selected E: for root / and formatted it for ext3, it installed the whole OS there, but when I reboot my computer, Ubuntu is like not installed and whatever I did in previous session is gone, the setting or installation isnt saved at all, I created username before now when I login to the Ubuntu it asks me again those 7 steps for installation, I tried it 2-3 times, I formatted another drive for ext3 and selected it for root, yet same thing happens again !
 
2, I want to setup VPN on Ubuntu, on network manager, the 'ADD' tab is disabled I wonder why ? though 'ADD' tab at DSL, Wireless, and all other tabs the ADD tab works, I dont know maybe its because its running in demo mode ?

---

### Post by DeViLDuD3 on 2009-05-12
hulo any one ? can any one tell me why does ubuntu shows me live user when I installed it repeatedly several times ?

---

### Post by cybrsaylr on 2009-05-12
You said "E: and had like 200 mb free space".

That is not enough room for Ubuntu.

I put Ubuntu on a 20GB partition you need at least 6GB of space for Ubuntu.
Ubuntu will not mount on a 200 mb partition.

---

### Post by nacho32 on 2009-05-12
> **DeViLDuD3 said:**
> hulo any one ? can any one tell me why does ubuntu shows me live user when I installed it repeatedly several times ?
odd I would down load the super [grub boot load ISO]("http://www.supergrubdisk.org/") burn to disk and try from their,
make sure in your Bois that it can boot off the other hard drive as well, the boot loader might be loaded on the other HD, but if the bios is not set right it will skip and will not find the boot loader, but you should be having no problem, I'm running a triple boot xp-win-7 beta and 9.04 with no problems, the super grub boot loader is a must have tool... hope this helps

---

### Post by DeViLDuD3 on 2009-05-12
well sorry if I had made mistakes.. drive E: is total 17 gb and it was like all empty the setup copied the files.. I guess it ate like 6 gb, then when I entered in the gnome and asked to resize the partitions, I selected the drive E: for ext3 and mount it as root, the installation went on sucessfully. but when I reboot Ubuntu, it asks me again for those '7' steps if I cancel it it takes me back to live session user. I Kind of installed Ubuntu like this 3 times, selecting one more partition which was 10 gb all free and converted it to ext3 and selected it as root, yet after successfull installation and reboot, Ubuntu kind of forgets it was installed before ?

---

### Post by nothingspecial on 2009-05-12
Have you taken the cd out?

---

### Post by DeViLDuD3 on 2009-05-12
well offcourse, but during installation it wuz in !

---

### Post by DeViLDuD3 on 2009-05-12
well grub boot load did it for me =)
 
so lets move on to the second question..
in network manager the VPN "ADD" tab is disabled? why?

---

### Post by DeViLDuD3 on 2009-05-12
hulo anyone ? the VPN "ADD" is inactive? whats the solution ?
I tried doing sudo apt-get install network-manager-vpnc and openvpn but it doesnt seem to recognize these packages, it only recognizes network-manager.
I manually downladed network-manager-vpnc, openvpn and pptp for 8.10 but then it doesnt install the dependencies showing them unsatisfactory ? whats the solution to it ?

---

### Post by DeViLDuD3 on 2009-05-13
hulo anyone ?

---

### Post by DeViLDuD3 on 2009-05-13
hulo is there anyone ?

---

### Post by DeViLDuD3 on 2009-05-13
hulo can anyone reply to dis ?

---

### Post by DeViLDuD3 on 2009-05-13
how can I make the network manager- VPN "ADD" tab active? any idea?

---


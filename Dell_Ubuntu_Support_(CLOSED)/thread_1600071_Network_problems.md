---
title: "Network problems"
date: 2010-10-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 1234554321 on 2010-10-18
When i try to connect to my router, it shows no connections, and I'm not sure how i can make it show them.
Help?
(new with ubuntu)

---

### Post by 1234554321 on 2010-10-18
Please hellp, and when i right click on the connections thing (currently using wired, but i need to get it working for my router) enable wireless is not selected and it doesn't let me click it to turn it on.

---

### Post by Gorakand on 2010-10-18
I am having the same issues as you are.  I can't connect once I install 10.10 with both wired and wireless connections.  

To make it worse, I can't even use "sudo get-apt" to utilize any application through the terminal.

---

### Post by 1234554321 on 2010-10-18
Can someone PLEASE help?
I've used ubuntu before (Not sure what version) and i fixed it by doing a few things, Which i don't remember.
I just need some helpful person to give ideas on what will fix it.
Thanks if you do.

---

### Post by gibbylinks on 2010-10-19
It sounds like you both need to enable/install the correct drivers.

Perhaps you could both post back with the model of your laptops, that will help people point you in the right direction :P

ALWAYS try to include as much information as you can when asking for help. People can't help with vague posts like "My screens black" or "Wireless doesn't work" as much as they'd like to.

It's a good idea to put stuff in your signature, that way you don't need to keep retyping it, and update your profile to show what version of Ubuntu/Kubuntu etc your using (see below my icon)

---

### Post by johnnytm on 2010-10-19
sounds like you dont have drivers installed. go to system-->administration-->additional drivers (hardware on 10.04) let it run and if a driver shows up enable it. Would be nice to know what card it is first though. there are 2 broadcom drivers and only 1 works right. post results of ```
sudo lshw -C network
```

---

### Post by lekifsirk on 2010-10-19
I am having a similar problem.  I just bought a Dell N7010, wiped the hard drive and installed Win 7 Ult and then Ubuntu.  I have no wired or wireless network.  Below is the output for 'sudo lshw -C network."
Any help would be greatly appreciated.
Thanks.


kris@kris-laptop:~$ sudo lshw -C network
[sudo] password for kris: 
  *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:2000(size=128)

---

### Post by johnnytm on 2010-10-19
lefiksirk, from your post you dont have any drivers for either device. If you can please post the out put of
```
l[SIZE=3]spci -nn | grep 'Broadcom'[/SIZE]
```[SIZE=3] [SIZE=1]then I can see what your wired ethernet card is[/SIZE][/SIZE]

---

### Post by johnnytm on 2010-10-19
actually I have found another post that appears has the same drivers you need lefiksirk [http://ubuntuforums.org/showthread.php?t=1505697&page=9](http://ubuntuforums.org/showthread.php?t=1505697&page=9) I hope you have a cd that u can add as a repository. Put the cd in the drive open synaptic, hit settings and go to repositories and check the official cd box close the window and press update. now look for the broadcom sta driver and get that wireless working then download the atheros driver for your nic.

---


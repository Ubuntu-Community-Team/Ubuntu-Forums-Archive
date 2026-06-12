---
title: "PocketPC Activesync under 8.10 with xp?"
date: 2009-04-14
forum: Desktop Environments
---

### Post by geekyhawkes on 2009-04-14
I have an XP Pro (SP3) virtual machine running under 8.10 but am struggling to get activesync working with my WM6 pocketPC.  When the device is connected it appears in ubuntu (either as a usb mass storage device or a network adapter depending on the activesync status on the device), but it doesnt appear to the virtual machine.  

How should i configure the usb properties under virtualbox to make the xp vm activesync with the device?  

Thanks.

---

### Post by bgerlich on 2009-04-14
You are using the OSS version of Virtualbox. Only the closed source version from virtualbox website supports USB. Download and install that one. You can save and reuse your virtual machine image.

---

### Post by geekyhawkes on 2009-04-14
Thanks, i have actually found a way around the problem that didnt involve activesync.  

The next issue i have is that i want to be able to address messages from the network to the ip address of my virtual xp machine.  The problem i have is that it doesnt seem to be working, from within VM XP the ip address is being reported as 10.0.2.15 but if i ping that from ubuntu then i get not reply.  This IP address also doesnt fit with the rest of my network, all of which start 192.168 etc.

Is there some sort of IP forwarding i need to do to get through to the VM install of XP or is it not that easy?


Im guessing it is something to do with the way i have setup the network adapter in VMbox.  Under attached to i have host interface, nat and internal network.  Can someone give me an idea which of these i should select so i can address tcp/ip traffic to the ip address of my xp machine?

I have played with all 3 of the options but appart from an ip address change on vm machine reboot i have had no more success really.  All pointers welcome please guys.

---


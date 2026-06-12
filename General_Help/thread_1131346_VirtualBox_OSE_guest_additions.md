---
title: "VirtualBox OSE guest additions"
date: 2009-04-20
forum: General Help
---

### Post by Volt9000 on 2009-04-20
I'm really stuck here. I've been trying to install the guest additions in VirtualBox. I've got WindowsXP installed as the client, and when I click Devices > Install Guest Additions I'm told that it can't find the iso, so it prompts me to download. I say yes, but then it complains it can't download it.

I searched high and low and there's no sign of the VBoxGuestAdditions.iso file anywhere on my system. According to the manual it should have been installed along with VirtualBox.

What can I do?

I'm using VirtualBox OSE 2.0.4. According to Synaptic I have the following packages already installed:
virtualbox-ose
virtualbox-ose-guest-utils

What am I missing?

---

### Post by fcuk112 on 2009-04-20
i had this same problem, when you click download it should show you the path it is trying to download from.  just paste this into your browser and you should be able to locate the iso.

---

### Post by Volt9000 on 2009-04-20
Ah geez, I feel like an idiot for not having tried that. ](*,)

When the message said it was unable to download the .iso I just assumed the URL was invalid.

Thanks a bunch!

---

### Post by t60-raven on 2009-05-02
I had this same problem too, however fcuk112's solution didn't work for me.

I had to
1. delete the previous guestadditions.iso (in /../home/.virtualbox)
2. go to synaptic and remove the virtualbox-ose-guest-source and the virtualbox-ose-guest-utils, then add them again 
3. open the VM again and download guest additions from the devices menu

edit:
just as a sidenote, my solution was for 9.04

---

### Post by DustWolf on 2010-10-30
For everybody else that ends up in this thread looking for the OSE guest additions for windows installer, unwilling to go trough compiling their own copy from source and unwilling to use the non-OSE guest additions on a guest in an OSE host:

[http://code.google.com/p/virtual-box-windows-guest-additions-installer/]("http://code.google.com/p/virtual-box-windows-guest-additions-installer/")

Took me forever to find it...

LP,
Jure

---


---
title: "network-admin &quot;locations&quot; don't work"
date: 2006-02-25
forum: Desktop Environments
---

### Post by svref on 2006-02-25
gnome "network-admin" aka "Network settings dialog" is not working as I expect.

I have an ibook, and an 802.11b network with wep encryption.  These can talk fine.

I create a "location" called "home" and put in the relevant information.

Then I create a "location" called "coffeeshop" and put in vanilla DHCP without any wep encryption.

No matter what network location I last have selected, whenever I bring up network-admin, it always reverts the current location to "coffeeshop"!!!

____

sidebar: the Help button for network-admin is typical gnome-quality documentation ("To add a DNS server, select DNS Servers->Add"), and appears to document a version of network-admin with another button for managing network locations.

I also have had no luck finding the homepage for gnome network-admin, so I ask here...

---

### Post by svref on 2006-02-26
I never did find a fix to the fact that network "locations" don't work.  I'm very disappointed - making mundane laptop network manipulation understandable to my wife was a major reason I switched from Debian to Ubuntu, and now it turns out that the GUI is just useless chrome with broken functionality.

---

### Post by KlfJoat on 2006-02-28
I have this same issue, and it's not the only issue I have with network-admin.  

Currently, my CPU is sitting at 100% usage because I had the audacity to make a change with network-admin, and then click the "close" button.  If I open network-admin, but make no changes, it closes after a reasonable period of time.  This has happened ever since I first set up my networking.

---

### Post by svref on 2006-02-28
My guess is: Check your wifi drivers.
I mostly gave up on network-admin, switching to the laptop-saviier NetworkManager from universe, however, I suspect the problem with network-admin was compunded by wifi drivers not be up to doing a network "scan".  You can check if your drivers can do the same by doing **sudo iwlist eth1 scan**.  If it prints out good info then it works, obviously.  If it prints out something about not being able to scan... well maybe you can d/l and compile a newer driver that upgrades the functionality.  (I had an Airport)

---

### Post by kickaha on 2006-03-02
I have this issue also.

The help page seems to be for some other version of network settings.
When I boot my notebook, I'm not sure what location it picks, because
the 'location' drop-down is blank. When I open the list, it's always
pointing to the item that the mouse happens to be over.

I'm curious as to whether this is a gnome problem or an ubuntu networking
admin problem.

I know it's not a driver issue. My Averatec notebook has an Intel IPW2200
wifi chip in it, which is supported natively right out of the box. Once I
manually set my interfaces file and performed an /etc/init.d/networking restart, wifi worked just fine.

It really unconsionable that something that important to networking
functionality is so badly broken...

</rant>

---


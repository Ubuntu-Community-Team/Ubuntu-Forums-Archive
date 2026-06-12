---
title: "Linksys WMP54G will not stay connected"
date: 2006-08-06
forum: Desktop Environments
---

### Post by BirdZerk on 2006-08-06
I just started using Xubuntu on a computer with a Linksys WMP54G wireless pci card.  Because this computer is not connected to the internet I had to download:

bcm43xx-fwcutter_20060108-6build1_i386.deb
and
bcmwl5sys.zip

to be able to get the card working, but now I have a problem that I don't understand.  When I goto the network-admin what shows up is the:

wireless card as eth1 (active)
ethernet connection (active)
modem connection (not configured)

I selected the wirless card and then clicked properties and selected the network for the wireless router (only one listed) and the connection setting as DHCP and then clicked OK.  Back in the network-admin screen I deactivated the ethernet connection and made sure the default gateway device selected is eth1 (wireless).  Clicked OK and everything seems to be set, but firefox can't find any webpages.  I open network-admin screen again and see that the default gateway device has no selection (blank).  So the question is how do I make the network default gateway device stay connected to the eth1?

---

### Post by russbuss on 2006-08-12
I'm not sure how much this will help, but I had some similar sorts of problems (although I'm running Ubuntu, not Xubuntu).  After you get everything set in the network-admin screen, does your connection ever work through your wireless card?

My problems were mainly that my connection would work for a bit and then stop.  I found that rebooting my machine while the connection was working seemed to solve the problem.  I must confess that I have no idea why this would work.

Like I said, I don't know if this will be of much help, but I figured it couldn't hurt.

---


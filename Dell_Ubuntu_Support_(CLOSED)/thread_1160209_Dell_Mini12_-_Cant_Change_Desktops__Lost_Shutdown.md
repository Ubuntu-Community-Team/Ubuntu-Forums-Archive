---
title: "Dell Mini12 - Cant Change Desktops / Lost Shutdown"
date: 2009-05-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by idesigntec on 2009-05-15
I'm a complete noob to linux.  I've been a Mac user since 1990.  Recently my Powerbook 17in bit the dust and I needed a replacement but couldn't afford another Mac.  Since I only need a notebook for web browsing and email, I figured I'd save some money and get a Dell Mini with Linux.  I'd heard Ubuntu had matured to the point that it was user friendly.  I've had it for a month now and I'm feeling like this was a big mistake.  

My first clue was taking it right out of the box and trying to connect to my wifi network.  I use WPA2 with MAC address filtering and don't broadcast my SSID.  Ubuntu just wouldn't connect (I've got multiple Macs and Win boxes, smart phones, etc... on this network and never had an issue, even with the Windows stuff).  It took me an hour just to find out the MAC address of the Dell.  I finally gave up as it was quicker to change my entire wifi network (removed MAC filtering, broadcast my SSID) and got the Dell connected.  But now I feel vulnerable.

Anyway, to my current problems:

Not being able to live with the look and feel of Gnome, I tried to customize the theme.  Spent hours googling and reading how to do that, with no luck.  I couldn't do any more than switching the themes that came built into Gnome.  Couldn't add any new ones from the net.  The built-ins are as ugly as the default.  Gave up on that and next tried to switch to KDE.

I found instructions to do that here on the Ubuntu forums and followed them to the letter:

sudo aptitude update
sudo aptitude install kubuntu-desktop
during install, I chose KDM as the desktop manager

sudo aptitude remove ubuntu-desktop

I then rebooted.  Got the Kubuntu splash screen and login screen and thought all was going well.  The desktop then booted into Gnome.  I tried to reboot again and found that in the Quit menu, I have now lost my option to shutdown or restart the system.  I can only logout, switch user, or suspend.  Nice...

I do see that there are now a number of what I assume to be KDE apps (they all start with K).  It looks like KDE and Gnome are now merged? but still with the ugly Gnome GUI,

I've tried several times to remove Gnome and cannot, and am left without the ability to shutdown or restart.

What am I missing here?  Any help will be appreciated.  I'm discouraged - Linux isn't what I'd hoped it'd be and I'm thinking the best thing to do may just be dumping this thing on eBay.

TIA,

Bill

---

### Post by tyroeternal on 2009-05-15
When you go to log in there is an **Options** button in the bottom left hand corner.  From there you can switch your login session from gnome to kde :D

---


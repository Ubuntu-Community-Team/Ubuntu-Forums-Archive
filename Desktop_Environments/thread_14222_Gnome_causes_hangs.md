---
title: "Gnome causes hangs?"
date: 2005-02-05
forum: Desktop Environments
---

### Post by m0bilitee on 2005-02-05
I'm only speculating, but I'm seeing system hangs in the desktop and any attempts to kick off the download manager in Firefox.

I'm using Warty 4.10 with kernel 2.6.8.1-4, basically a clean installation. After running for a few minutes, if I go to the Computer menu and choose System Configuration, before the additional menu can cascade any items, the whole desktop hangs. I can move the mouse around, but alas I am dead and it freezes up.  Firefox also hangs when I try to click on anything that would kick off the download manager. For example, I try to download attachments in this forum, and firefox hangs. I can force quit it and run it again.  I've run it from a command line, hoping it would throw an error to stdout, but nothing appears.

If I hang the desktop as initially described, I cannot get back out nicely. If I ctrl-alt-backspace to get X to die and respawn GDM, the login screen doesn't come back up after X starts, it just hangs with a graphical screen and mouse pointer.  I ultimately have to restart the system to get things going.

EDIT - Sometimes it does give me the logon screen, then hangs after I type in name and password.

It's almost as if a gnome or window management issue is occuring under the hood.  

This is a Dell Latitude D600 with 512M of memory, brand new box (< 2 weeks old), and I am running NDISwrappers for wireless.  

Ideas?

m0b

---

### Post by m0bilitee on 2005-02-06
Follow up: This is somewhat related to networking.  Gnome seems to get confused that I start networking after i get logged in (this is necessary since i'm using ndiswrapper and then use iwconfig to set my wireless parameters. The Network applet within Ubuntu does not allow me to specify my WEP key for a key index of #2, rather than the standard #1--odd that that is missing).

So, how can I get Gnome to play nice?  I've changed my computer name to localhost.localdomain and was hoping any Gnome/Nautilus stuff would work via loopback 127.0.0.1, but as soon as I get an IP address via DHCP after running dhclient, SOMETHING changes somewhere and some of the apps try to open up to another IP.

Or am I just crazy?  :-)

M0b

---

### Post by Beffroi on 2005-02-07
I am experiencing very similar problems, the gnome desktop freezes (everything the mouse pointer is dead). Mostly this happens when I am using Firefox (or Mozilla). Both are also very slow on some websites (e.g. ebay), the freeze mostly happens after I have hit  such a website. 
I had similar issues a few times when used gedit. This just did not hung the whole desktop but only the task panel so that I couldn't use the pull-down menues anymore. I also experienced the above-mentioned issues with the restarted desktop. 
Additional information: When I was patient enough to wait for several minutes (5-10), the desktop recovered from its freeze.
My hardware: Mainboard: ABit AV8, Athlon 64, Radeon 9000 AGP, 512 MByte RAM, 120 GByte Maxtor HD (Windows 2000/Ubuntu Multiboot), LCD-Screen over DVI).
Is there anyone who has an idea what can be done about this? 
                            
                                                             Thanks,
                                                                            Beffroi

---

### Post by m0bilitee on 2005-02-07
What is your machine name, and does it resolve from the local DNS server properly?  I think my problems come from the fact that gnome starts before I get my DHCP issued IP address.

---

### Post by Beffroi on 2005-02-07
Ubuntu actually does not resolve my machine name every time I switch it on I get the error that it is "temporarily unable to resolve" the name (or something similar).
As I use my computer as a stand alone machine I did not think this would matter. Do think that this creates the problem?
                                                           Beffroi

---

### Post by Beffroi on 2005-02-09
I think I solved the problem for my machine (though I do not pretend to understand what went wrong  :confused: ). Here is what I did: I used the Network Editor (under Computer -> System configuration) to add my internet connection (Dial up [modem/ ppp] in my case.
For some reason, Ubuntu had set the DNS from my Internet provider as the general DNS, so I deleted that.
Finally, I configured my eth0 as loopback (however, I inactivated it, so I don't see how this could have an impact).
I don't know which of the measures did the trick but right now I can surf the web without experiencing any gnome-related problems.
I hope that this solved my problem for good.  :D

---


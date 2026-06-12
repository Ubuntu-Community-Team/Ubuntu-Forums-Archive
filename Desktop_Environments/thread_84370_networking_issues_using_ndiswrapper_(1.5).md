---
title: "networking issues using ndiswrapper (1.5)"
date: 2005-10-30
forum: Desktop Environments
---

### Post by droopyeight on 2005-10-30
Wow, is wireless a pain.

I installed SUSE 10 earlier this week and got the wlan working on it after following the mediawiki on the ndiswrapper site for SUSE.  After having audio issues, I decided to use Ubuntu instead.  I have the audio working with Ubuntu, but now I'm having wireless issues -- after a few days involving many hours, here's where I am.  Any help is **greatly** appreciated, thank you.

hw: ibm thinkpad A22p w/ Trendnet TEW-421PC pcmcia wireless card

Thinking that the older version of ndiswrapper might be the problem (Ubuntu 5.10 comes with ndiswrapper version 1.1-4), I compiled and installed ndiswrapper 1.5 and downloaded the newest windows drivers off of the Trendware site (these drivers are the ones that I got to work on SUSE).

The Network Configuration tool shows the wlan0 interface and allows me to activate it.  Doing a iwlist wlan0 scan shows my AP.  It looks like everything should be fine to me.  However, I can't receive any DHCP settings from the router behind my AP bridge and even setting my IP to a static IP won't let me ping anything (even the AP).  I receive a Destination Host Unreachable message.

Doing a 'route' command shows the expected routes, but there's about a 20 second pause between the first and second lines in the resulting table display:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

I've checked the man page for ndiswrapper to see how I can determine the installed version (just to make sure) but it doesn't mention how.

So, my question is: what is it that I'm missing?  What do you do when everything appears that it should work but it doesn't?

Thanks for any help!

---

### Post by Zotova on 2005-10-31
It seems your card is working at the moment, try disabling any security on your router and see if you can connect - if it does then you can work your way up from there, enable wep, then wpa etc.

Also try using a static ip address and see if you have any joy connecting that way.

I must admit I never had loads of joy with ndiswrapper, some things which might help:

Don't use the version in ubuntu, I don't know why but it just doesn't seem to work. I got various errors in Hoary using the ndiswrapper which comes with Ubuntu.

To make sure the old one is installed I'd suggest doing a search for ndiswrapper and delete all the related the files. Then start again and compile and install a fresh version of 1.5 from the ndiswrapper site (as you have already done).

That fixed a problem I had with ndiswrapper although I'm not saying it will for your problem, just a suggestion which I hope might be of some help.

I found with ndiswrapper that every 2 or so weeks the darn thing would just stop working - others do seem to have better experiences though. In the end I just gave up and brought a card with native linux support.

---


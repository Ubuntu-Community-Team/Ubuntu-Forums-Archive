---
title: "Inhuman intervention required for modem setup"
date: 2005-07-11
forum: Desktop Environments
---

### Post by edrosten on 2005-07-11
Hi,

I'm new to Ubuntu (but not Linux or UNIX in general), and I had a problem with the modem (networks in general) setup desktop applet (is this, therefore the correct forum?). Esentially, it would not create a script which would allow connection to my ISP. Part of the problem, I believe is the lack of any remotely `advanced' options. Since pppconfig created a working script, copying /etc/chatscripts/provider to ppp0 and /etc/ppp/peers/provider to ppp0 (updating it to point at the correct chatscript) worked in that I can now use the gnome panel modem applet to connect/disconnect.

I don't think this fits with the "For human beings" slogan :-)

Seriously, though, is this a bug, (mis)feature or what? The network config documentation has several errors. Firstly, it says the configuration tool is in the wrong place in the menus. Secondly, it seems to be for a different version of the configuration tool (one which does have advanced options).

Here are options which it might need (ie the options I changed in pppconfig):

Authentication type (I require PAP, instead of chat)

Judging by the noise the modem makes, it sounds like it is connecting at a slower speed, so an option (or different default) is required for modem speed, as well.

The DNS type (ie static/dynamic/other).


Thanks

-Ed

---

### Post by tristan on 2005-07-11
As much as I like ubuntu, I have to admit that the default gui tools for modem internet setup and connection are simply not good enough.

I don't even bother with them now. I use **sudo pppconfig** to quickly establish my dialin settings, and use pon to connect to the internet. Once connected, **synaptic gnome-ppp **. Gnome-ppp should be on ubuntu by default, it's fast and easy to set up a working internet connection, and looks good too!

---


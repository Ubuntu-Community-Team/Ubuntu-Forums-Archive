---
title: "wifi woes --- wtf?"
date: 2005-11-17
forum: Desktop Environments
---

### Post by TMR on 2005-11-17
I would be very grateful for some help with wifi installation.  I am a
Linux newbie, and my old Unix knowledge is rusty (and didn't include
much installation work).  Please feel free to ridicule my ignorance
--- I can take the sarcasm --- but please help!

**Background**
I have an old HP Pavilion (900MHz), which now has 192Mb of memory.
Before I threw it out I realised I had the perfect opportunity to try out a
Linux distro for laughs, and installed Ubuntu 5.10.  No laughing
matter --- this is a seriously great and professional operating system
(my last Unix was Solaris, about 10 years ago).  How times have changed!

So, I decide to keep the box and put it on my home wifi network.
Ubuntu had done such a great job of H/W autodetect on install that I
decided to just put in the new wifi card (v. cheap Trend 228-PI) and
reinstall Ubuntu.  But that didn't work so now I've got a fresh
install, a new wifi card, and a huge headache.

**What I did**

1) Installed Ubuntu 5.10.  System>Administration>Network shows that
there is no wlan interface. eth0 is present but not configured --- but
this was the same as when I installed before the wifi card was
present --- and the PC doesn't seem to have a NIC. (Is this a default?)

2) Went to [www.trendnet.com](www.trendnet.com), saw there was no Linux driver for my
card.  Read Wiki, found out about ndiswrapper.
System>Administration>Synaptic Package Manager>ndiswrapper-utils
checked, then I applied it.  It loads. (Where does it load from?)

3) Did the following (as local user in terminal window):

[FONT="Courier New"]mkdir wifi_drivers
cd wifi_drivers
cp /media/cdrom1/drivers/* .
ls[/FONT]

and got: 

[FONT="Courier New"]NETR8180.INF  rtl8180.sys[/FONT]

(Why is /cdrom empty? Is that just the mount point or something?)

4) Did the following:

[FONT="Courier New"]sudo ndiswrapper -i NETR8180.INF
ndiswrapper -l[/FONT]

and got:

[FONT="Courier New"]Installed ndis drivers:
netr8180	driver present, hardware present.[/FONT]

5) I tried:

[FONT="Courier New"]ndiswrapper -m
[/FONT]
but when I rebooted, still no wlan in network administration.

So I manually editted /etc/modules and added ndiswrapper to the
bottom.

(That's right, isn't it? It's what ndiswrapper -m is supposed to do?)

6) When I rebooted, network admin could see a (new) wireless
connection --- not configured.

7) I ran network admin and activated the Wifi card, telling it to use
DHCP.  It took a long time (sending DHCPDISCOVERs, perhaps?)

When I looked in /etc/network/interfaces, nothing had happened.  So I
manually edited it: it now says

[FONT="Courier New"]...loopback stuff...

mapping hotplug
   script grep
   map wlan0

iface wlan0 inet dhcp
auto wlan0[/FONT]

(Isn't that what the GUI was supposed to do?)

Now the wifi card dead as a dodo.  iwlist wlan0 scan returns nothing.
The card worked straight away in my XP box --- what's going on here?
I can see it in ifconfig, and with iwconfig, but it won't find my network
--- iwlist wlan0 scan returns 'no scan results'  The LED on the back of the card is blinking away.

Please help.  Thanks a lot.

---

### Post by TMR on 2005-11-17
Hey, I fixed it. I tried to build an ndiswrapper --- that didn't work because I assumed I could use gcc-4.0 instead of 3.4, and ended up with an invalid kernel format (that is why it happened, right?).  So I gave up on that and reinstalled my system.  Now it works.

The problem seems to have been:

1) I used the driver on the CDROM that came with the card (NETR8180) instead of the one I later downloaded from [www.trendnet.com](www.trendnet.com) (NET8180)

2) I misunderstood the purpose of ndiswrapper -m.  It writes to something other than /etc/modules.  

I might have got it sooner had not the ndiswrappered wrong driver behaved differently on the two subsequent times I installed it, but hey --- it's a learning curve :-).

Although there wasn't time to get an answer for my question, I got loads of material from historic forum chats.  Thanks a lot guys.

...TMR

---


---
title: "Help with Linksys WMP54G Desktop Wireless PCI Network Card"
date: 2009-02-03
forum: General Help
---

### Post by solwic on 2009-02-03
Alright, I went out and bought a nice, shiny new Linksys WMP54G v4.3 PCI Wireless network card today.  Brought it home, popped it in the computer, booted Ubuntu and....nothing.  No notification, no "Hooray for you!", no nothing.  

I'm still hardwired in through my onboard NIC, so no real emergency yet, but I'm lost.  How do I get this thing working?  

Ubuntu 8.10 Ibex, normal install, no KDE to blame...what gives?

Thanks!

---

### Post by Crafty Kisses on 2009-02-03
Have you checked the Hardware Drivers option to see if you have any drivers available for download?

---

### Post by solwic on 2009-02-03
> **Codename said:**
> Have you checked the Hardware Drivers option to see if you have any drivers available for download?

I ran the updater, found nothing.  Checked hardware drivers and it only showed me my video card.  

Do I need to just say f*ck it and take this thing back?  I thought Ibex brought wireless internet out of the dark ages in Ubuntu.  

Help?

---

### Post by caro on 2009-02-03
Does your computer recognize the network card?

```
lspci
```

---

### Post by Crafty Kisses on 2009-02-03
I wouldn't take it back just yet, let's see if Ubuntu at least recognizes it, post the results of this command:
```
lspci
```

---

### Post by solwic on 2009-02-03
> **caro said:**
> Does your computer recognize the network card?

```
lspci
```

Here's the output: 

```

james@wordslinger:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 04)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
**02:02.0 Network controller: RaLink RT2561/RT61 802.11g PCI** ([color=red]IS THIS IT?[/color])
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)

```

Please forgive my ignorance:  I've never used wireless with Ubuntu (never been that foolish before now).  Thanks!

---

### Post by Crafty Kisses on 2009-02-03
I mean I guess we could try an Ndiswrapper, can you grab the Windows drivers for this?

---

### Post by caro on 2009-02-03
That appears to be it.

*Should an SEC guy be helping a Big 10 fan?*  :razz:

---

### Post by solwic on 2009-02-03
> **Codename said:**
> I mean I guess we could try an Ndiswrapper, can you grab the Windows drivers for this?

This card isn't recognized by Ubuntu OOTB?  Linksys is a pretty popular brand....

How do I install Ndiswrapper?  Again, never done this stuff before.  

Thanks!

---

### Post by solwic on 2009-02-03
> **caro said:**
> That appears to be it.

*Should an SEC guy be helping a Big 10 fan?*  :razz:

:lolflag:

---

### Post by Crafty Kisses on 2009-02-03
Well first you need to grab the Windows driver for this card, you could check Linksys's website, or did your card come with a disc? Then from there we can look for a ".inf" file.

---

### Post by caro on 2009-02-03
I think Codename's suggestion is your next step.  Good luck.

---

### Post by solwic on 2009-02-03
> **Codename said:**
> Well first you need to grab the Windows driver for this card, you could check Linksys's website, or did your card come with a disc? Then from there we can look for a ".inf" file.

Got the .exe, extracted, and found Rt61.INF.  Now what?  I hit Alt+F2 and typed Ndiswrapper (I installed it via add/remove programs) but nothing happens.  

Any ideas?

Thanks for all your help.  :)

---

### Post by Crafty Kisses on 2009-02-03
Alright, install this package, and tell me when you have it installed:
```
sudo apt-get install ndisgtk
```

---

### Post by solwic on 2009-02-03
> **Codename said:**
> Alright, install this package, and tell me when you have it installed:
```
sudo apt-get install ndisgtk
```

Did that, ran it, selected the INF file and it says it's there, and the hardware is present.  Still no notification of how to set up the wireless network though.

---

### Post by Crafty Kisses on 2009-02-03
So just to confirm, you did the following? You installed the "ndisgtk" package, grabbed your driver, Once you grabbed the driver, saved it to wherever you want then open the folder where the driver is, and look for the ".inf" file, once you see the .inf file, open up a Terminal and run:
```
sudo ndisgtk

```
Then where it says "Install new driver" find the location of the .inf file, and then where it says "Install" you clicked it.

---

### Post by solwic on 2009-02-03
> **Codename said:**
> So just to confirm, you did the following? You installed the "ndisgtk" package, grabbed your driver, Once you grabbed the driver, saved it to wherever you want, then open the folder where the driver is, and look for the ".inf" file, once you see the .inf file, open up a Terminal and run:
```
sudo ndisgtk

```
Then where it says "Install new driver" find the location of the .inf file, and then where it says "Install" you clicked it.

Yes, and it shows up:

[IMG]http://i444.photobucket.com/albums/qq165/joojoo612/Screenshot-WirelessNetworkDrivers.png[/IMG]

If I click "Configure Network" it says it couldn't find a configuration tool.  I used System -> Preferences -> Network Configuration, but don't know how to set that up.  The OK button is grayed out.  

Also, if I move the INF file do I need to set it up again?

---

### Post by Crafty Kisses on 2009-02-03
Try and get the card to look for an address:
```
dhcpcd wlan0

```
If your router is running DHCP of course, you could also try:
```
sudo ifconfig wlan0 address <ip address>
```
Just to see if it does anything.

---

### Post by solwic on 2009-02-03
> **Codename said:**
> Try and get the card to look for an address:
```
dhcpcd wlan0

```
If your router is running DHCP of course, you could also try:
```
sudo ifconfig wlan0 address <ip address>
```
Just to see if it does anything.

dhcpcd wlan0 returns:

```


james@wordslinger:~$ sudo dhcpcd wlan0
err, wlan0: timed out
err, wlan0: lease information file `/var/lib/dhcpcd/dhcpcd-wlan0.info' does not exist
warn, wlan0: using IPV4LL address 169.254.218.110
james@wordslinger:~$ dhcpcd.sh: interface wlan0 has been configured with new IP=169.254.218.110

```

The second command i entered as ```
sudo ifconfig wlan0 169.254.218.110
``` and it just showed me my prompt again.

Still no notification, nothing shows up under System -> Preferences -> Network Configuration.  No hint at all that anything is working.  

Router is broadcasting DHCP, b and g mix.

---

### Post by Crafty Kisses on 2009-02-03
Here, take a look at this thread: [http://ubuntuforums.org/showthread.php?t=832809](http://ubuntuforums.org/showthread.php?t=832809).

---

### Post by solwic on 2009-02-03
> **Codename said:**
> Here, take a look at this thread: [http://ubuntuforums.org/showthread.php?t=832809](http://ubuntuforums.org/showthread.php?t=832809).

That confused the hell out of me lol.

Still no go.  This shouldn't be this hard....

Any other ideas?  I have no clue what I'm doing here.

---

### Post by Crafty Kisses on 2009-02-03
You may want to try installing wicd, read this thread: [http://ubuntuforums.org/showthread.php?t=1051499&highlight=RaLink+RT2561%2FRT61+802.11g+PCI](http://ubuntuforums.org/showthread.php?t=1051499&highlight=RaLink+RT2561%2FRT61+802.11g+PCI).

---

### Post by solwic on 2009-02-03
> **Codename said:**
> You may want to try installing wicd, read this thread: [http://ubuntuforums.org/showthread.php?t=1051499&highlight=RaLink+RT2561%2FRT61+802.11g+PCI](http://ubuntuforums.org/showthread.php?t=1051499&highlight=RaLink+RT2561%2FRT61+802.11g+PCI).

Actually I rebooted and it found the broadcast.  Asked for the WPA key, my root password, and voila, connected.  

So the old Windows stand-by worked.  When in doubt, reboot!

Thanks Codename, for the help.  You rock, dude.  :)

---

### Post by solwic on 2009-02-03
One last question:  I saved the driver file to the desktop.  If I move that file, will I have to change it with ndisgtk?

---

### Post by Crafty Kisses on 2009-02-03
> **jrock612 said:**
> One last question:  I saved the driver file to the desktop.  If I move that file, will I have to change it with ndisgtk?

I don't think so, and no problem for the help jrock, any time. :)

---

### Post by solwic on 2009-02-03
> **Codename said:**
> I don't think so, and no problem for the help jrock, any time. :)

You were right:  moving the file made no difference.  I just unplugged my ethernet cable (had the forethought to set all this up BEFORE I moved the computer to a different floor of the house than the router) and rebooted.  Works like a charm, though it did ask me to unbind the keyring?  Wanted my password.  

Is it going to do that all the time?  And can I stop it if it does?

Thanks again.  :)

---

### Post by Crafty Kisses on 2009-02-03
I'm not too sure on that one. Sorry about that.

---

### Post by solwic on 2009-02-03
> **Codename said:**
> I'm not too sure on that one. Sorry about that.

No worries.  The answer is probably floating around on Google somewhere.  I just thought, hell, you're batting .1000, might as well throw one last pitch.  :P

---

### Post by Crafty Kisses on 2009-02-03
Actually read this: [http://ubuntuforums.org/showthread.php?t=187874](http://ubuntuforums.org/showthread.php?t=187874).

---

### Post by solwic on 2009-02-04
> **Codename said:**
> Actually read this: [http://ubuntuforums.org/showthread.php?t=187874](http://ubuntuforums.org/showthread.php?t=187874).

That post is over two years old.  Is it still relevant?  Also, there's a .09 on that site...I wonder if I should get it, or use the older .08?

---

### Post by solwic on 2009-02-04
[quote=black_zerg]I tried everything without luck .

so my solution is just :
application->accessories->password and...->edit->reference
change unlock password as a blank.

hope it helps![/quote]

Is that safe?

---

### Post by solwic on 2009-02-04
As a last post I fixed it; reset the keyring password to blank.  not sure if it's safe, but it works.  Thanks for the heads up, Codename.  :)

---


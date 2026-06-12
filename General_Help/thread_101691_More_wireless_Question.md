---
title: "More wireless Question"
date: 2005-12-10
forum: General Help
---

### Post by asad112 on 2005-12-10
Hi, I am running an HP Pavillion ze4900, only on ubuntu, without a windows partition anymore. 

I currently need the drivers for:
Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller

I have found them on the HP website, but I only can download it as a .exe file. Can anybody point me where to go? I really want to get wireless working badly on this laptop, but it is very frustrating.

---

### Post by taurus on 2005-12-10
Is that a PCMCIA card and what is the manufacture of it?  Could it be Linksys?

---

### Post by asad112 on 2005-12-10
when i issue the lspci command, this is exactly what comes up:

0000:02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless  LAN Controller (rev 03)

it is the wireless that was built into this laptop.

---

### Post by arthyee on 2005-12-15
i have the same broadcom wireless built-in my acer travelmate 290e. also having problem activating it. it doesn't show up under 'networking' and the wireless indicator doesn't light up too. it seems the wireless need to be activated thru software (according to acer support). anyone out there have better luck?

---

### Post by nik on 2005-12-15
Haven't tried that card, but try ndiswrapper

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

The driver is included in breezy, but you might have to update... 
If using a 2.6 kernel, make sure to read the FAQ first to save some time...

---

### Post by kaaredyret on 2006-02-21
[QUOTE=arthyee]i have the same broadcom wireless built-in my acer travelmate 290e. also having problem activating it. it doesn't show up under 'networking' and the wireless indicator doesn't light up too. it seems the wireless need to be activated thru software (according to acer support). anyone out there have better luck?[/QUOTE]

Did you - or anyone else - ever get wireless to work on a **TravelMate 290E**?

---

### Post by free0n on 2006-02-21
If you guys need the drivers I have them up on my site here

[http://www.vx13d.net/wifi.tar.gz]("http://www.vx13d.net/wifi.tar.gz")

I have the same device on my gateway laptop and it seems to be working great  with ndiswrapper. 

You should be able to follow the steps on the ndiswrapper page  [here (skip down to the install BCMWL5.inf part) ]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") 

Hope it helps let me know if you need any help or anything :)

---

### Post by kaaredyret on 2006-02-21
Oh thank you, something nice happened. Of course I cant test it from here :neutral: but I can see other networks using 

iwlist wlan0 scan

Just to abuse your good will - is there any gnome applets you recommend for use and configuration? I am a GUI boy :mrgreen: 

Thanks again!

---

### Post by kaaredyret on 2006-02-26
Okay, I have a problem now. If I turn on my laptop, boot into Linux then my wireless card is not activated; the orange LED on my laptop that indicates that the card is operative, is off, and I see no networks. Nothing I do activates it.

If I boot into Windows XP first, then the LED is turned on. If I then boot into Linux after having used Windows, THEN the LED is ON, and Linux can find wireless nets.

EDIT: Hmm, only happened a few times. Not a real problem.

---

### Post by kaaredyret on 2006-04-06
Okay, now I bought myself a nice Linksys wireless router. I haven chosen WPA and that works *perfectly *on the Windows XP machines in our household. Actually it couldnt be easier to get online than that... 

Now, how do I get WPA(2) support with my current driver (or is there any other driver I could use? Win XP says WPA2 in the list over wireless networks.

I am really not into lenghty command fixes and if Dapper will make it work, I can wait. I simply am too busy with real life to struggle for hours with Linux and wireless networking.

TIA

---

### Post by qbox on 2007-10-23
If you have problem with wifi card... see this link
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
it worked for me.

---


---
title: "Using wifi with Ubuntu 6.06 LTS"
date: 2006-07-22
forum: Desktop Environments
---

### Post by Ephemeral on 2006-07-22
Hi!
I recentely bought Planet Linux (french magazine) and they gave a liveCd of Linux Ubuntu 6.06 LTS.
I tried it and love the version!
(Congratulations and thanks to the developers!)
Anyway, I wanted to get internet working before I install it, which seemed a fairly good idea.
Anyways, I went to the networking place and had three options :
Wifi
Eternet
And something else.
I click wifi, then properties and put what I would normally put.
It says it was activating but nothing followed... And I still couldn't access internet.
I have a usb wifi key, its an Inventel dongle 802.11G.
I also have the normal Wanadoo dongle if that can be of any use...
Please help me, I would really like to use this Linux.

Post Scriptum : How do I make Ubuntu look like I want it to ?
As in, not the bars and stuff, just to make it look like I would like it to look...?
Thanks for any help,
Mark

---

### Post by Ephemeral on 2006-07-22
Please, I really need help :(

---

### Post by Ephemeral on 2006-07-22
BUMP
Please reaply and not ignore me :(

---

### Post by Ephemeral on 2006-07-22
Answered all posts except mine :(

---

### Post by BigDave708 on 2006-07-22
> **Ephemeral said:**
> Hi!I wanted to get internet working before I install it, which seemed a fairly good idea.
Anyways, I went to the networking place and had three options :
Wifi
Eternet
And something else.
I click wifi, then properties and put what I would normally put.
It says it was activating but nothing followed... And I still couldn't access internet.
I have a usb wifi key, its an Inventel dongle 802.11G.
I also have the normal Wanadoo dongle if that can be of any use...


Trying to access the internet or a LAN via a USB port on Linux so far is pretty much an experiment in futility. The best way to connect to the internet I have found is to use a wired connection to a broadband router. However, it may be possible to get a PCMCIA wireless card to be recognised, although no where near all wireless cards are supported by Ubuntu.

> **Ephemeral said:**
> Post Scriptum : How do I make Ubuntu look like I want it to ?
As in, not the bars and stuff, just to make it look like I would like it to look...?
Thanks for any help,
Mark

Care to elucidate to exactly what you mean there?

---

### Post by Ephemeral on 2006-07-22
If I cant get internet then I guess I dont want Linux.
I thought it would be cool, to have less viruses, themes and all the Linux goodness, but I am guessing that it will never happen :(

---

### Post by BigDave708 on 2006-07-22
> **Ephemeral said:**
> If I cant get internet then I guess I dont want Linux.
I thought it would be cool, to have less viruses, themes and all the Linux goodness, but I am guessing that it will never happen :(

Don't give up that easily . . . Wireless support isn't that brilliant at the moment, but a wired connection is likely to be automatically detected and supported (mine was) . . . The Edgy Eft release may well have better wireless support.

---

### Post by Ephemeral on 2006-07-23
I have tried LOADS of different Linux distributions and none worked, and I can't use wires, only wireless...
For now I give Linux until the next version of Ubuntu comes out I guess.
If you have ANY ways of getting wifi to work, please tell me.

---

### Post by virgee on 2006-07-23
If you could give a more precise description of the dongle (Inventel 802.11G is I think pretty wide) - type number or so. If we can find what chip is inside, we could find drivers.
I am bit afraid of compiling drivers when in LiveCD system, but we'll give it a go.

---

### Post by Ephemeral on 2006-07-23
All I can figure out is : 
Inventel dongle 802.11G Model No. UR054g (R01) V1.1
Its small, silver and rectangular.
I'll try finding a picture
*EDIT* : The grey thing with a light on :
[IMG]http://img472.imageshack.us/img472/254/parab22ij.jpg[/IMG]

---

### Post by ozorba on 2006-07-23
Can you post us the result of the dmesg command?

I have also found this French forum and it is talking about Invetel USB wifi.

[http://forum.hardware.fr/hardwarefr/OSAlternatifs/pack-wifi-wanadoo-inventel-sous-linux-sujet-32604-1.htm](http://forum.hardware.fr/hardwarefr/OSAlternatifs/pack-wifi-wanadoo-inventel-sous-linux-sujet-32604-1.htm)

You may have to do some investigation to find out where the problem is... Atmel chip is supported by Linux so far as I see.

---

### Post by Ephemeral on 2006-07-24
I'll try dmesg then the French thing, but only if it is possible to do on a live CD.
*edit* : the french thing is for Mandrake :rolleyes:

---

### Post by JoshHendo on 2006-07-24
Take a look at [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) , that may help you :)

---

### Post by patrickfromspain on 2006-07-24
Do yo have a wanadoo conection? It seems like wanadoo uses inventel quite a lot.

Anyway, could you post de output of lsusb?

And in the networking tab, how is the wireless device named? wlan0? ath0? ethx?

EDIT: dmesg and lsusb both work with the live cd. Instead of not trying because that was supposed for an installed version of Mandrake why don't you try. It isn't that hard and you can't harm anything. :-k

---

### Post by virgee on 2006-07-24
Looks like you will have to use ndiswarapper (it will use windows drivers). I found a page in French describing it. [http://fr.gentoo-wiki.com/HOWTO_Livebox_et_dongle_wifi_Inventel](http://fr.gentoo-wiki.com/HOWTO_Livebox_et_dongle_wifi_Inventel)
It is for Gentoo distro, but it would be applicable for ubuntu in its core.
Another links I consider usable (as far as my French lets me) or that could be worth reading:
[http://www.funix.org/fr/linux/dongle.htm](http://www.funix.org/fr/linux/dongle.htm)
[http://jbnote.free.fr/prism54usb/index.html](http://jbnote.free.fr/prism54usb/index.html)

---

### Post by sharperguy on 2006-07-24
I hear that wifi0 is NOT the one to pick, try configuring the other connections to see if they work.

---

### Post by Ephemeral on 2006-07-24
Tried dmesg, got 800 different lines I didn't bother reading.
And I tried the guide and it STILL doesn't work.
I am guessing my effort is redundant.
I hate Wanadoo anyway xD

---

### Post by Ephemeral on 2006-07-25
Bumpity Bumpity Bump

---

### Post by Ephemeral on 2006-07-26
*Ignored*

---

### Post by [h2o] on 2006-07-27
I have gotten ndiswrapper to work with a D-link USB-dongle once, so if you have already tried ndiswrapper then I guess you just had some really bad luck :(

---

### Post by AZzKikR on 2006-07-27
I once had an USB adapter as well, based on the RT2500 chipset (Ralink). It was a hell of a job to make that working, and I couldn't get it to work at boot time. I manually had to press a button on the configurator application to connect myself to my network. After all that crap, I decided to buy a Linux supported PCI card..

The thing I had to do to make it working involved downloading drivers from Ralink, compiling it, insmod'ing it, and compiling an application to connect myself to my network. I don't know how it all went, since it's been about 11 months ago.

So yes, I am adjusting my computer rig to be compatible with Linux. I'm not adjusting Linux to be compatible with my rig :D

The PCI card has a better signal reception anyways (at least for me). If I were you, I'd get a (SUPPORTED!!) PCI card, insert it, and a few configuration steps away and you're basically done. There are a lot of Ubuntu HOWTO's on how to configure PCI cards based on certain chipsets. 

Don't give up that easy ;) I am a full converted Ubuntu user now and I like it way better than Windows!

---

### Post by Sokar on 2006-07-27
You will need an internet connection, via wired link for example, but you can try this:

If in the networking place you see the wifi option, it can be that the system has recognised the card, and can be a problem of the networking place application. Try this: go to the synaptic and install the "NetWork Manager". Once instaled, go to your networking place and disable all cards (even the ethernet card). Restart the computer and, if you're lucky, the NetWorkManager (the new application that should appear in the system tray), will detect your ethernet, wifi...

It worked for my Intel 3945ABG card.

---

### Post by Ephemeral on 2006-07-27
I don't have a CARD, just a little usb key.
And also, how do I install something on a LiveCD ?
Because I am NOT installing Linux unless I am sure it works with my internet.
Another thing : My wep key is in numbers & letters, it is a follows :
##### #### #### #### #### #### ##
BTW, err, what is synaptic ?

---

### Post by Ephemeral on 2006-07-27
Bump

---

### Post by Ephemeral on 2006-07-28
Is the only way to get an answer to pay via e-mail ?

---

### Post by Ephemeral on 2006-07-28
errr....

---

### Post by Ephemeral on 2006-07-29
SOrry for fitfhdriple posting, but I really would like to get some help, I want to use Ubuntu, but I need your help to be able to make it work.

---

### Post by Ephemeral on 2006-07-31
Why do you ignore me ?

---

### Post by patrickfromspain on 2006-07-31
we don't ignore you. You must realize that maybe, if you don't make the effort to install ubuntu on you hard disk first, we won't make the effort to help. 

Working with a LiveCD is a pity.

Anyway, we'll do another try.

in a terminal:

sudo iwlist scanning that should give you a list of available Nets... check if yours is there. Also, you'll see how your wifi is named. I guess that if your net is not there you'll have a lost battle.

sudo gedit /etc/network/interfaces

and paste that into it: (supposing wlan0 is how your wifi is named)

iface wlan0 inet static
address your_ip_address
netmask 255.255.255.0
gateway your_router_address
wireless-essid your_wireless_essid
wireless-key your_wireless_key

in the end you should get something similar to:

iface wlan0 inet static
address 192.168.1.99
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid MY LAN
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

then, save, exit and in terminal:

sudo /etc/init.d/networking restart

now you should be connected.

---

### Post by Ephemeral on 2006-07-31
Wow, thanks a lot for the reply :)
One last thing, how do I know the address of my modem ?
And is my ip address the one of my computer ? (so should I use a findmyip site ? )
And my wireless key is :
#### #### #### #### #### #### ##
Do I have to put in spaces?

---

### Post by Ephemeral on 2006-07-31
So I would put in :

iface eth1 inet static
address  86.198.##.###
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid Wanadoo_7271
wireless-key #### #### #### #### #### #### ##

I'll try that

---

### Post by Ephemeral on 2006-08-01
Doesn't work, going to buy a wifi PCI card, any advice on things ?

---

### Post by Ephemeral on 2006-08-12
Back from holidays, any ideas on wifi PCI card and router I could use ?

---

### Post by maniacmusician on 2006-08-12
hi Ephemeral,

though I don't have any advice on what kind of card is compatible at boot, I will be glad to help you install whatever card you do get. if it's not supported with ubuntu, it is *probably* supported by ndiswrapper. Whenever you get a new PCI card, start a thread in Desktop support, and send a PM my way with the link and the reminder that I was supposed to help you. I'm no stranger to wireless troubles; it took me a long time to figure out how to use ndiswrapper. but now, i've repeated it so many times on so many different computers, i have the process down to around 15 minutes at the most lol. anyways, good luck with getting the wireless card, i hope i can help you set  it up.

edit: if you do still want to make the USB key work, we can probably try that too. but if you want to splurge for a pci card right away, thats fine too.

edit: i'll tell you what card and router I have: Belkin wireless G plus router and the Belkin wireless G plus desktop pci card. It does *not* get detected automatically, I had to configure it specially with ndiswrapper. but it does work. Also, if you're serious about installing it, don't do it all from the live cd, do a hard drive install. if you do it on the live cd and it works, then yay woohoo; but you'll have to do it all over again after you install it on your hard drive. if you dont mind doing that, then sure, but it seems to be an unnecessary nuisance, no?

---

### Post by Ephemeral on 2006-08-13
Thanks for the reply !
P.S : I pmed you

---

### Post by Ephemeral on 2006-08-15
Anyways, I messed up my WIndows system and couldn't format my HD ^^
So, I have Linux Ubuntu INSTALLED now, on my computer, I am talking here using another computer.
Now that Linux is installed can anyone help me ?
BTW, I have TWO wireless USB adapters :
A NETGEAR USB 2.0 wireless 54 Mbit/s (WG111 v2)
A Inventel Dongle (no further ideas on what it is :C )
SHould I try buying a NETGEAR Wireless router to connect to my modem or is that a worthless buy ?
Please answer, I really would like Internet ^^

---

### Post by kronepils on 2006-08-15
If you have Ubuntu installed, I suggest you try NetworkManager.

The easiest way is probably to install it through Automatix ([www.getautomatix.com](www.getautomatix.com))
In Automatix (you will find it in System Tools menu), select NetworkManager (and other goodies!).

Reboot!

When the machine is up and running, you should see a new icon (looks like a screen, I think) up next to the clock.
Click it, and it should list all the wireless networks you can "see".

For all this to work, iwlist scan must work for you! I understood from the posts, that it did. Otherwise it's a driver issue.

NetworkManager is great, and works wonders for many of us! You will have to type a selfchosen password (to unlock the keyring) everytime you boot, but I can live with that.


Good luck!

---

### Post by Ephemeral on 2006-08-15
Thanks a lot for the answer !
There is just one thing I dont understand, how do I install it without having access to internet ?
If you have MSN, could you give it to me for additional LIVE help ?

---

### Post by Ephemeral on 2006-08-15
Google Talk account : markman.flashback
Lol, old account ^^

---

### Post by judgekaster on 2006-08-15
first things first. let us see if your card has been detected by linux: open a terminal and issue the following command:

```

iwconfig

```

post the results here. i'll try to monitor this thread in the next few hours.

---


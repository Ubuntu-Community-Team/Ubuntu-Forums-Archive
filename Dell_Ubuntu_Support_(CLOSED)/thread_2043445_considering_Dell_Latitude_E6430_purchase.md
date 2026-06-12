---
title: "considering Dell Latitude E6430 purchase"
date: 2012-08-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wanderingwaste on 2012-08-16
I am looking to purchase a new laptop to replace my aging Dell Latitude e6500. I am looking primarily at a Dell Latitude e6430 with the following:
 

 Intel core i7-3720qm
 16gb ram
 256gb ssd
 intel centrino 6300 wlan
 nvidia quadro 5200m (wish Dell wouldn't force this, I probably won't need it)
 9 cell/97whr battery
 1600x900p screen
 

 My plan is to run Ubuntu 12.04 with either Cinnamon or Gnome-classic instead of Unity (unity is just too much flash; I don't hate it, I just prefer a dead-simple desktop UI). 

The laptop this will be replacing is running 11.04 with the 2.6.38-8 (I think) kernel, and I am always shocked and how well everything just works. It boots fast, runs fast (and fairly cool), with virtually no stability issues no matter what (outside of a crappy broadcom wlan card), and gets great battery life even though the batteries I use are all 4+ years old and heavily abused (4-5 hours).
 

 My primary concerns are getting that same stability, compatibility, and battery life. The e6430 will be replacing a laptop that, wlan card aside, runs like it was made for linux. Is there anything I can expect to have problems with? I have seen posts about terrible battery life and high heat levels due to the new kernel not interacting right with the hardware, as well as various and sundry components not being compatible with 12.04, but nothing concrete, and not for this model. I don't mind getting under the hood to work on stuff, but I hate crappy workarounds.
 

 Is there anything wrong with this config? Anything I should watch out for?

---

### Post by wahrschein on 2012-08-17
No info about your main issues, but about the price. When I asked Dell about the option to deliver notebooks without windows I was told the only option there was the latitude series. But instead dropping the price a little they even raised it! Hope you have better luck with your store, best regards from Germany.

---

### Post by wanderingwaste on 2012-08-17
Wahrschein, do you have access to a reseller? Sometimes, third-party enterprise resellers are able to get you options and deals that Dell wouldn't ordinarily allow. For instance, my reseller is able to (or at least used to be able to) send me a notebook with no ram or hard drive, were I to so specify it.

One of the reasons I love Dell business grade systems is because they let you swap and upgrade most of the easily-accessible components yourself (i.e. ram, storage drives) and will still provide support and warranty regardless. Why pay Dell ridiculous amounts for RAM and storage, when you can just buy the stuff yourself and take the 5 minutes to swap it?

As to my initial question, I am really just interested in what issues to expect regarding the graphics card, heat, and battery life. I ordinarily wouldn't worry, except I have read a lot about issues with the 3.2.0-x kernel not doing a good job of power management (whereas the 2.39.x-x kernel I am running now has seemingly no issues with this).

---

### Post by eombah on 2012-09-21
I bought a dell e6430 (quad-core i7, 256gb ssd, 8gb) intending to use it with ubuntu 12.04 64-bit.
It did not work well.

Problems:
- nvidia optimus driver not supported
- touchpad not supported
- two system freezes in 2 hours
- machine gets very hot
- fan is constantly on (noisy)

I have been using linux on all my laptops and desktop over the last 10 years, for the e6430 I reverted to the pre-installed windows 7.

---

### Post by soul_rebel on 2012-09-29
Sadly Dell Latitudes are among the few laptops you can buy without Windows in Italy. They make it hard, but you can get a lower price too (I got ~50 euros less than the equivalent one with windows preinstalled, this time)

I bought a e6430 and I am quite displeased overall:
The laptop body is just disproportionate for its screen and the 16:9 ratio for a professional laptop is just stupid, but everybody is doing it. 
The surface around the keyboard is gummy and I think that in a few years it will look horrible. The fan is a bit noisy and its linux support is incomplete for a laptop that came with ubuntu preinstalled. 

On the positive it is sturdy and fast and probably linux support will get better in the next year or so.

So far these are the thing that do not work at all:
fingerprint reader: there is no driver

Things that are buggy:
touchpad: there is a proprietary driver from Cirque. I do no have any link for it, but it works decently. There is also a patch for the kernel driver that initializes the driver and makes it work (badly) with the protocol used in other ALPS devices.
acpi, battery and ac status is not detected and there are errors in dmesg. (not reproduced on ubuntu)
ethernet: driver loses carrier when changing mtu and this breaks dhcpcd (not reproduced on ubuntu)
sd card reader reports an error on boot

I took the intel video chip, not the nvidia one, after all Torvalds was pretty clear about nvidia.

---

### Post by PenzoiderS on 2013-01-20
Hi there (ciao conterraneo ):P).

I've just bought an E6430:

- i5 3220M
- 2 gb ram
- 320 gb sata 5400rpm HD
- HD4000 VGA (no nVidia)
- 1600x900 monitor
- centrino Ultimate-N 6300 wifi
- no fingerprint/smartcard reader
- 9 cell battery
- ubuntu 12.04 preinstalled
- 5 yr basic warranty

as soon as it will be in my hands I'll upgrade with the following goodies (note: on SSD and RAM I was able to save 250&#8364; instead of purchasing from DELL.. mantaining the dell warranty):

- SanDisk Extreme SSD 480 Gb
- 16 Gb DDR3 Corsair 1600 Mhz RAM (2x8)
- snap in the 3G/WWAN module (taken from my old DELL laptop)
- 2nd drive bay (to use slot-in DVD as external, if needed, and fit a 1Tb SATA 5400rpm HD) link here if you need it: [http://goo.gl/QzjeS](http://goo.gl/QzjeS)

I bought this 'cause I wanted to replace my XPS studo 13 (horrible linux experience due to wifi weakness and nVida Hybrid SLI = terrible heat, poor performance (no SLI), great battery drainer).
I've choosen this E6430 'cause its ubuntu certified hardware, so I thought was a flawless buy for my ubuntu needs.

Now I'm very disappointed in reading this (just after purchase, grrrr):

> Things that are buggy:
touchpad: there is a proprietary driver from Cirque. I do no have any link for it, but it works decently. There is also a patch for the kernel driver that initializes the driver and makes it work (badly) with the protocol used in other ALPS devices.
acpi, battery and ac status is not detected and there are errors in dmesg. (not reproduced on ubuntu)
ethernet: driver loses carrier when changing mtu and this breaks dhcpcd (not reproduced on ubuntu)
sd card reader reports an error on boot

@soul_rebel: Wich version are you using? 12.04? did you find any solution to these issues? (link me please, grazie)

@wahrschein: I've bought mine on DELL premier page (for partners): if you choose ubuntu over win7/8 you'll have almost hundred &#8364; off (not a rise of price)! So next time find a DELL reseller or partner instead of buying it directly from website (I think M$$ft has some "influence" in this overprice on public website)

---

### Post by gerrman97 on 2013-01-20
Hello,
I have absolutely no expeience with the e6430, but i do have ALOT of experience with the previous models (e6400, e6410) and i would like to see, in comparison, a picture of the model. If u have one, pm it to me, or email me at [email]gerrman97@yahoo.com[/email] (link will probably be removed) i may be able to help in your desicion.

---

### Post by PenzoiderS on 2013-01-23
I'll recive it in a few days.
I ordered with ubuntu 12.04 preinstalled, maybe there are already the driver fixes for some of the issues reported here (maybe some DELL's custom OS image).

I think I'll save the original image to share with you and eventually solve these issues.

@gerrman97: you can find many pictures here if you wish [http://www.notebookcheck.net/Review-Dell-Latitude-E6430-Notebook.81780.0.html](http://www.notebookcheck.net/Review-Dell-Latitude-E6430-Notebook.81780.0.html)

---

### Post by PenzoiderS on 2013-02-07
My E6430 came with 12.04 preinstalled and touchpad working with multitouch 2finger scrolling and also pinch-zoom. (I have the original ISO image for the factory settings if you're interested I can upload it.. 2.2 Gb it will take ages with my connection.. so ask only if you really need it.. the solution for trackpad is in this post.. so maybe you don't need the iso really)

Now I switched to Debian Sid (I wanted a debian based rolling release, as fast as possible.. so a good netinstall was for me best solution).
So I faced the touchpad issue you reported.

Everything is now working by the way:
[LIST]
[*]ethernet is fine (did not try to change MTU on the fly 'cause i don't need)
[*]ACPI battery stats are ok and SDcard reader too (some warnings on boot, but just working ok)
[*]touchpad had errors but fixed (see below)
[/LIST]

The problem with touchpad is that is recognised as standard ps2 wheel mouse instead of synaptic/ALPS touchpad.. so you cannot find even the touchpad tab under mouse settings and you get a stupid touchpad with unability to scroll or even tap to click.

I found a way to **fix this TouchPad issue** installing a custom driver and using dkms.

download this (currently newest package is 1.2):
[URL="http://www.dahetral.com/public-download"]http://www.dahetral.com/public-download
[/URL]
(really say thank you to these people who wrote this driver, God bless them)

untar and copy (as root) the psmouse-alps-dst-X.x folder to your /usr/src directory (now X.x = 1.2)

once copied just run these commands

```
sudo dkms add psmouse/alps-dst-X.x
sudo dkms autoinstall
sudo rmmod psmouse && sudo modprobe psmouse
```

now you'll find the TouchPad tab under mouse settings and you can enable scrolling and so.. just because now is considered a touchpad and not a PS wheel mouse.

NOTE: if a new driver comes just the new one in /usr/source
and repeat the procedure.
For cleaniniess remove the old one with
```
sudo dkms remove psmouse/alps-dst-X.x --all
```
where X.x is the number of the old version to remove from dkms.
Then you can also remove the relative folder.

hope this helps. now I have a fully working touchpad.

\\:D/

---


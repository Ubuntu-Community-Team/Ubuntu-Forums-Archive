---
title: "Some Troubling Issues With Acer Aspire One"
date: 2009-02-12
forum: General Help
---

### Post by gfmartn05 on 2009-02-12
Hi everyone. I just joined Ubuntu forums and I'm happy to say that I've been using Ubuntu for quite some time now and I'm very pleased with it overall. It's actually the distro that pulled me out of the Windows world.

I bought an Acer Aspire One last year and it's a very nice piece of hardware. I've shared a lot of the similar problems that most everyone who owns this netbook has encountered but I think I'm running into some issues that are, for a lack of better words, really starting to p*** me off. Hence the reason I come to you Ubunutu gurus today.

First off, I'm not sure if this happened to anyone else but about a week ago I checked for recommended updates with the Update Manager. I got my updates and installed them however when I went to go restart my netbook and Ubuntu was initializing, the boot process returned an error saying something about Kernel Panic and that it was trying to kill the init process. Obviously this isn't all that good and I lost all of my programming data because of it.

So then I reinstalled Ubuntu and upgraded to the 8.10 Intrepid Ibex release, which solved a lot of problems namely the updating issue, but then I ran into a very odd problem. A few days into using 8.10, my networking devices just stopped functioning. Not just the infamous Atheros wireless card but the NIC card as well. None of the automatic network connections would start and I tried creating new ones to get a connection and it seemed like the netbook didn't even want to try to connect. It just kept having the balloon pop up saying that the network was disconnected. This is a very serious issue for me because I absolutely rely on my wireless connectivity.

So now I'm back down to 8.04 LTS, which I can't install recommended updates on, and now the latest MadWifi release won't interface with my Atheros wireless card. Which is something that I find funny because before all of this happened, on my initial 8.04 install, I compiled and installed MadWifi with no problem. After a restart I had full access to my wireless card. The only thing I can think of that may be causing this is because I can't install the recommended updates which may contain an update of a package that MadWifi uses.

So ultimately my question is, knowing that I want to upgrade to 8.10 (I really fell in love with that release), why did my networking devices stop working all of a sudden, what can I do to fix it if I upgrade again, and what in the world is that Kernel Panic issue?

---

### Post by callan79 on 2009-02-12
> **gfmartn05 said:**
> Ubuntu was initializing, the boot process returned an error saying something about Kernel Panic and that it was trying to kill the init process. Obviously this isn't all that good and I lost all of my programming data because of it.

None of the automatic network connections would start and I tried creating new ones to get a connection and it seemed like the netbook didn't even want to try to connect. It just kept having the balloon pop up saying that the network was disconnected. This is a very serious issue for me because I absolutely rely on my wireless connectivity.


Hi gfmartn05,

Welcome to the forums, sorry to hear you're having issues.

Disclaimer - I make no claims to be a 'guru' :guitar:

Now, I don't own an Aspire One, however I do maintain the network of a customer that has one, running 8.10. Also three of my colleagues at work have the Aspire One, again all running 8.10.

They all just use the "ubuntu-modules-backports" package in order to make the wireless work. None of them have had any trouble so far, so perhaps yours is a one-off issue. Unfortunately I can't really explain it.

As far as 'kernel panic' goes, that's basically what happens then the kernel (system core) just absolutely goes crazy and cannot recover. I guess you could call it a "crash". Sometimes a bad driver or bad program can do this.

So I'd encourage you to try 8.10 again, but install from scratch, don't do a dist-upgrade. And also the following tips :

(1) Make sure you keep a Bootable Live USB around the place

(2) If you run into a problem, ask here before re-installing

(3) Take regular backups :-)

(4) I recommend you partition your drive with /home in a separate partition. At least this way if you DO need to re-install, you can install the system without destroying your data.


Good luck, and feel free to ask any Q's.

Cheers
Callan

---

### Post by Neural oD on 2009-02-12
8.10 has been having some issues with networking  - a lot of people remove the std NetworkManager. Then run this: sudo apt-get install wifi-radar

---

### Post by doug1212 on 2009-02-12
Hi,
I have put 8.10 on a AAO 110 and did have a few issues with wireless, this was mostly the fault of Gnome network manager mangling the WAP settings.

I followed the guide and built the latest madwifi driver and added the WICD repo installed WICD, this automatically removes network manager.

Good luck,
Doug.

---

### Post by gfmartn05 on 2009-02-12
callan:
Thanks for your insight. I'm actually downloading the 8.10 release right now and avoiding a dist upgrade. Once I get that image downloaded, I'll make a bootable USB key from that image.

neural:
If I get the wifi-radar package from the repository BEFORE removing the std NM, will that cause any significant issues that I should be concerned about? More than likely I'll have to get it first because, as I said before, not only did my wireless stop working but so did the NIC.

doug:
I noticed something like that as well. I use WEP 128b encryption on my network and for some reason it kept defaulting to a WEP encryption on a lower bit setting. So whenever I went to go connect to my network, I would get a prompt for the passphrase every single time.

---

### Post by dsm iv tr on 2009-02-12
Since you're already downloading the 8.10 ISO, this may be of little use, but with the UNR image nearly everything works out-of-the-box for me on my AA1. It's even LPIA already.

[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

That said, I've had my share of wireless issues with a regular 8.10 install on the AA1, until I installed the backports package and started using ath5k. I haven't had a single issue since then.

Before using ath5k's release from the backports package, I've had the most success with ndiswrapper. MadWifi (ath_pci) hasn't worked so well for me for a while now.

---


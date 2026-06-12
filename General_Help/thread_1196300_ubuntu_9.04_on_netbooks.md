---
title: "ubuntu 9.04 on netbooks"
date: 2009-06-24
forum: General Help
---

### Post by privatejarhead on 2009-06-24
im looking at buying a netbook soon and the two i've seen (and liked) so far are the acer aspire one aoa150 and the asus eeepc 1000he. i've looked at reviews for both and im leaning towards the acer, but one thing bothered me a little concerning both. both netbooks come with either xp or linspire, which looks very childish and over-simplified for my liking (same with ubuntu nbr). i just want to have my normal gnome desktop on the netbook exactly like one would see on a normal laptop/desktop computer. would ubuntu 9.04 desktop edition work on either of these two netbooks or am i forced to use nbr?

---

### Post by snowpine on 2009-06-24
Ubuntu and NBR are the same core system, different user interfaces. "Regular" Gnome desktop Ubuntu will run on the same hardware as NBR. I do not own the specific netbooks mentioned, but would be shocked if they were not well-supported by Ubuntu 9.04. I assume you have used the Search feature to read others' experiences on those netbooks?

---

### Post by t0p on 2009-06-24
I own an Eee Pc 701.  In the past I've installed Ubuntu 8.04 and 8.10 on it.  Unfortunately I always found full Ubuntu install to take up too much room (storage on my 701 id a 4 GB SSD and 4 GB SD card).  Just recently, I tried 9.04 netbook remix, but that also was too big.  Now, I'm trying eeebuntu - the "base" install is nice and small, and I am now in the process of installing the software I will need.

If you get a netbook with plenty of disk space, you'll have no problem running Ubuntu with full Gnome GUI.

---

### Post by joemun on 2009-06-24
I have an Asus eee 900 linux version (20GB=4GB+16GB), it came with Xandros preloaded, which i didn't like, so installed XP on it, used for a while until the 4 GB ssd (the faster one) got full and annoyed by the low memory messages from windows, i decided to give Ubuntu 9.04 a try (the desktop gnome version) and i like it a lot, works very well. I bought a 2 GB RAM which didn't work on XP and with Ubuntu it have no problems at all. Everything is recognized without problems. There is a very well known issue with the intel driver in Jaunty, but instead of upgrading it i decided to roll back to the 2.4 driver (the intrepid one). Give it a try you won't regret it...

---

### Post by blueridgedog on 2009-06-24
I have the eeePC 1000 and the Ubuntu NBR works like a champ.  I needed very few tweaks to get everything working (including the camera).

---

### Post by CoreyB. on 2009-06-24
I think you can install Ubuntu Netbook Remix and there is an option to change to the "classic desktop".

It's called Desktop Switcher in UNR.  I'm not sure if it is installed by default, but it is in the universe repository.

---

### Post by Old_Grey_Wolf on 2009-06-24
> **privatejarhead said:**
> ...i just want to have my normal gnome desktop on the netbook exactly like one would see on a normal laptop/desktop computer. would ubuntu 9.04 desktop edition work on either of these two netbooks or am i forced to use nbr?

You are not forced to use NBR; however, I use it because of the limited size of the display. It can be switched to use a normal gnome desktop when you need it.

---

### Post by philcamlin on 2009-06-24
netbook remix is the way to go :popcorn::popcorn::popcorn:

---

### Post by hibliss on 2009-06-24
I own the 1000he. Very feature packed for the price. Battery life in Ubuntu is around 7.5 hours on average, depending on power usage settings. I can get as much as 8.5 hours with totally non real world settings (wifi, bluetooth, and webcam off, screen very dim).

My advice if you decide on this machine is to go with Eeebuntu 3.0 Standard. Based on Jaunty, it has the array repository and eee-control already installed. All of the FN keys work out of the box (except the trackpad key). 

Power management with acpi scripts that come pre-installed is great. I could not be happier with it. 

There is a pretty recent review here that reviews distros on netbooks - [http://www.reghardware.co.uk/2009/06/09/which_linux_for_netbooks/]("http://www.reghardware.co.uk/2009/06/09/which_linux_for_netbooks/")

---

### Post by blueridgedog on 2009-06-24
> **hibliss said:**
>  I can get as much as 8.5 hours with totally non real world settings (wifi, bluetooth, and webcam off, screen very dim).

Then this is the tool for you:

[http://www.lesswatts.org/projects/powertop/download.php](http://www.lesswatts.org/projects/powertop/download.php)

I just came across it in another thread.

---

### Post by hibliss on 2009-06-24
> **blueridgedog said:**
> Then this is the tool for you:

[http://www.lesswatts.org/projects/powertop/download.php](http://www.lesswatts.org/projects/powertop/download.php)

I just came across it in another thread.

People need to realise that the machine was made from the factory to run Windows and is optimised for it. Asus includes the Super Hybrid Engine and quick boot partition/mode. 

It will take some time before Linux is seeing better battery life than the factory installed OS with factory optimisations. The way the linux guys are figuring it out is through reverse engineering the Super Hybrid Engine in Windows.

---

### Post by paxmark1 on 2009-06-25
bought a refurb eee900a 4 gb and 1 gb memory for $200CDN.  auto update bricked it in  xandros after powering up.  I was not going to use xandros anyway.

easypeasy went on without a hitch on liveusb.  eeebuntu installed with base via cdrom, borked when i rotated the video 90 degrees.  I then installed unr 9.04.  No problems, quite sweet  (have not tried wifi yet)  I did update-manager -d and am running 9.10 rc2 with no big bugs yet.  
definitely way beyond my old xp computers and a whole lot easier than debian onto a netbook is my guess.  peace,  mark

---

### Post by Divider on 2009-06-25
Jaunty works 100% with a EEEPC 900a right out of the box.
Also Supports packet injection, right out of the box. :P

Specs:
Atom 1.6 ghz
2 GB DDR2 533
4GB SSD PCIe
Intel media Accel. 945
Atheros Wireless B/G no setup needed for packet injection.

I used to have to download a custom kernel from array.org for intrepid ibex to work with it, but Jaunty really is the best Distro yet.

---

### Post by privatejarhead on 2009-06-26
also, i've heard about how one could expand the drive space on SSD's by using the SD card slot on the left side of the aspire one netbooks. does it work under ubuntu?

---

### Post by blueridgedog on 2009-06-26
> **privatejarhead said:**
> also, i've heard about how one could expand the drive space on SSD's by using the SD card slot on the left side of the aspire one netbooks. does it work under ubuntu?

I use  mine as additional space, but it dosn't expand existing partitions on the ssd.

---

### Post by t4thfavor on 2009-06-26
EEEPC 900a works great with just plain old jaunty on it. Its the second one I have owned, and I like it even more than the first. 

I had 2GB ram in the first, and I really don't notice much of a difference, though I have only had the 1GB one for about 3 days. 

I still plan on upgrading to 2GB asap.

---

### Post by Rallg on 2009-06-26
I have the Dell mini 9. It came with 16G storage and 1G RAM, which I upgraded to 2G. No hard drive, Atom processor. I bought it with XP but later completely removed XP and installed Ubuntu, the regular distro rather than the remix. I had 8.10, and now I am using 9.04.

The desktop is regular Gnome, with some Compiz effects. I don't use the "cube." I have numerous applications, as with my regular laptop.

No problem. Of course, netbooks are optimized for doing some things, but not others.

My guess is that the netbook remix desktop was designed with the idea that a netbook user would only use half a dozen applications, mostly related to on-the-go communications. But netbooks turned out to be more popular than that.

As for using the SD card slot to expand storage, I would only use that for files that are not in regular usage (that is, some documents and large data files, rather than a working partition or swap space).

---

### Post by Divider on 2009-06-26
> **t4thfavor said:**
> EEEPC 900a works great with just plain old jaunty on it. Its the second one I have owned, and I like it even more than the first. 

I had 2GB ram in the first, and I really don't notice much of a difference, though I have only had the 1GB one for about 3 days. 

I still plan on upgrading to 2GB asap.

Did yours have the 4 GB SSD with the laaaaaame R/W speed?

I'm upgrading to a 32 GB supertalent 150 R | 90 W pcie SSD.

---

### Post by hibliss on 2009-06-29
> **privatejarhead said:**
> also, i've heard about how one could expand the drive space on SSD's by using the SD card slot on the left side of the aspire one netbooks. does it work under ubuntu?

Sure, you can get a 32gb SD card, but it will show up as a removable disc. You can still boot off it and run and OS off it though.

---


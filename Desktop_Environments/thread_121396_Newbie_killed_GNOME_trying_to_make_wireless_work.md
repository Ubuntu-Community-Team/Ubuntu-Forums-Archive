---
title: "Newbie killed GNOME trying to make wireless work"
date: 2006-01-25
forum: Desktop Environments
---

### Post by greymaiden on 2006-01-25
As might be expected for a new user, I am having some trouble getting my Broadcom Wireless card to work.  

I started out in the wiki going through all the steps dealing with the ndiswrapper.  Nada.

Then I found this thread on the forums: [HOW TO: Configure Wireless Cards with Broadcom Chipsets]("http://www.ubuntuforums.org/showthread.php?t=25683&highlight=wireless+cards")

Now all I get when I login is an empty screen for five minutes before GNOME loads anything.  That's right, I spend five minutes staring at an empty screen then it finally all loads.  An attempt to acess System -> Administration -> Networking took another five minutes to come up, and my wireless card still isn't listed there.

So I have two questions:

1) Why is everything running so slowly all of a sudden?  

2) How do I get Ubuntu to recognize my wireless card?  I'm not even talking about getting it working here, I'm talking about getting it to show up as a valid device in the first place.

I'm sorry if this is redundant.  I've been running searches all evening and nothing seems to address the issue of not being able to find your wireless card in the first place.

Thanks for any help,
Jamie Lynn

---

### Post by dcstar on 2006-01-25
[QUOTE=greymaiden]As might be expected for a new user, I am having some trouble getting my Broadcom Wireless card to work.  

I started out in the wiki going through all the steps dealing with the ndiswrapper.  Nada.

Then I found this thread on the forums: [HOW TO: Configure Wireless Cards with Broadcom Chipsets]("http://www.ubuntuforums.org/showthread.php?t=25683&highlight=wireless+cards")

Now all I get when I login is an empty screen for five minutes before GNOME loads anything.  That's right, I spend five minutes staring at an empty screen then it finally all loads.  An attempt to acess System -> Administration -> Networking took another five minutes to come up, and my wireless card still isn't listed there.

So I have two questions:

1) Why is everything running so slowly all of a sudden?  

.......[/QUOTE]
Possibly because the system is waiting for timeouts for all network accesses.

Check your /etc/hosts file and post the contents here.

---

### Post by greymaiden on 2006-01-25
Seriously, this is all tht's in my /etc/hosts file:

127.0.0.1 localhost Baldur

Additionally, I had to go add the local host name when I first logged on because it wasn't there.

---

### Post by ahave2005 on 2006-01-25
Have you tried > lspci or > lspci | grep Network, grep just look for a line with network in it and display it.

If you can find your network controller here, you can make it work in Ubuntu. Sure there must be exceptions, but I haven't seen them yet.

If you find it, we'll take from there.

/ahave

---

### Post by greymaiden on 2006-01-25
Yup.  The card is right here:  

> 0000:02:01.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Additionally, here's the info for the chipset from lspci -n
> 0000:02:01.0 0280: 14e4:4320 (rev 03)


I am as concerned about restoring my desktop to it's previous speedy functionality as I am about getting this wireless card to work, however.  Any other ideas on that?

---

### Post by ahave2005 on 2006-01-26
You could have a look in your logs??? There is a graphical frontend for that in your menu.

As for your wireless card, you have a choice between native linux drivers or ndiswrapper for a windows driver.
As for ndiswrapper, have a look at the thread here:
[http://www.ubuntuforums.org/showthread.php?p=550172#post550172](http://www.ubuntuforums.org/showthread.php?p=550172#post550172)

Or have a look at here for a native linux driver: [http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

Give it a shot and keep asking.

/ahave

---


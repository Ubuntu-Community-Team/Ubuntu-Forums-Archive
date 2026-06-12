---
title: "peer-to-peer wireless network between xp and ubuntu, Is it possible?"
date: 2006-05-07
forum: Desktop Environments
---

### Post by yakkob on 2006-05-07
I am trying to find a way to setup an ad-hoc network from my desktop (ubuntu 5.10) to my laptop (win xp) with internet connection sharing, so .

I have a broadband connection connected to an uplink on a hub and both computers are currently hooked up to the hub with cables.  I want to free up my laptop so that both computers don't have to sit on the desk.

I have scoured the internet and run in circles trying to figure everything out and I am running out of patience (and so is my wife) I can't find one tutorial or forum that has helped me.

It took enough time to get my wireless card working with ndiswrapper and everything works now I just need to work out how to configure everything... Is it a hopeless task?

I don't have enough $ to go buy a wireless router right now...

Please help.

---

### Post by dickohead on 2006-05-07
Have you actually tried to run ad-hoc between them yet? Just for file sharing? Because internet connection sharing would be just a step away!

I suggest you set them both to ad-hoc mode and see if you can connect, then ping from each to the other to assure communication, then setup a Samba share and see if you can have access, from there just share the connection from windows (might need to be win XP Pro, home might not do it) and use it from Linux.... I used to do that with a Mandrake machine dual botting with winXP, I shared the connection from it to others, but not with wireless.... don't see why it shouldn't work.

---

### Post by kennethb on 2006-05-08
I think you really need a wireless router; especially if you want to use your laptop away from your desk.

It sounds like you want your Linux laptop to share the Internet connection through your Windows XP box; is that correct? If this is what you are trying to do, then I don't know if Windows XP allows this.

Here is a descpription of my setup:

The broadband cable goes into a cable-modem; the cabel-modem goes into a wireless router (Apple Airport Extreeme Base Station); the wireless router goes into a 5 port hub. The 5 port hub feeds 2 PCs via wired ethernet. The wireless router feeds 2 desktop Macs and 2 laptops (one Mac and one Linux).

Do you want to use your laptop via wireless to the Internet?

---

### Post by louis_nichols on 2006-05-08
Windows will totally allow him to share his internet connection via wireless. I've done it and it works great.

I've always wondered if Ubuntu will do the same, but unfortunatelly I don't have the hardware to test such a configuration.

Dickohead is right: take it one step at a time! Did you already configure an ad-hoc wireless connection in XP? Does the wireless card under Ubuntu detect it?

---

### Post by yakkob on 2006-05-08
Okay my setup 

> internet-> Hub ->Ubuntu Desktop
                     [INDENT][INDENT]| ->win xp home[/INDENT][/INDENT]
This is what I want to do.

> internet -> hub -> ubuntu desktop -> wireless ad-hoc -> win xp home.


I was hoping it would be possible.  
So ad-hoc network them.  I need some help with that... A good tutorial might do.  If you know of one.

Then I should be able to share the internet with Samba?  I setup Samba with the wired connection, it is quite easy with Ubuntu, I was impressed, I've tried with with Suse, and red hat, and Fedora before and always got swamped.

I hope this clears things up.

---

### Post by yakkob on 2006-05-08
I woke up this morning and it seems my wireless network card has disappeared from ubunut entirely.  It was working fine. Now I can't find it in either device manager and when I run ndiswrapper -l there is nothing there either.

Have you ever heard of that happening before?

It's a d-link dwl-g510 with Marvell W8300 chipset.

Help please.

---


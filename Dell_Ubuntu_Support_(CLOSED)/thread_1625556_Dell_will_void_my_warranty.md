---
title: "Dell will void my warranty"
date: 2010-11-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RochJer on 2010-11-19
I contacted Dell Technical Support and asked question if it will void my warranty if I downloaded/install the ubuntu. They said yes so what is your suggestion or steps I need to do if I really want to install ubuntu? 

Thanks.

---

### Post by e79 on 2010-11-19
From my point of view, this is not a problem. If Dell voids the warranty simply because you installed a different Operating System, lets just fool them ! Their warranty covers only the 'hardware part' of the laptop if I'm not mistaken, so if your Windows would go haywire, they would not help you anyway; so lets proceed :

1. Check if your laptop came with some Restore-Disks or Factory-Reset disks, that would allow you to quickly reformat to Windows in a usable state if you need, and  if so, skip step 2.
2. If not, download and burn a CloneZilla CD and clone an image of you whole hard drive having Windows, storing it onto an external drive per example, so you can revert to it in case you need to ship it back to Dell.
3. Download Ubuntu goodness, burn your disk and make sure it is fully compatible with your laptop, using the LiveCD in 'Try Mode'. If you are satisfied with the results, go ahead, install it and enjoy the Freedom !

One or two things you might want to take into consideration :
1. If you already have data on your Windows installation, back it up !
2. Always back up your Home Directory as often as possible in case you need to reformat it in Windows and ship it to Dell for repair...  :p

BTW, shame on Dell  for giving such poor service, I would personally not buy from them again just for that fact...but this is only my opinion !

Hope this helps

---

### Post by alienprdkt on 2010-11-19
> **RochJer said:**
> I contacted Dell Technical Support and asked question if it will void my warranty if I downloaded/install the ubuntu. They said yes so what is your suggestion or steps I need to do if I really want to install ubuntu? 

Thanks.

Odd I just had dell come out last month and service one of our servers that initially came with windows 2003 server but I had put ubuntu 8.04 server on it. They replaced mother board for free and it still has till 2012 for the warranty!

---

### Post by gbrainin on 2010-11-19
Dell sells computers with Ubuntu built in, and I can tell you from personal experience that they are warranted (I had a defective part which was exchanged under warranty).

Why does changing the OS on a system that you bought with Windows void the warranty?  My theory is that they don't want to have this conversation on their tech support line: "Okay, first go to your Start button." "I don't have a Start button."  Now their support script is broken.

I think e79 is exactly right on how to get around this: Backups.  I believe most Dell systems come with a reinstall partition on the hard drive, so as long as you don't delete or overwrite that partition when you're installing Ubuntu, you can easily recreate a "factory fresh" configuration if you need it in order to get warranty work done.

Also, don't forget that the warranty is usually only one year.  After the first year, there's no warranty to void.

---

### Post by RochJer on 2010-11-19
Thanks I appreciate this. I will do that and I already have the recovery/system discs if something screwed up which I doubt it. I miss the OPEN SOURCE !!! :P

---

### Post by ugm6hr on 2010-11-19
The best advice I have been given is to state that any HD has been removed for reasons of data security.
This obviously works unless the problem is the HD, in which case it wouldn't matter which OS was installed beforehand.
The reason for them stating this is that they don't want to receive lots of phone calls from people struggling with Ubuntu. Often, the first thing they do is re-image the default OS to ensure any fault is not a software issue.

---

### Post by reiki on 2010-11-20
Installing a new operating system will not void your warranty. The Magnuson-Moss Act prevents them from doing this.

"Warrantors cannot require that only branded parts be used with the product in order to retain the warranty.[2] This is commonly referred to as the "tie-in sales" provisions[3], and is frequently mentioned in the context of third-party computer parts, such as memory and hard drives."

...and operating systems.

They CAN, however, have you restore the machine to factory OS before troubleshooting and accepting your claim of warranty repair. 

Easiest way around all this is to shrink the factory OS partition to a very small size (my win7 partition got shrunk to 100GB on my 750GB drive...the rest is Ubuntu) as this allows you to run any windows diagnostics they ask you to run and keeps the factory OS on the machine.

---

### Post by gabriel8a2002 on 2010-11-20
Actually they can.  Specially if they have bought "extended" warranty from places like Assurant.  Assurant insures circuit city(before) and staples, also if they bought it from Office Depot and even Best Buy(assholes!). 

Now...this is kinda a "duh!" thing, but ill tell you guys anyways.  There is NO WAY that they can find out for sure that you added a separate operating system.  What to do if you run into hardware problems?  1-format your entire hard drive and leave it blank, and send the system back(dont tell them that u replaced the operating system) 2-reinstall the OS that it had 3-fry the hard drive  (please verify u got warranty)

I worked in some of these places as a technician.  We are allowed to deny people service IF THEY CHANGED THEIR OS.  Of course we charge $$$ to send ur system to service (we change the OS back and send it to service "duh!") but we dont tell the customer that, we just tell them that their data will go bye bye if it goes to service...


So key words!  DONT TELL DELL U CHANGED UR OS!   IF u did, and you need service, well change it back, format the hard drive, or fry the hard dirve :popcorn:...

---

### Post by SeijiSensei on 2010-11-20
> **alienprdkt said:**
> Odd I just had dell come out last month and service one of our servers that initially came with windows 2003 server but I had put ubuntu 8.04 server on it. They replaced mother board for free and it still has till 2012 for the warranty!

Support for servers and support for residential desktops are very different.  Servers are often sold without an installed OS, and Dell routinely offers Linux as an OS option on servers.  I suspect that you're also paying for a higher level of support both in terms of the price charged for a server and the prices of the warranties as well.  The margins on consumer systems are so narrow that I can believe they limit support to just the system as configured at the factory.

As an example, 3 years of next-business-day onsite support adds $350 to the cost of T510 server that sells for about $600.  For that same $350 you can buy another consumer workstation.

---

### Post by mc4man on 2010-11-20
I've had dell out here several times recently to service 2 1330m laptops and the Os installed has not been a factor. 
Actually a tech will be here Mon to replace a fan unit from either a screwed mobo/fan replacement last tues. or the 'new' fan unit was defective.
Atm that laptop only has ubuntu installed and there is no way Dell is not responsible for the hardware under warranty

A few tips if you remove orig Os rather than dual boot.

If there is a hardware failure that still allows a boot to a visible screen then dell usually provides a utility disk that you can boot to and run tests on any or all hardware. The test will provide an error code - that's all you need to give Dell.
(sometimes also an audio beep - if so leave and let them hear - happened here on a ram with some bad addresses

If they ask if you have an Internet connection for the machine just say no - in some cases they want to remote in, no connection -  no remote.

I've found Dell easy to work with, and willing to replace most anything even when not totally broken, ie. keyboard w/ sticking keys, power adapter that was on the fritz, - usually the support will ask - 'is there anything else'

---

### Post by chee on 2010-11-21
I have an Inspiron 6400 that is well out of it's warrantyor anything like that.  A friend had installed Ubuntu just after the warranty ran out,  he formatted the whole hard drive which got rid of my Windows totally,  so I had no Windows or software discs at all.  I wanted to go back to Windows to use my HVR950Q (I didn't want to mess around with Ubuntu at the time,  that has changed ;) ) so I called Dell and told them the whole story.   Within 3 days I had a full set of software discs (like 10 dvds I think) and all free of charge.  

To be honest,  I really like my laptop and all the service I have had but that last thing was enough to make me buy a Dell again,  they didn't even flinch about sending the discs.

---


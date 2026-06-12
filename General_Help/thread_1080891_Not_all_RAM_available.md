---
title: "Not all RAM available"
date: 2009-02-25
forum: General Help
---

### Post by dwasifar on 2009-02-25
And this one's not a 32-bit OS problem.  :)

I'm trying to set up a friend's old HP ze2000 laptop with Ubuntu.  Things seemed crazy slow, and when I went to System Monitor to see if I could find the holdup, I found it was only reporting 374MB of RAM even though there is 512MB installed.  I swapped DIMMs around for a while without improvement.

System Monitor reports 374MB.  If I boot from live CD and run memtest, that reports 383MB.  The BIOS, however, reports 512MB.

What's going on here?  Hardware fault?  This motherboard should support up to 2GB.

---

### Post by taurus on 2009-02-25
Maybe you have one of those onboard integrated graphic controllers that takes a chunk out of your RAM for video RAM.

---

### Post by manowar689 on 2009-02-25
hello and thank you for posting the 374MB of ram you are seeing is actually the ram in use in realtime which just means that it doesnt need all of it at the specific time you checked it is all and to speed the laptop up i would suggest a lighter distro as ubuntu can be somewhat resource intensive so i would have two suggestins for you either install xubuntu a lighter derivitive of ubuntu or if you dont mind installing drivers from source you could opt for say a netbook distro like easy peasy linux an eee pc distro which is fairly light and offers a nice interface with a solid ubuntu base this is the link 

[http://www.geteasypeasy.com/](http://www.geteasypeasy.com/) 

if you need help please pm me if you like good luck lol

---

### Post by mb_webguy on 2009-02-25
> **manowar689 said:**
> hello and thank you for posting the 374MB of ram you are seeing is actually the ram in use in realtime which just means that it doesnt need all of it at the specific time you checked it is all and to speed the laptop up i would suggest a lighter distro as ubuntu can be somewhat resource intensive so i would have two suggestins for you either install xubuntu a lighter derivitive of ubuntu or if you dont mind installing drivers from source you could opt for say a netbook distro like easy peasy linux an eee pc distro which is fairly light and offers a nice interface with a solid ubuntu base this is the link

Punctuation is our friend. ;)

dwasifar:  You said you were running memtest from the LiveCD.  What happens when you run memtest using the GRUB menu option?

---

### Post by dwasifar on 2009-02-26
> **manowar689 said:**
> hello and thank you for posting the 374MB of ram you are seeing is actually the ram in use in realtime which just means that it doesnt need all of it at the specific time you checked it is all and to speed the laptop up i would suggest a lighter distro as ubuntu can be somewhat resource intensive so i would have two suggestins for you either install xubuntu a lighter derivitive of ubuntu or if you dont mind installing drivers from source you could opt for say a netbook distro like easy peasy linux an eee pc distro which is fairly light and offers a nice interface with a solid ubuntu base this is the link 

[http://www.geteasypeasy.com/](http://www.geteasypeasy.com/) 

if you need help please pm me if you like good luck lol

Um, no.  I know the difference between available RAM and RAM in use; it's pretty easy to tell the difference in system monitor.  This system should be capable of running regular Ubuntu without going to a small-footprint distro.  Thanks just the same.

---

### Post by dwasifar on 2009-02-26
> **mb_webguy said:**
> Punctuation is our friend. ;)

dwasifar:  You said you were running memtest from the LiveCD.  What happens when you run memtest using the GRUB menu option?

Good question.  I assume it would report 383 like the live CD does.  I'll try it and report back later.

---

### Post by teh.chicken on 2009-02-26
Hi, I am having a similar problem... I have 4gb of ram installed (on-board graphics uses 512mb) but ubuntu only shows 2.5gb. I am running 32 bit, could this be the problem?
Thanks

---

### Post by kanikilu on 2009-02-26
> **dwasifar said:**
> Good question.  I assume it would report 383 like the live CD does.  I'll try it and report back later. Also maybe try testing the modules individually to make sure they are each working and reporting the correct size.

Also, I happen to notice that 256+128 is 384, obvious question, but are you **sure** you have 2x256 and not 1x256 and 1x128? I know you said the BIOS is reporting 512, so that's probably not the case, but it might be worth double-checking...

---

### Post by issih on 2009-02-26
My mother used to use one of those, and if I remember rightly the amount of ram used by the video card is set in the bios, and windows certainly only reported the remainder as being available.

So assuming your bios is set to use 128Mb of your 512 then this all adds up.

Check the bios settings to see whats what.

Hope that helps

---

### Post by brokenLockpick on 2009-02-27
> **teh.chicken said:**
> Hi, I am having a similar problem... I have 4gb of ram installed (on-board graphics uses 512mb) but ubuntu only shows 2.5gb. I am running 32 bit, could this be the problem?
Thanks

Fairly common, and yes there is a limit to what a 32bit addressing scheme can manage. It's further complicated because even if there are memory chips on a discreet graphics card, as it's been explained to me the system still must assign addresses to that memory so it subtracts from available addresses for system ram.

This is similar to the cause of the 137GB limit on hard drives which seems like an arbitrary number but is actually 128GiB as was due to the address length only being suitable to map 128GiB (true gigabytes)

---


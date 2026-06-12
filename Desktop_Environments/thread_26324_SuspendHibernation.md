---
title: "Suspend/Hibernation"
date: 2005-04-12
forum: Desktop Environments
---

### Post by Jerrac on 2005-04-12
I am sure there is a topic out there that addresses this problem, but I couldn't find it. So here we go.

I can suspend and hibernate my Sony Vaio FRV37 laptop fine. But it will not start back up. When I start it back up from suspend, it just gives me a blank screen and I have to reboot. When I wake it up from hibernation, it gets to a certain point, and hangs. It as this noise at the top of the screen.

So, what can I do to fix this?

---

### Post by Manny C on 2005-04-12
Hi

I thought that I would let you know that the module in Linux (ACPI) that controls suspend (in particular) is still very much a work in progress.

Namely, good luck getting suspend to work...hibernate support may be possible...do a google search for ACPI and your model of laptop.

--
Kind Regards
Manny C

---

### Post by coldsalmon on 2005-04-12
I also get a blank screen when I come out of suspend, but I just press CTRL+F7 and I get back to my desktop.  Does this work for you?

--C

---

### Post by Marc Higgins on 2005-04-13
have a samsung sens x05, hibernation works a treat but suspend, well not yet. It also detected my have a samsung sens x05 laptop, hibernation works a treat but suspend... well not yet. The hibernation looks a bit like it will do the full reboot but if you give it a chance (~8-10 seconds) it does the biz. Ubuntu also detected my wireless lan & HP MFD scanner/copier/printer/coffee_machine :-)  I couldn't get any of these working on FDC3 & because I only have 256 meg of ram on FDC3 everything was soooooo sloooooow. All in all a very slick, fast, stable distro, only issue is i'm having an issue getting skype to work

---

### Post by ObjectWiz on 2005-04-14
Hi there,

I have an Acer Aspire 1524WLMi Athlon 64 and hibernate seems to work well.  Suspend does work... the laptop does suspend and the relevant light comes on.  My question is:  how do I wake it up?  The power button doesn't work and I haven't been able to configure the keyboard so my 'Zz' button doesn't work either...

*sniff, sob*  ;-)

Peter.

---

### Post by Jerrac on 2005-04-17
[QUOTE=coldsalmon]I also get a blank screen when I come out of suspend, but I just press CTRL+F7 and I get back to my desktop.  Does this work for you?

--C[/QUOTE]
Well it doesn't work for me...

---

### Post by Johan on 2005-04-18
In some cases where acpi doesn't work, apm will do the job. Try searching the forums for apm for instructions for how to enable apm (and disable acpi).

---

### Post by Jerrac on 2005-04-18
[QUOTE=Johan]In some cases where acpi doesn't work, apm will do the job. Try searching the forums for apm for instructions for how to enable apm (and disable acpi).[/QUOTE]
Eh, I was under the impression that newer laptops didn't even have apm... Is that true?

---

### Post by Jerrac on 2005-04-20
Well, I just tried disabling acpi and only having apm. Didn't work. Then I tried only acpi, didn't work. 

I would really like to get this working...

---

### Post by Jerrac on 2005-04-28
Just giving this a little bump... Anyone have any ideas?

---

### Post by erzhong on 2005-04-30
I am using IBM t42 and hibernation/suspend works fine.  

I just switched from Mandrake 10.1 Official to Kubuntu.  I think that the hibernation problem may be caused by the size of the swap partition.  My T42 had 512 MB memory when I bought it.  With a 1GB swap partition, hibernation worked.  After another 512 GB memory was added, the hibernation would not work any more.  The swap partition is less than Memory+Graphic Memory, and I guess that was the reason.  When I decided to try Kubuntu, I increased the size of the swap partition to 1.2GB > Memory+Graphic Memory, and hibernation works.

---

### Post by Jerrac on 2005-04-30
Hmm.... Mine is 2 megs short of the 512 of ram I have... I will try resizing it.

Does your suspend work?

---

### Post by erzhong on 2005-05-05
Suspend works fine on my T42.  But I have not done a thorough test.

---

### Post by h2gofast on 2005-05-09
[QUOTE=Jerrac]Just giving this a little bump... Anyone have any ideas?[/QUOTE]
 panasonic toughbook pII 366.  having the same problems as everyone else.  hibernate worked under debian sid.

---

### Post by Jerrac on 2005-06-03
Well, I still haven't gotten it working on my laptop. I have the latest Ubuntu and resized my swap area to 1gb when installing. Which somehow changed to 900-something... Still doesn't work. I have come to the conclusion that my laptop has some weird hardware or something that won't work with linux for hibernation. :(

---

### Post by dejitarob on 2005-06-03
[QUOTE=Manny C]Hi

I thought that I would let you know that the module in Linux (ACPI) that controls suspend (in particular) is still very much a work in progress.

Namely, good luck getting suspend to work...hibernate support may be possible...do a google search for ACPI and your model of laptop.

--
Kind Regards
Manny C[/QUOTE]
Suspend and hibernation worked for me in Gnome on my Inspiron 9300. In KDE, I get the similar blank screen results described by Jerrac.

---

### Post by Jerrac on 2005-06-16
Something new on hibernation that I just found: [http://wojas.vvtp.tudelft.nl/acertm/](http://wojas.vvtp.tudelft.nl/acertm/)

The person who wrote that suspects that the Acer hidden partition is for the suspend to disk stuff, I have a similar partiton on my Sony laptop. Could that be part of the reason I cannot get it to recover from hibernation?

---

### Post by stoft on 2005-08-16
It doesn't seem related but this seems to be a good place to put it for future reference and help. I'm running a standard Debian Sarge on my Toshiba Satellite A50 with suspend under KDE working almost well. I've had two major problems, the first one is that it would try to suspend but pop right back out again. This one I solved by first unloading the uhci_hcd module (google for it and you'll find references on the topic, this is a known problem in kernel 2.6.8 and a kernel upgrade - in my case to 2.6.11 - handles it).  The other  problem is a restart of the x-server when coming out of suspend, this one I haven't solved yet. Hibernate did not work in 2.6.8 but I'll try it soon in 2.6.11. I hope this helps someone along.

---

### Post by GeneralZod on 2005-08-16
I highly recommend that you file a bug report on this; the devs tend not to read the forums, so any bugs reported here tend to get lost.  Filing a bug report means that there is a higher chance that hibernate will work "out of the box" in future releases - which is one of Ubuntu's stated goals.  See e.g. [http://ubuntuforums.org/showthread.php?t=56977](http://ubuntuforums.org/showthread.php?t=56977)

---


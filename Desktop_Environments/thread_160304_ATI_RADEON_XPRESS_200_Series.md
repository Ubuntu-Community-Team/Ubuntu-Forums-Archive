---
title: "ATI RADEON XPRESS 200 Series"
date: 2006-04-14
forum: Desktop Environments
---

### Post by equinox55 on 2006-04-14
I was trying to use the ubuntu live cd to try out the linux system. But when i rebotted a got a black screen with a whole bunch of letters and stuff.  I stoped and I could not do anything, i had to eject the cd and restart the pc.  How to i get pass this?  Any ideas.

---

### Post by tay on 2006-04-15
Upon booting I hit the default boot screen, booted the linux kernel, and the went to a black screen.  ( no letters though...)

I also tried the special boot paramaters with no luck also.

Running an ATI Radeon XPRESS 200M Series.

---

### Post by equinox55 on 2006-04-16
Why are you hijacking on my thread?  Go and start a new topic!:evil:

---

### Post by jocko96b on 2006-04-18
[QUOTE=tay]Upon booting I hit the default boot screen, booted the linux kernel, and the went to a black screen.  ( no letters though...)

I also tried the special boot paramaters with no luck also.

Running an ATI Radeon XPRESS 200M Series.[/QUOTE]


I have the exact same graphics adapter in my laptop (HP Pavilion zv6000) and I get the exact same result.  Same results with both the Live CD and Install CD.  I did dedicated in the bios SidePort + UMA an additional 128MB of system ram, but with no change.   From what little I have read, ATI doesn't usually play well with linux...

---

### Post by pbaehr on 2006-04-18
I have that card. (Not the M one, the desktop one) I believe I had to use "noapic nolapic" as boot parameters to get it to work. I don't actually know what they do, but it fixed the problem.

You will, however, experience more trouble with that card further down the road. It probably will not boot into a graphical interface by default and I have yet to encounter a person with that card who successfully got their 3d acceleration working. I ended up buying an NVIDIA PCI express card to use instead.

Also, I should mention, I was installing, not using a live CD.

---

### Post by jocko96b on 2006-04-19
I looked on ATI's website, and aparently they have drivers for linux, and the Radeon Xpress 200M series is listed as supported in release notes.  Im still very new to all this, but wouldn't the drivers they offer get the 3d acceleration working?  Now to go forth and try to figure out if the initial bootup is hanging because of the video drivers, then how to get around that problem...

ATI's link is: [https://support.ati.com/ics/support/KBAnswer.asp?questionID=1176](https://support.ati.com/ics/support/KBAnswer.asp?questionID=1176)

---

### Post by jocko96b on 2006-04-19
Hey, got it to install.  I found a howto guide (props to [email]ruudbeukema@gmail.com[/email] for the guide) for the HP zv6251ea laptop to install ubuntu.  I don't have the exact same model, but I do have a 6000 series, and so far the howto has worked.  On the boot, type 'linux vga=771' (without the quotes) and it worked like a charm for me.  oh, the link to the howto is:

[http://members.home.nl/ruudbeukema/techniek/linux/](http://members.home.nl/ruudbeukema/techniek/linux/)

So far, so good for me.  Best of luck to you guys.

---

### Post by tay on 2006-04-20
[QUOTE=davisbaumung]Why are you hijacking on my thread?  Go and start a new topic!:evil:[/QUOTE]

chill out man.. we have the same exact problem.. same exact card. how is that hijacking?

---

### Post by tay on 2006-04-20
[QUOTE=jocko96b]I looked on ATI's website, and aparently they have drivers for linux, and the Radeon Xpress 200M series is listed as supported in release notes.  Im still very new to all this, but wouldn't the drivers they offer get the 3d acceleration working?  Now to go forth and try to figure out if the initial bootup is hanging because of the video drivers, then how to get around that problem...

ATI's link is: [https://support.ati.com/ics/support/KBAnswer.asp?questionID=1176](https://support.ati.com/ics/support/KBAnswer.asp?questionID=1176)[/QUOTE]

yeah.. i found alot of how-tos here for config xserver with ATI.. but still no luck with the special boot parameters.  I will go try vga=771 and noapic nolapic again, and follow up.

---

### Post by equinox55 on 2006-04-20
Sorry for that I was sick and angre that day? Reviewing the rest of it

---

### Post by equinox55 on 2006-04-20
I'am so lost at what all you guys are saying!

---

### Post by tay on 2006-04-21
boot:live-expert vga=771 noapic nolapic

failed to boot.

I noticed it also failed to synchronize ntp also.

it hung worse after failing also.. i pressed ctrl-alt-del and it ejected the cd, and hung at the error message screen.  I then had to take out the battery, and flip the switch on my surge protector

---

### Post by swawryk on 2006-04-21
[QUOTE=davisbaumung]I was trying to use the ubuntu live cd to try out the linux system. But when i rebotted a got a black screen with a whole bunch of letters and stuff.  I stoped and I could not do anything, i had to eject the cd and restart the pc.  How to i get pass this?  Any ideas.[/QUOTE]

I had exactly the same problem with the ubuntu 5.10 live CD on a Compaq Presario with a RADEON 200M.  To see if this problem has been dealt with on more recent releases I have just tried the live CD for 6.06 (Dapper Drake release 6).  It didn't have this problem for me.  So far so good ...

:D 
Steve

---

### Post by BobSock on 2006-04-22
I'm having the same problem. I disabled APTI through my bios and was able to install it correctly but startx won't work, it gives me a video card error. 
[Running an ATI radeon xpress 200 integrated card]
So is there a way to get GUI support with this card? Or if I download the install CD Dapper Drake does this support my card?
Currently I have Kubntu Breezy 5.10, switching from SuSE because I heard Ubuntu is more friendly.

---

### Post by swawryk on 2006-04-22
[QUOTE=BobSock][Running an ATI radeon xpress 200 integrated card]
So is there a way to get GUI support with this card? Or if I download the install CD Dapper Drake does this support my card?
Currently I have Kubntu Breezy 5.10, switching from SuSE because I heard Ubuntu is more friendly.[/QUOTE]

I have not found any support forthcoming to fix this problem with 5.10.  I have been using the live CDs so far.  Only planning to install once I'm satisfied.

I did find that this problem disappeared for me with the 6.06 live CD.  So I do recommend download Dapper Drake release 6.  I personally wouldn't recommend going straight for the install CD, but that might be just me.

:) 
Steve

---

### Post by BobSock on 2006-04-22
Thanks for the fast reply. I have a small spare harddrive that I test a new install on first so I think I will go with the full install and see how it goes. That way there is nothing to lose. :)

---

### Post by Sidk on 2006-04-22
There is no real work around for this on you lappy. I've got a hp dv 5000 and the only way you will get the live cd to work is to edit the xorg.conf file after it's booted up and change "ati" to "vesa". Problem is that when you reboot it, you will loose the setting. That should get you at least to the desktop.

If you're using Dapper then just give it a "live nolapic" at boot and dapper should see the card ok. You shouldn't need to pass the vga=771 or the noapic command.

---

### Post by equinox55 on 2006-04-23
All right i will wait till may to order my new cds the 6. what ever then I will see if it works

---

### Post by tay on 2006-05-06
dapper live worked on my toshiba sattelite...
(somewhat)  

I'm done with this conversation and moving all further discussion to the dappper forums.

---


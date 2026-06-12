---
title: "Inspiron 1720  - Nightmare please help"
date: 2007-08-01
forum: Dell  Ubuntu Support
---

### Post by warwon on 2007-08-01
I used to have really good luck with hardware and Ubuntu.

I got a Inspiron 1729 as I had the supported hardware before and noticed that most of it should be fine minus some tweaking.

I got two hours of sleep last night, I'm gloggy for work and very upset at how hard it was to get anything working and I feel bad for my girlfriend who I was setting this up for as only half the stuff works.

I was able to restore the Nvidia card even through Ubuntu never detected my card at first, it was a   128MB NVIDIA® Ge-Force&#153; 8400M GS which is not a on-board video card by any-means.

I was forced to use Envy, to installed 3D card into the distro.

I've been using Linux for a few years and this reminds me of the old days of trying to get stuff to work.

Lets start with what doesn't work.

- Dell Wireless 1390 802.11g Mini-Card
- Dell Wireless 355 Blue-tooth Internal (2.0 + Enhanced Data Rate) 
- Ricoh SD card
- DVD drive

That's a big list of broken hardware for Ubuntu, and I know some of that is my fault like the wireless card should have gone with the Intel, well my mistake I thought Ubuntu was better for wireless support I was wrong.

Issues:

Wireless 1390 during the default install it was detected, the driver was listed under the hardware.

But no wireless points were listed, nor was I able to configure the card to detect any wireless points.

So I went through the process listed elsewhere on the forum to install the ndiswrapper, removing the old driver, and setting the ndiswrapper to the new driver, and for the ndiswrapper to be added in the modules configuration file.

Check that finally worked, I got a new tool listed under the Internet options Wicifg or something along those lines.

It lists all the networks in my area great so I was almost there.

I test it on the non-WPA router to make sure it works. It then tries to connect then when trying to get a IP it goes around for about 3-5 minutes then nothing.

So I try the WPA router that is working did work on the same wireless card from windows, still unable to get the wireless card in Linux to detect and configure the IP address from the Router.

So I try the network manager under Administrative tools my wireless card is there as it was before, but this time under proprieties the different networks in my area are listed. So I setup the WPA network in my apartment. Nothing it doesn't even try to configure the card, it takes all the settings and it now only has a cancel button no "okay".

So I have no idea how to get this wireless card to work nothing I try works, and the closer I get the further away I am.

Nest I found that my DVD drive in the laptop does work. How is this possible? I was able to install Ubuntu but when the distro actually boots it lists the CD drive (as per usual the hardware is detected but nothing works), when I go to use the DVD drive it gives me a failure to mount error. Sighs I have no idea

For the Ricoh SD card the hardware again was detected but nothing worked. I did try to add tifm_sd to the modules as I've been told that this usually fixes the issue. Yah right no luck again.

So here I have a new laptop that has no DVD drive, no wireless card, no card reader. I have a old crappy laptop and Ubuntu work right away on it, frak.

Anyhelp? please

---

### Post by dekar100 on 2007-08-01
Ok DVDROM  edit the /etc/modules and add this module  piix, reboot the system, 
bye

---

### Post by aeo24 on 2007-08-01
This post should answer most of your questions:

[http://ubuntuforums.org/showthread.php?t=501195&highlight=inspiron+1420](http://ubuntuforums.org/showthread.php?t=501195&highlight=inspiron+1420)

The above post shows you how to install, get the DVD working as well as many other problems that come with the new inspirons.

---

### Post by warwon on 2007-08-01
No I stop using Linux for about a year just cause of my current job. And I remeber when Envy first came out, and how badly it first killed my old distro a year or two ago, was just scared of it ;)

Seems to work  nice now

---

### Post by warwon on 2007-08-01
That link above looks amazing I don't even want to ask myself how I missed that last night.

:popcorn:

---

### Post by warwon on 2007-08-01
Looks like the biggest issue not covered in that document is how to get that wireless card setup as mine is not a Intel

---

### Post by aeo24 on 2007-08-02
Your card will work it just takes some fiddling with as i see you have done the BROADCOM cards seem to always be a hassle. If you just paste the exact card name (dell 1390?) or whatever in to the search box you will get a ton of link you should be able to find your answer fairly easily, i know i was debating getting the broadcom but then realized $40 CDN was worth my time and i got the intel card.

---

### Post by warwon on 2007-08-02
welll here's the update from last night.

1. I ran into a awful issue with the Ndiswrapper refusing to re-compile I think somehow when I was going back over the link to the keneral headers was lost.

So I gave up and reformatted the system as at this point it was beyond my skill to repair the damage, and I couldn't find much of the similar problem, I tried various IRC options and no one really cared.

So after reformatting and updating the the Ubuntu to the lastest kernels in the update manager, rebooting.

I was able to quickly go through a guide to install the Dell Wireless 1390 broadcom wireless and it working within ten mins of a new install.

Then I was to get the video card back up and running in another ten mins with Envy, most that time was the downloading.

I was able to get the card reader working another ten mins after that, I was on my A-game last night I guess :P

I got Midi configured as this is going to be a music production lab for my girlfreind.

Then I was able to add some code to get the Intel sound card working.

So everything works minus one things. The sound is beyond usual.

I haven't had a whole lot of time to check things out but eveythinig is so choppy...

Any ideas?

---

### Post by warwon on 2007-08-02
Also got the DVD-Rom working with full-playback wasn't difficult

---

### Post by aeo24 on 2007-08-02
No idea about the sound all though i know there is a sound section in the link i posted a few replies back. I have yet to actully receive my inspiron 1420 from dell( it just shipped yesterday!) but i took a lot of time to read these forums in an attempt to make my life easier.  I'm not exactly sure which sound problem you are having but i haven't read to much about any problems. As i said read that post i linked above. Hope you get it all working!

Also how did you install it? the alternate CD or the regular 7.04 CD just wondering.

---

### Post by warwon on 2007-08-02
it was in the ubuntu studio, which is pretty much the same minus the kernal is a bit different but shouldn't affect the sound as bad as it is

---


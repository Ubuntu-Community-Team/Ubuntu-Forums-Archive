---
title: "Beryl on 7.04 with ATi"
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by Mazen on 2007-04-30
Hi all, 
is there a HOW-TO for installing beryl on Feisty with an ATI card?
and if not i have a weird question, might the repos for edgy work on feisty?
thanks

---

### Post by Snowcat on 2007-04-30
Here you go:

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

---

### Post by kittyhawk63 on 2007-04-30
> **Snowcat said:**
> Here you go:

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

Thanks for this page, Snowcat.
kh

---

### Post by paulfife on 2007-04-30
Just to see if it would work I just tried installing it from Synaptic (did a search on beryl) and everything worked just fine for me. I'm still pretty new to everything, so I'm not sure if I'm missing something by doing this but it worked for me. I'm impressed that I was able to do this without touching a config file.

After installing I started the Beryl Manager and switched the window manager and I was in business. I tried both the open source and restricted driver and found the restricted driver didn't work properly for me. I have a Radeon 9800.

---

### Post by oomingmak on 2007-04-30
> **Snowcat said:**
> Here you go:

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")
Thanks Snowcat, that is an excellent link.

I have been trying to cobble together instructions from various sources (much of which is out of date and won't work unless you to figure out what version numbers and sources entries you need to alter when following their examples).

I note that the link you provided says that X1900 series cards are "unsupported". What exactly does that mean in this context?

There are threads on here where people say that they've got Beryl working on an X1950 card, so I'm guessing that "unsupported" can't mean that it doesn't work at all on those cards.

---

### Post by Mazen on 2007-04-30
Thanks Snowcat,

---

### Post by Mazen on 2007-04-30
> **oomingmak said:**
> Thanks Snowcat, that is an excellent link.

I have been trying to cobble together instructions from various sources (much of which is out of date and won't work unless you to figure out what version numbers and sources entries you need to alter when following their examples).

I note that the link you provided says that X1900 series cards are "unsupported". What exactly does that mean in this context?

There are threads on here where people say that they've got Beryl working on an X1950 card, so I'm guessing that "unsupported" can't mean that it doesn't work at all on those cards.

Well i guess the "unsupported" in the Open Source world means that, you can figure out how to do it yourself but the people who release beryl won't take any complain from you if it doesn't work, but as u said it doesn't mean that it DOESN'T work, no on the contrary it will, most probably, work but with some personal touches and creativity not "Legal" stuff given by the creators....hope u get my point lol
Enjoy Beryl,

---

### Post by oomingmak on 2007-04-30
> **Mazen said:**
> Well i guess the "unsupported" in the Open Source world means that, you can figure out how to do it yourself but the people who release beryl won't take any complain from you if it doesn't work, but as u said it doesn't mean that it DOESN'T work, no on the contrary it will, most probably, work but with some personal touches and creativity not "Legal" stuff given by the creators....hope u get my point lol
Yes, I do understand now. Thanks for taking the time to explain.

---

### Post by Mazen on 2007-05-01
i installed beryl with these HOWTOs and i get all sorts of weird colors on the screen and lines all over the place when i run it, it seems to be working fine, like the cube is tuning and everything but these lines hide everything,any idea what that is?
thanks

---

### Post by aoanla on 2007-05-02
> **oomingmak said:**
> Thanks Snowcat, that is an excellent link.

I have been trying to cobble together instructions from various sources (much of which is out of date and won't work unless you to figure out what version numbers and sources entries you need to alter when following their examples).

I note that the link you provided says that X1900 series cards are "unsupported". What exactly does that mean in this context?

There are threads on here where people say that they've got Beryl working on an X1950 card, so I'm guessing that "unsupported" can't mean that it doesn't work at all on those cards.

Actually, the term "unsupported" in this context means "doesn't work with", as far as I know. Snowcat's link is for getting Beryl to work with the open-source radeon driver, which doesn't work with the most modern Ati cards well (at lot of the problem being that they're having to work out how to write it by reverse-engineering what the fglrx driver does), but *does* support AIGLX. AIGLX is the easiest to use (and most efficient) means of enabling 3d accelerated desktop effects, and so you should use it if possible.

I believe that all of the X1950 owners are using the (not exactly performant, but official) fglrx drivers from Ati themselves. These drivers do officially support the X1950 and all the other newer cards, but they *don't* support AIGLX yet. Therefore it is trickier to get Beryl to work with them, because you can't have Composition turned on in your xorg.conf file - you have to get XGL working instead. There are, as I recall, a few threads on this issue on the forums, if you search for something like "Beryl XGL fglrx" or something.

---

### Post by BaffledMollusc on 2007-05-02
> **Mazen said:**
> Hi all, 
is there a HOW-TO for installing beryl on Feisty with an ATI card?
and if not i have a weird question, might the repos for edgy work on feisty?
thanks

These are the instructions I used to make Beryl work with my ATI X800 Pro: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy)

They worked like a charm.

---

### Post by kittyhawk63 on 2007-05-02
> **BaffledMollusc said:**
> These are the instructions I used to make Beryl work with my ATI X800 Pro: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy)
They worked like a charm.

BaffledMollusc,
I got these instructions to work on an ATI Radeon9200 SE video card.
The only thing that I notice is that there is a lag time in the graphics. In other words, things take longer to happen. I have the cube but I am not sure how to make it smaller. It takes up the entire monitor screen.
kh

Edit: Figured out those items giving me problems. Everything okay now except there is a very short lag time with Beryl. I just have to be a little less impatient. It works, and that is what I wanted. When I am in a hurry, I will turn off Beryl.

---

### Post by oomingmak on 2007-05-02
> **aoanla said:**
> Actually, the term "unsupported" in this context means "doesn't work with", as far as I know. Snowcat's link is for getting Beryl to work with the open-source radeon driver, which doesn't work with the most modern Ati cards well (at lot of the problem being that they're having to work out how to write it by reverse-engineering what the fglrx driver does), but *does* support AIGLX. AIGLX is the easiest to use (and most efficient) means of enabling 3d accelerated desktop effects, and so you should use it if possible.

I believe that all of the X1950 owners are using the (not exactly performant, but official) fglrx drivers from Ati themselves. These drivers do officially support the X1950 and all the other newer cards, but they *don't* support AIGLX yet. Therefore it is trickier to get Beryl to work with them, because you can't have Composition turned on in your xorg.conf file - you have to get XGL working instead. There are, as I recall, a few threads on this issue on the forums, if you search for something like "Beryl XGL fglrx" or something.
Thanks for your detailed explanation. 

What you say certainly explains all the grief that I've been having trying to get Beryl to work on my system. I've spent the last few days trying to get AIGLX to work (because I'd had no luck after weeks of attempts with fglrx), but given the card that I am using I'm clearly I'm wasting my time and should go back to trying fglrx.

To be honest all this XGL, AIGLX, FGLRX stuff is really confusing to me (I'm only just starting out on Linux), but least I know what to look out for know when seeking out appropriate tutorials for my system.

Thank you.

---

### Post by livesys on 2007-05-02
Beryl on Ubuntu 7.04 Feisty Fawn with ATI

If you own one of these ATI Radeon Card below:

    * 7000 / rv100 based cards.
    * 7200 / R100 based cards.
    * 7500 / rv200 based cards.
    * 8X00 / R200 based cards.
    * 9000 / rv250 based cards.
    * 9100 / R200 based cards.
    * 9200 / rv280 based cards.

    * 9500 / R300 based cards.
    * 9600 / rv350 or rv360 based cards.
    * 9700 / R300 based cards.
    * 9800 / R350 or R360 based cards.
    * X300 / rv370 based cards.
    * X600 / rv380 based cards.
    * X700 / rv410 based cards.
    * X800 / R420 or R423 or R430 or R480 based cards.
    * X850 / R480 or R481 based cards.

then you want to use "AIGLX" for Beryl because the driver is built-into Ubuntu 7.04 Feisty Fawn.  It is also much easier to set-up and less cpu-intensive.
Follow this guide:

> **Snowcat said:**
> Here you go:

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")


----------------------------------------------------

If you own one of these ATI Radeon Card below:

    * X1300 / R515 based cards.
    * X1600 / R530 based cards.
    * X1800 / R520 based cards.
    * X1900 / R580 based cards.
or one of the newer 
    *X1350 / X1650 / X1950 cards

then you want to use "glx + fglrx" for Beryl.  It is much more complicated to setup as well as more cpu-intensive.  However, it is the only way for those unlucky ATI owners :(
Follow this guide:

> **BaffledMollusc said:**
> These are the instructions I used to make Beryl work with my ATI X800 Pro: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy)


---------------------------------------------------------------

Why does this have to be so complicated?

Why does people keep pointing newbies to using the ATI proprietary driver when they can easily use the built-in open-source driver to run Beryl?

Why is Unbuntu's developers not coming up with a nice solution (a 3D Desktop Wizzard) to end this madness?



kittyhawk63,

Did you try using the link that Snowcat posted?  

> **Snowcat said:**
> Here you go:

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")


The "AIGLX + Beryl" combination is much less CPU-intensive than "glx + fglrx + Beryl"

---

### Post by oomingmak on 2007-05-03
Livesys, thank you for the additional clarification. 

Your message is another great example (like aoanla's) of genuinely useful and easy to understand information that lets users know which method they should be trying to use and why. 

If only there were more posts like this (rather than people just pasting links to out of date instruction guides that are in no way suitable for the card that you've asked for help with).


> **livesys said:**
> 
Why does this have to be so complicated?

Why does people keep pointing newbies to using the ATI proprietary driver when they can easily use the built-in open-source driver to run Beryl?

Why is Unbuntu's developers not coming up with a nice solution (a 3D Desktop Wizzard) to end this madness?


Surely it can't be hard to update the documentation for time to time (it's not like they're having to develop program code or anything) but I've seen so many guides with edgy repositories or incorrect ATI version numbers in relation to the download link given for the drivers, not to mention loads of entries that are specific to the computer of the guy who wrote the guide (all of which have caused problems for me when trying to follow these instruction guides).

---

### Post by nandotron on 2007-05-05
[QUOTE=livesys;2581839]Beryl on Ubuntu 7.04 Feisty Fawn with ATI

If you own one of these ATI Radeon Card below:

    * 7000 / rv100 based cards.
    * 7200 / R100 based cards.
    * 7500 / rv200 based cards.
    * 8X00 / R200 based cards.
    * 9000 / rv250 based cards.
    * 9100 / R200 based cards.
    * 9200 / rv280 based cards.

    * 9500 / R300 based cards.
    * 9600 / rv350 or rv360 based cards.
    * 9700 / R300 based cards.
    * 9800 / R350 or R360 based cards.
    * X300 / rv370 based cards.
    * X600 / rv380 based cards.
    * X700 / rv410 based cards.
    * X800 / R420 or R423 or R430 or R480 based cards.
    * X850 / R480 or R481 based cards.

then you want to use "AIGLX" for Beryl because the driver is built-into Ubuntu 7.04 Feisty Fawn.  It is also much easier to set-up and less cpu-intensive.
Follow this guide:




----------------------------------------------------

If you own one of these ATI Radeon Card below:

    * X1300 / R515 based cards.
    * X1600 / R530 based cards.
    * X1800 / R520 based cards.
    * X1900 / R580 based cards.
or one of the newer 
    *X1350 / X1650 / X1950 cards

then you want to use "glx + fglrx" for Beryl.  It is much more complicated to setup as well as more cpu-intensive.  However, it is the only way for those unlucky ATI owners :(
Follow this guide:



---------------------------------------------------------------

Hi,

does anyone know if the x1400 graphics card will work with aiglx?  havent see it listed. Thanks!

---

### Post by [ajax] on 2007-05-05
This worked for me:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

---

### Post by livesys on 2007-05-05
> **nandotron said:**
> 

Hi,

does anyone know if the x1400 graphics card will work with aiglx?  havent see it listed. Thanks!


It pretty safe to say that the newer ATI Radeon X1xxx series is not supported under aiglx so you will need glx + fglrx for your X1400.

This video card is quite popular in notebook system so just do a forum search for X1400 and you should see many threads that assist you with installation and troubleshooting.  Good luck :)

---

### Post by kpolice on 2007-05-06
I have a Radeon 9600 and I don't recommend the r300 open source driver or in other words the AIGLX option.

The performance with this driver is worst than with the fglrx driver, it doesn't support ACPI so I have to close the lid of my laptop to turn off the monitor (with the fglrx driver it is turned off automatically after a few minutes) and one of the most important things for me video playback is just ugly. Everything looks pixelated and when I move my vlc window sometimes I lose my video and I just see black.

Also firefox scrolling is slow with the open source driver. And it is not less CPU intensitive, with the r300 driver my fans are working almost every minute which in a notebook is not what you expect.

The open source driver is the way to go for radeon 9200 or older cards but for 9500 or newer I really recommend the fglrx driver + xgl.

---

### Post by dodgePT on 2007-05-06
In AIGLX you can use gmplayer -zoom for mplayer to display correctly while in fullscreen mode, using X11/Xv.
How do i modify mplayer startup to always include this instruction (-zoom) without having to enter it in console?

Is there a way of doing something similar with VLC player?

---

### Post by HeyItsMatt on 2007-05-07
> **livesys said:**
> Beryl on Ubuntu 7.04 Feisty Fawn with ATI

If you own one of these ATI Radeon Card below:

    * 7000 / rv100 based cards.
    * 7200 / R100 based cards.
    * 7500 / rv200 based cards.
    * 8X00 / R200 based cards.
    * 9000 / rv250 based cards.
    * 9100 / R200 based cards.
    * 9200 / rv280 based cards.

    * 9500 / R300 based cards.
    * 9600 / rv350 or rv360 based cards.
    * 9700 / R300 based cards.
    * 9800 / R350 or R360 based cards.
    * X300 / rv370 based cards.
    * X600 / rv380 based cards.
    * X700 / rv410 based cards.
    * X800 / R420 or R423 or R430 or R480 based cards.
    * X850 / R480 or R481 based cards.

then you want to use "AIGLX" for Beryl because the driver is built-into Ubuntu 7.04 Feisty Fawn.  It is also much easier to set-up and less cpu-intensive.


Hey - in the guide that you mentioned to follow, it says that my card should be listed under "Full 3D Support" if I want to use Beryl.  My card is a Radeon 9500 Pro / R300, which you have listed there, except on the linked site it's listed under "Experimental 3D Acceleration", not Full 3D.  Also, I just installed Feisty Fawn and for some reason the option "Desktop Effects" under "System / Preferences" does not even exist, although I've read it's supposed to be there... making me wonder if my card was recognized as incompatible with Compiz or something.

Is there any wiki or site out there that has a list of cards that have been confirmed to work with either Beryl or Compiz (under a particular driver, with AIGLX vs. XGL, etc)?  I'll be honest, the only thing I really want is transparent windows :)

Also, if I just get Compiz or Beryl using aptitude / from the package management system, can I basically just uninstall it if it's totally not working right, and have anything go back to normal?

---

### Post by therealknewman on 2007-05-21
Thanks for the help livesys, I used the guide that was posted but I used the compix window manager, this makes the windows bounce when I move them and some other neat effects but I still have no 3d cube. I have the x1600 so its been a long journey for me and it was nice to see the cool window effects finally!

---

### Post by Mazen on 2007-05-22
i installed Beryl using the AIGLX HowTo and i have a problem with the video, i doesn't turn with the cube!
any help?

---

### Post by Mazen on 2007-05-22
i realise it takes alot of cpu power when viewing videos maybe instead of using the graphic card i have!
any solutions?
and is Beryl with XGL working good on 7.04 now?

---

### Post by Mazen on 2007-05-22
anyone?

---

### Post by antiplex on 2007-05-30
seems to be still the same situation. at least it is for me. i've spent about 2 days now trying to improve somehow the desktop-performance and i'm kind of feeling frustrated now. well, one might argue that i simply could turn off beryl and get back to metacity but honestly i think beryl is more than only eyecandy (of course depending on how one's using it) but can also extent productivity with the expose-clone, transparent windows during moving, transparency for certain types of windows(e.g. terminals) and last but not least the improved memorability of apllication-window's positions through using 'the cube'.

i've got the fglrx + xgl + beryl solution 'running' (rather strolling) since i have an ati radeon X1600 card and therefore can't use the open source driver. its really a pity that ati is not willing to support aiglx and i am pretty sure that my new computer will have a nvidia card.
what is bugging me most is the really sluggish scrolling of for example webpages in firefox and secondly the high cpu-usage during any window/desktop-change. :(

here's what i've tried so far:
- originally i had the proprietary fglrx driver from the ubuntu repository installed and it seemed to work slightly better than with the latest driver directly from ati (8.36.5). the reason why i switched to the latest driver was that i had to recompile my kernel because i needed some options set that hardly may have to do anything with this issue and it appeared to me that you can't use the fglrx-ubuntu .deb package for a self-compiled driver. anybody experienced something different? i tried to find an older version on the ati website but couldn't find any. anybody's got a link to ati-version of the 8.34.something driver maybe?
- in [this thread]("http://ubuntuforums.org/showthread.php?t=451494") a few users improved the situation by using a 386-kernel instad of the default generic one, but this did not change anything in my case.
- [this one]("http://ubuntuforums.org/showpost.php?p=2343898&postcount=13") about issues with libx11-6 in that context made me really hope that i could somehow find a solution but since i have all updates installed and even completely re-installed the latest libx11 with no effect, it seems to be a problem with xgl. 


i think users in [this thread]("http://ubuntuforums.org/showthread.php?t=401186") have the same problem and there seems no real way around it except waiting for an ati-driver supporting aiglx or put an nvidia card into your pc if you want to use beryl.

if any body has any hints/news about the whole thing please let me/us know...

---

### Post by antiplex on 2007-06-12
i just found a [petition to ati/amd for better support of aiglx]("http://www.petitiononline.com/xSeAILGX/petition.html") and it sure would do good if some more ppl would sign it...

click the link above or use this url: [http://www.petitiononline.com/xSeAILGX/petition.html](http://www.petitiononline.com/xSeAILGX/petition.html)

i'm unsure if this might help but well, lets hope it does! ;)

peace - antiplex

---

### Post by shadows85 on 2007-06-15
> **Snowcat said:**
> Here you go:

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")


I tried that once, and xserver broke down... Maybe I didn't do it correctly or something..

---

### Post by Supertonic on 2007-06-19
Hey does anyone know if I should even bother trying Beryll on my laptop?  I have an HP dv5000 and lspci shows this: 
* 01:05:0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)*

I haven't found much info for my card regarding Beryl.  If so, should I use AIGLX or fglrx +xgl? drivers?

Thanx!

---

### Post by nandoc on 2007-08-02
Hi,
After reading so many pages I got finally to this one:
[http://ubuntuforums.org/showthread.php?t=488385&highlight=beryl+ati+radeon](http://ubuntuforums.org/showthread.php?t=488385&highlight=beryl+ati+radeon)
It WORKS !!!!!!! for ATI powered Laptops (have tried 2 different ones) and works on my ATI  Radeon X1650 perfectly....
Give it a try,
NANDOC

---


---
title: "Audio issues!!!"
date: 2005-12-31
forum: Desktop Environments
---

### Post by crispy_420 on 2005-12-31
OK heres my problem:

All my audio works fine most of the time in the applications I normally use. But when I try to watch flash based movies (online), I get no audio until I plug my speakers into my motherboard's onboard audio. Also my Logitech Deluxe keyboard wants to control the onboard volume control.

My motherboard is an Intel D845BG and my soundcard is a Creative Sound Blaster Live 5.1.

Basically what I want is to setup the Creative card as default for all audio and not the onboard audio. How do I go about doing that?

HAPPY NEWYEAR!

---

### Post by crispy_420 on 2005-12-31
I was able to get it by disabling my onboard soundcard in BIOS. And after reconfiguring a few applications. 

Is it possible to disable within OS and not bios? Make the OS not even see the onboard audio card exsists?

---

### Post by handy on 2006-01-01
The following info' may or may not be appropriate?

The following page will tell you how to select just one card using Ubuntu:

[http://doc.gwos.org/index.php/Multisounds/](http://doc.gwos.org/index.php/Multisounds/)

Search the above site for more info' it is very useful.

Also the following worked for me:

[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

Good Luck :p 

handy

---

### Post by crispy_420 on 2006-01-02
I tried that but it ended up getting rid of all the system sounds (close window, open menu, audio on boot to desktop, etc.). Basically it was the same as disabling onboard audio. So I'm back to the same place. All software working, no system sounds

Just for future reference:

If I were to do a reinstall, with onboard audio disabled in BIOS, will get to avoid this whole issue?
Just a thought for next time or to test since I use swappable hard drives and should get one back from RMA soon. Maybe time to get another swapable drive cage.

---

### Post by handy on 2006-01-03
It would seem that audio in Ubuntu is a thorny issue!

Personally I don't have any system sounds, which is the way I like it. :p 

I always turn them off when I set up a windoze machine, unless the customer expresses a desire for them.

I only want sounds for UT2K4, CD's & especially DVD's.  All of which I have sounds on my system.  Naturally I'm happy 'cause I've got what I want.  :KS 

Installing with the onboard audio turned off in the BIOS won't make any difference if you have configured done the following:

=========================

Multisounds/

From Ubuntu Document Storage Facility

Lot of Ubuntu users have multiple sound cards (the most common example being an onboard sound card and a PCI external sound card). Most of such users would want to use one specific card in preference to the other. Here is how to do it: Our main motive here is to make ALSA output to our chosen sound card. Sound cards are numbered in an order of preference by the kernel. The "default" sound card is numbered as "0", and the rest get numbered as "1", "2" etc. Let us assume here that our onboard sound card is the "default" (numbered as "0") sound card and we want to change that to the PCI sound card. Here is what we do for that from terminal:

sudo gedit /etc/asound.conf

and enter the following in that:

pcm.!default {
type hw
card 1
}

ctl.!default {
type hw
card 1
}

Pease remember that you need to replace "1" with the appropriate sound card number but for most users with two sound cards it will be "1". Now save and exit and run the following from terminal:

sudo /etc/init.d/alsa restart

now you should be able to get sound to work from the "other" sound card 

=========================

It would seem that for the vast majority of (not only) new Ubuntu users, sound is a can of worms.

Perhaps it might be worth posting a new thread in the sub-forum "Hardware Help/Video & Sound" ?

All the best,

handy

---

### Post by crispy_420 on 2006-01-03
Actually after a reboot, all works fine. System sounds are on as are all media players and the main thing for me was flash based audio in firefox. I read about this online mini movie and had to check it out. 

And I'm trying to use windows less and less. As I plan to redo my windows compter mainly towards gaming and some multimedia tasks, I needed an alternative for day to day use.

If you like anime this is the link to the movie that got me started in all this.

[http://ninjai.com/]("http://ninjai.com/")

Some more interesting movies here:

[http://www.atomfilms.com/af/home/]("http://www.atomfilms.com/af/home/")

*** check out the "Ninja Pays Half My Rent" clip ***

At the very least this has taught me a little more. But isn't this why we are all here anyway. To learn and share.

Thanks for the help.

Now off to setup my keyboard and mouse. 

**_Keyboard:_**

Logitech Desktop Elite (corded) ***got some special keys working but not all***
   Like to get all keys setup to my preferences but that is a long term goal.

_**Mouse:**_

Logitech MX510 ***want back/foward side keys to work***

Any idea where to start?

---

### Post by handy on 2006-01-03
Very good news!!  :KS 

I have to ask you if you ran this line:

sudo /etc/init.d/alsa restart

last of all in the "Multisound" instructions?

Cheers,

handy

---

### Post by crispy_420 on 2006-01-03
I might have along the way if it was posted on one of those links. Don't remember to be honest. If it was in one of those initial links provided I tried it. Then I went back to disable onboard and reconfigured my media apps. Not 100% on what I did but disable onboard audio was a good start. And as I figure, why would I need it anyway, except to complicate my life?

You check out those film links?
Any links to set up mouse and keyboard?

You like my new avatar? (only if a family guy fan?) *** for some reason not an animated .gif***

---


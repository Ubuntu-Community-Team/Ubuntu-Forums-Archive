---
title: "Jaunty"
date: 2009-04-23
forum: General Help
---

### Post by DeMus on 2009-04-23
What are the first experiences with Jaunty?
Does it work? If so, did you find trouble installing it?
Does something not work? Is that easy to fix?
How is the speed compared to 8.04? And I do not only mean the boot speed, but in general?
Is hardware detected well? Or do you need external drivers? How about nVidia, how is that handled?

I know, a lot of questions, but I have 8.04 running and with a program called Boinc it is running 24/7 on 100% of the CPU. I do not like to get a system which doesn't work, or which works slower.
So please, only honest answers please. Tell your experiences.

Thanks very much.

---

### Post by prssn on 2009-04-23
Compiz stopped working for me when upgrading. And no one seems to have a solution

---

### Post by dabl on 2009-04-23
> **DeMus said:**
> 

So please, only honest answers please. Tell your experiences.

Thanks very much.


OK.  I installed Kubuntu 9.04, on an ext4 filesystem, from a daily Alternate Install CD image just before the Beta release, 3 weeks ago.  After installation, it booted cleanly into KDE 4.2.

As usual, configuring it to my taste took probably 6 hours, over a couple of days.  The only problem I had was that, somewhere along the way, my nVidia driver installation got partially corrupted, but I didn't realize it.  I suddenly noticed that OpenGL wasn't actually running, or not running right.  I re-installed the proprietary nVidia driver, re-ran nvidia-xconfig and now it is fine again.

Firefox with java and flash plugins works fine, Google Earth works (now that GLX is working), music plays with Amarok 2 (which I don't comprehend) or alsaplayer, which I do, K3b burns CDs just fine, VMWare Player runs my 8GB Win XP VM just fine, except there's something wrong and the "bridged networking" function doesn't work most of the time. lm-sensors finds as many sensors as it used to, gkrellm shows the output, everything pretty much just works.  :)

---

### Post by dabl on 2009-04-23
> **prssn said:**
> Compiz stopped working for me when upgrading. And no one seems to have a solution

What troubleshooting have you done?  Does glxgears run?  When you open a console window and enter ```
compiz --replace
``` what is the error output?

---

### Post by theozzlives on 2009-04-23
> **prssn said:**
> Compiz stopped working for me when upgrading. And no one seems to have a solution

My video chip was blacklisted (Intel) on my laptop, but after running compiz-check and overriding, compiz works again. Otherwise Jaunty is great... faster, more attractive.

---

### Post by DeMus on 2009-04-25
I installed it on a separate partition and until now only one thing doesn't work, which did work in Hardy. BUt I will make it work. It's nothing to do with Jaunty, I guess.
All other things including the nVidia driver and Flash works fine.
Also I must say I like the way it looks. It's clearer, brighter.
Yes, I like it. Canonical has done a fine job. Thanks guys (and girls)

---

### Post by Philk on 2009-04-26
DeMus,

I'd be very interested in what your Boinc installation does in 9.04, compared to what you were running earlier.

I have Boinc running on both 9.04 and my earlier 8.10 partitions of my machine.  With similar preferences set for both installations, the 9.04 is only running tasks at about half the speed of the 8.10.  In both cases, the tasks I'm running are Astropulse tasks under SETI.  What takes about 107 hours in 8.10 takes an estimated 208 hours in 9.04.

Have you had a chance to compare computation times yet?

Philk

---

### Post by DeMus on 2009-04-26
> **Philk said:**
> DeMus,

I'd be very interested in what your Boinc installation does in 9.04, compared to what you were running earlier.

I have Boinc running on both 9.04 and my earlier 8.10 partitions of my machine.  With similar preferences set for both installations, the 9.04 is only running tasks at about half the speed of the 8.10.  In both cases, the tasks I'm running are Astropulse tasks under SETI.  What takes about 107 hours in 8.10 takes an estimated 208 hours in 9.04.

Have you had a chance to compare computation times yet?

Philk

Not really no. I had JJ installed parallel to Hardy to see how it worked. This afternoon I killed Hardy and installed JJ using the complete disc. Boinc is running for about 2-3 hours now so it is too early to tell.
I do have one strange thing though: in the Boinc manager when i click on the button Your Account (or one of the others) not Firefox but Epiphany is opened. I set FF as preferred program but still Epiphany starts. Any idea how to change that. I'm afraid when I un-install Epiphany I won't be able to visit the websites related to Boinc straight from the manager at all. You also have this same problem?

---

### Post by Philk on 2009-04-26
DeMus,

I can't really help you there.  I originally had my e-mail app (Thunderbird) pop up when I hit the web Help buttons.  Now nothing happens when I hit them.

I had double checked the preferred applications listings, but those were set the way I wanted.

I agree with your "too early to tell" comment.  I have noticed the "To completion" times coming down as calculations continue.  However, they're not coming down that much.  On the other hand, if I extrapolate from the just over four hours the computations have been running, I come up with about 72 hours for completion.  Quite different from the 207 hours for completion that Boinc is calculating.

Sorry I can't be any help on the apps, though.

Philk

---

### Post by Hellstudios on 2009-04-26
I upgraded Yesterday, And I must say, I love it. all the apps that didn't work before (cario dock, record my desktop) run fine now.


I still Can't find a driver for my ati card, but I guess I won't be playing any games until I get Nvidia. :P



I love it all in all, just get it already!

---

### Post by VCoolio on 2009-04-26
No problems here. Just the usual when doing a clean install: getting free-non-free codecs, fonts, getting partitions to automount, installing the nvidea driver. Went smoothly, and Jaunty is faster I think (but I tweaked Intrepid a lot over the months, so that could have caused some delays there). I'm very happy again with a new release. Not too happy with the new notifications without buttons option, but I knew that; just a difference of opinion.

---

### Post by viralnexxus on 2009-04-26
I upgraded from 8.10 to the latest 9.04 just a couple of days ago.  I found booting to be faster, packages and overall theme (look) was awesome!  Everything went smoothly during the installation process, including the drivers for my Nvidia Geforce 8300GS.  However, my sound stopped working almost immediately post installation.  The only tweaking I did after installation was changing the default theme to the DarkRoom theme; and by doing that it somehow caused my sound to stop functioning.  I cannot seem to get it to work, even after reading through tons of: Forum Posts, Articles, IRC, Help Files, Google, etc...  I am using a RealTek AC 97 onboard (no speakers) sound card, and no mic plugged in.  HELP!!!!!!
-=VB=-

---


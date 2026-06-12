---
title: "Issues with resolution"
date: 2006-02-20
forum: Desktop Environments
---

### Post by Nimue on 2006-02-20
I installed Ubuntu on my friend's laptop as it is an easier distro to use, and good for the beginning Linux user (so as to familiarize him/her with a variety of packages and the like). I, personally, have a stage one Gentoo install on both my laptop and my desktop. I don't mind waiting - so I reap the benefits. I can understand why people choose alternate distros however (as two days to install OO2.0 is a bit much). Anyway - her laptop's 1280x800 resolution is not recognized for some freak reason. I edited her xorg.conf file to have it, but Gnome, apparently, has its own config file somewhere that I can't manage to find. Would someone please direct me to it so that she can have a decent resolution? As it is now, she's at 1024x768@87hz and she has a lot of screenspace that could be used, and is perfectly black (for some reason it isn't fullscreening).

Just throw me around the basic config files for Gnome while you're at it (if you have time anyway). I, personally, use Fluxbox myself. But I can understand why people don't want to use that (as CLI can be daunting to some people).

---

### Post by bscbrit on 2006-02-20
You edited the correct file - there is no Gnome specific screen configuration file that I am aware of.

---

### Post by Nimue on 2006-02-20
Well the xorg.conf has no entries under the screen sections for the resolution 1024x768. I made certain the ONLY entry there was the 1280x800@60 one. HOWEVER, when I go to the resolution changer in the system tools or whatever, it doesn't list it. That leads me to believe that there is some irksome gnome config file out there somewhere. Also, I've noticed that upon editing the xorg.conf file a bit and then exiting/starting X, gnome whined about the 'Gnome keyboard layout' being different than the 'X keyboard layout.' I've already fixed that though, but it DOES show that gnome reads configuration stuffs from more than just xorg.conf - thus proving my point a bit more.

Anywho - if anyone knows how to add resolutions to the resolution changer dealie, aside from xorg.conf (as that doesn't appear to work), please tell me. I may just have to stick her with a Window Manager I know - like fluxbox. But I doubt she has the knowledge quite yet to run the more complex (in their simplicity) window managers that I am familiar with.

Also, just for the hell of it...

[http://img81.imageshack.us/img81/425/screeny28ih.jpg](http://img81.imageshack.us/img81/425/screeny28ih.jpg) - My Desktop
[http://img92.imageshack.us/img92/8728/screeny222ba.jpg](http://img92.imageshack.us/img92/8728/screeny222ba.jpg) - My Laptop

---

### Post by bscbrit on 2006-02-21
Yes, it does seem that Gnome reads other files - but not for the screen configuration.

The problem with part of the screen being unused sounds like a driver problem.

Can you post the relevant part of the xorg.conf please - perhaps a fresh pair of eyes can spot something amiss, but there are no guarantees :D

---

### Post by dbott67 on 2006-02-21
My laptop's resolution (ancient Toshiba Tecra 8000) was not detected correctly either.  I did some Googling on the make & model of my graphics card & monitor and found that I needed to add some "modelines", as well as adjust the refresh rates.

Here's a [post]("http://ubuntuforums.org/showpost.php?p=163824&postcount=1") that I wrote sometime ago explaining it.

Another little trick you might try is to use a "Live CD" and see if it correctly detects the screen resolution.  If it does, you can copy the xorg.conf file from the "live" session to USB/floppy.  Then, boot into the "installed" version and edit the installed xorg.conf to match.

-Dave

---

### Post by bscbrit on 2006-02-21
dbott67 - Good suggestion re the use of a live disk. Simple but effective. I'll put that one in my notebook of useful tips.  Thank you.

---

### Post by arrizaba on 2006-02-21
I had similar problems with the Dell Inspiron 1300.
With the inspiron 1300 it does not matter that you tweak the xorg file. It won't make any difference.
The monitor native resolution is 1280x800, but X only displays 1024x768.

What you have to do then is change the resolution at boot. But don't panic, some people already did the job for you. What you need is the package 915resolution, which can install from synaptic. Afterwards you need to do some tweaks by replacing one existing screen configuration to the one made by the 915resolution hack. Check the page:

[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

Note: This also works for computers other than the Inspiron 1300, see the list in the page above.

---


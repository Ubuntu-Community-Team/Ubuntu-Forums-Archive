---
title: "setting up an 800mhz clunker for a toddler"
date: 2009-05-25
forum: Education &amp; Science
---

### Post by anystupidname on 2009-05-25
Does anybody have some advice/ideas/suggestions beyond what I've listed below? (I thought about a touchscreen but not after looking at prices so I'm sticking with keyboard and builtin trackball)

Here is my plan so far to make it a kiosk type learning/playing machine:
- LXDE (I'm open to a different window mangler) + Edubuntu (I'll need to figure out a way to hide menus and just have the game and education menu categories show as big icons on the desktop (suggestions how?)
- lock down firefox with glubble and/or kidzui and/or something else...?
- add some stories and kid songs in ogg format with easy launch icons
- lock DVD tray button at startup with "eject -i 1"

Any suggestions much appreciated!

---

### Post by robert shearer on 2009-05-25
Never used it, it may a starting point/option in your search?? Runs on Ubuntu according to  wikipedia.

> Sugar is used on the OLPC XO-1 laptop computer and is also available as a session option on Ubuntu and Fedora. Unlike more traditional desktop environments, it does not use a "desktop" metaphor and only focuses on one task at a time.

[http://www.sugarlabs.org/](http://www.sugarlabs.org/)

[http://wiki.sugarlabs.org/go/Welcome_to_the_Sugar_Labs_wiki](http://wiki.sugarlabs.org/go/Welcome_to_the_Sugar_Labs_wiki)

[http://en.wikipedia.org/wiki/Sugar_(GUI)](http://en.wikipedia.org/wiki/Sugar_(GUI)))

---

### Post by kerry_s on 2009-05-25
i would go with a standard desktop rather than lxde, there much more easier to setup and maintain, in fact if i was doing it, i'd go with a debian base install + gnome-core. debian is much faster and there are no added features like the *ubuntu's, gnome is very easy to lock down, the icon's can be locked on the panel, in fact i would only leave a panel for just the tasklist, notification, volume and clock. everything else can be desktop icons, the desktop icons can be dragged to the size you want, so you can mix different size icons, in gconf-editor there is a whole section on lockdown, and gnome has a low resource mode so it will run just fine on 800mhz, you didn't say how much ram, i hope you got at least 256mb.

---

### Post by samden on 2009-05-25
Try a base install of Ubuntu Christian Edition, then install the edubuntu packages on top of that. That way you get the Dansguardian web filter - which I presume you'll certainly want for a toddler.

---

### Post by anystupidname on 2009-05-26
@robert: Nice! Thanks, I'll add that to the mix. Looks interesting.

@kerry: Thanks, good ideas. I'm not particularly stuck on Ubuntu or a specific window manager. I guess Debian would be a little lighter plus I was checking out the Debian Junior project.
[http://www.debian.org/devel/debian-jr/](http://www.debian.org/devel/debian-jr/)
The box has 512MB RAM. (I had some extra crappy old RAM around, heh) An initial test with regular Ubuntu performed a little slower than I'd hoped. Perhaps I'll need to tweak it to favor RAM over swap or something...

@samden: Please do not evangelize here. The distro you recommended is for religious people and it has been discontinued. I find it offensive.

---

### Post by snowpine on 2009-05-26
This distro looks kind of cute, maybe you can get some ideas here: [http://www.foresightlinux.org/kids.html](http://www.foresightlinux.org/kids.html)

---

### Post by kerry_s on 2009-05-26
> @kerry: Thanks, good ideas. I'm not particularly stuck on Ubuntu or a specific window manager. I guess Debian would be a little lighter plus I was checking out the Debian Junior project.
[http://www.debian.org/devel/debian-jr/](http://www.debian.org/devel/debian-jr/)
The box has 512MB RAM. (I had some extra crappy old RAM around, heh) An initial test with regular Ubuntu performed a little slower than I'd hoped. Perhaps I'll need to tweak it to favor RAM over swap or something...

debian is the way to go. i did 1 for my niece on a old 750mhz 128mb ram laptop so i know it can work. i went fully custom on mine though, installed the base and built up from there, it's much easier to control only whats needed. i used the net installer:
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso)

unchecked desktop & standard at the package selection to get a base install. then i started with:

logged in as root:
**apt-get install xorg gdm gnome-core gconf-editor synaptic**

thats enough to get you into gui, just reboot log in and use synaptic to continue adding what you want. use gconf-editor to turn on lowresource mode, use the find in the menu.

---

### Post by samden on 2009-05-26
Anystupidname, I was not evangelising at all, I was offering a practical suggestion.

You stated a wish to "lock down firefox". I had a suggestion that would help you achieve this easily. I have never used Ubuntu CE myself but have seen it recommended by others for this purpose. I could just as easily have recommended the unofficial Muslim edition, which has dansguardian set up as well, but recommended CE because it is an official fork and probably better supported.

If you wish to bring religion into the discussion by rejecting a technical suggestion because of your own religious views, that's your business. I choose to leave religion out of my computing and just use whatever tool works best for me.

---

### Post by robert shearer on 2009-05-26
> use gconf-editor to turn on lowresource mode, use the find in the menu. 

This caught my attention.... !  but no joy.
Tried the find option in gconf-editor (on my Debian lenny install) but it returned a "pattern not found".

Can you elaborate on how to do this?

cheers bob

EDIT...  found it!
in configuration editor   apps=>metacity=>general    then scroll down to 'reduced resources' and tick the box then close.

seems to speed up window opening/closing. Firefox a bit faster too???
I will keep playing.  Thanks for that tip.

---

### Post by kozimodo on 2009-05-27
Try qimo ([http://www.qimo4kids.com/](http://www.qimo4kids.com/)) although you will still need to lock down firefox etc.

---

### Post by bthessel on 2009-05-27
I am actually looking to set up the exact same thing for my 5 year old. I will give Qimo a try. 

Any, let me know of any good tips you stumble upon and I will do likewise.

---

### Post by bthessel on 2009-05-29
Ok, I think I am going to try using the Netbook Remix since it is already setup with nice large icon set. I am going to use Dan's Guardian for my internet filter on it. I may disable the network connection on it unless I am in the room just to be safe.

---

### Post by durand on 2009-05-31
I think the requirements for Qimo are a bit too high for your computer.

---


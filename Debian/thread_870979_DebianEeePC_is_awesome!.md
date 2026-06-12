---
title: "DebianEeePC is awesome!"
date: 2008-07-26
forum: Debian
---

### Post by wolfen69 on 2008-07-26
just got an Asus EeePC 2gig Surf. to say the least, the default OS (heavily modified xandros) was *very* unimpressive. i tried eeexubuntu, but image was a bit too large to install. and then i stumbled upon a link to debianeeepc. it is a 16mb net-install image based on debian lenny, you boot to via usb stick. [here]("http://wiki.debian.org/DebianEeePC") is the link to it. you can do the install via wireless. just select your wireless ath0 during setup and enter your wep key.

when selecting which packages to install, i opted for a minimal, no gui install by only selecting standard and laptop. (installing a desktop environment would have installed gnome and a ton of apps, putting me way over my 2gig limit)  i installed xorg and the xfce4 desktop. after that, i had to go to (as root) /var/cache/apt/archives and remove all the .deb files used for installing all the apps and such, freeing up much needed space. then installing a few apps such as firefox, synaptic, wireless manager, codecs, etc. 

wow! to say i'm impressed is an understatement. this baby runs flawless and fast. highly recommended for those who want the debian experience on the go.

---

### Post by Bachstelze on 2008-07-26
I did exactly the same thing. Just with Ubuntu instead of Debian ;)

---

### Post by tel93 on 2008-07-26
I want the eepc so badly now :) :)

---

### Post by Bungo Pony on 2008-07-26
After playing with an eeepc at a store, I have to agree that I don't like the default install. IMO, Asus needs to get a better distro on those nifty little machines.

---

### Post by stream303 on 2008-07-27
That's great to hear.  One thing I did to my 20G was to make sure I was running noatime in the ext3 filesystem line in /etc/fstab, and changed the kernel sheduler from CFQ to Deadline.  (I just put elevator=deadline in my menu.lst kernel line for grub.)

Not sure if Lenny is using noatime, or relatime yet in fstab.  Since there are no heads on the ssd disks, the deadline kernel scheduler seems the most appropriate.  Even though I'm using Mandriva 2008.1, I think noatime (or relatime) and the deadline kernel scheduler would be useful among all distros you may load on it.

---

### Post by wolfen69 on 2008-07-28
> **HymnToLife said:**
> I did exactly the same thing. Just with Ubuntu instead of Debian ;)

do you have the 4gig model?

---

### Post by Bachstelze on 2008-07-29
> **wolfen69 said:**
> do you have the 4gig model?

Yes, but how does it matter?

---

### Post by wolfen69 on 2008-07-29
> **HymnToLife said:**
> Yes, but how does it matter?

it matters because you are more limited as to what you can install on 2gigs as opposed to 4. if i had 4, i probably would have gone with regular ubuntu. but debian works great as it turns out. 

i only have 500MB left, so i can't go crazy installing stuff.

---

### Post by Bachstelze on 2008-07-29
> **wolfen69 said:**
> it matters because you are more limited as to what you can install on 2gigs as opposed to 4. if i had 4, i probably would have gone with regular ubuntu. but debian works great as it turns out. 

Well, I wasn't talking about "regular Ubuntu". I installed a base system, and then built from it, just like you did in DEbian. Ubuntu lets you do that too, and you can still benefit from all the other advantages Ubuntu has over Debian (larger repositories due to less strict policies, for example).

---

### Post by wolfen69 on 2008-07-29
i realize you installed a base system, and i know about ubuntu minimal installs. but the one thing that bugs me about the ubuntu vs. debian minimal installs is that in ubuntu, if i do "apt-get install xfce", i get a complete barebones xfce, (some people may prefer this) without the ability of apps being automatically added to the menus and other time wasting annoyances. and much more configuration needed. in debian, no such problem. debian minimals dont really add any more apps, they just make it a little easier to continue to get your system up and running. (imagine that, debian making something easier than ubuntu) ubuntu was a little *too* minimal. on the flipside, debian is a little harder to get wireless perfect, but reading the wiki took care of that. plus, debian minimals tend to use a tad less memory.

what i was referring to in my previous post, (which i didnt make clear) is about installing a full featured os, like mandriva, eeedora, eeexubuntu. and ubuntu. sorry for not being clear.

---

### Post by K.Mandla on 2008-07-30
I'm just going to shift this into the Debian section. ... :)

---

### Post by basenvironment on 2008-07-31
> **HymnToLife said:**
> Well, I wasn't talking about "regular Ubuntu". I installed a base system 
how large is a base ubuntu system? Can you do a minimal install from the liveCD or do you still have to use the alternate cd?

>  all the other advantages Ubuntu has over Debian 
what would ALL those be?

>  (larger repositories due to less strict policies, for example)
unsupported repositories...

---

### Post by bluemm on 2008-10-30
so is debianEeePC a stripped down version of eeebuntu/ubuntu-eee?

i like the idea that you only need to download 15mb or so and download the rest while installing.  sounds like a neat idea.

---

### Post by kerry_s on 2008-10-30
> **wolfen69 said:**
> just got an Asus EeePC 2gig Surf. to say the least, the default OS (heavily modified xandros) was *very* unimpressive. i tried eeexubuntu, but image was a bit too large to install. and then i stumbled upon a link to debianeeepc. it is a 16mb net-install image based on debian lenny, you boot to via usb stick. [here]("http://wiki.debian.org/DebianEeePC") is the link to it. you can do the install via wireless. just select your wireless ath0 during setup and enter your wep key.

when selecting which packages to install, i opted for a minimal, no gui install by only selecting standard and laptop. (installing a desktop environment would have installed gnome and a ton of apps, putting me way over my 2gig limit)  i installed xorg and the xfce4 desktop. after that, i had to go to (as root) /var/cache/apt/archives and remove all the .deb files used for installing all the apps and such, freeing up much needed space. then installing a few apps such as firefox, synaptic, wireless manager, codecs, etc. 

wow! to say i'm impressed is an understatement. this baby runs flawless and fast. highly recommended for those who want the debian experience on the go.


> i had to go to (as root) /var/cache/apt/archives

apt-get clean

also if you delete /usr/share/docs & /usr/share/man
you'll get more room. those things can be found on line.


xfce4? you can do better than that. grab a lite wm instead.

don't forget to grab the eee stuff in the repo. also you really don't need standard and laptop, you can install only what's specific to your computer when your building up. for example: in the laptop you might only need uswsusp to put the computer into standby and hibernate(s2ram,s2disk,s2both) all the others are not needed. turn off the logs if you really don't need them, i only keep a few.(/etc/syslog.conf, just # them out)

the more you build up from the base the better you'll get. also don't be afraid to mix gnome and kde programs in there. for example: kolourpaint even with kde libs is still lighter than gimp. eog is a great image viewer in gnome, you can use that to, i now prefer totem-xine & the w32codecs to other media players, if only vlc would fix there firefox plugin, etc...

my laptops only 450mhz 256mb ram, you should have no problems.

---

### Post by wolfen69 on 2008-10-31
i've since wiped the debian install and use pupeee on a 1gb flash drive. but i want to do a net install of intrepid. yeah i know debian might be better, but i can't help playing around with different installs. btw, xfce was pretty fast on it. what are your thoughts on ice wm? i may even do openbox on it. all i use it for is surfing, so i really don't need much of anything installed.

---

### Post by kerry_s on 2008-10-31
> **wolfen69 said:**
> i've since wiped the debian install and use pupeee on a 1gb flash drive. but i want to do a net install of intrepid. yeah i know debian might be better, but i can't help playing around with different installs. btw, xfce was pretty fast on it. what are your thoughts on ice wm? i may even do openbox on it. all i use it for is surfing, so i really don't need much of anything installed.

icewm and openbox will be much faster. just play around try different things, you'll eventually find what fits your system best. i've done all the playing around already and settled with debian etch base + jwm, rox, leafpad, etc...
it just works the fastest and rock solid, my laptop has problems with kernels higher than 2.6.20, it's 10 years old can't expect it to be supported forever. :)

i've grown past the fancy stuff, i just want things to work and work fast.
my stuff just looks empty. see pic's

---

### Post by oOarthurOo on 2008-10-31
Want to save some space? Next time just install the laptop component, since standard stuff gets pulled in by the apps you install and if you find you really need something (like locate) you can just install it.

Also, remove debconf-i1810 which has all languages, aptitude will automatically install the english version to satisfy dependcies and free up space. 

Then, from a clean system go into aptitude "aptitude" and uncheck install recommended dependencies automatically. Then start building your system. I do things I need one at a time and read the recommends, if I feel I need it I will either cancel and add it or cancel and add the -r switch to install recommends for that app (eg. nautilus). 

You can also clear downloaded installation packages, do without a swap partition or file, since RAM on those things is easier than HD space. 

Just for example, upon install of basic and laptop, I do something like:

aptitude install xserver-xorg-video-intel
aptitude install gdm
aptitude install gnome-screensaver
aptitude install -r nautilus
aptitude install leafpad 

^^ leafpad is a great tiny replacement for gedit.

---


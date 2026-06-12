---
title: "need help to trim down xubuntu please."
date: 2008-03-17
forum: Desktop Environments
---

### Post by keratos on 2008-03-17
Read some posts about ubuntu and xubuntu trimming but not got the answer I need hence this post.

I installed from the alternate CD so that was a good start.

How do I trim down xubuntu ?

There are loads of packages that appear useless to me, X clients, games, artwork, themes, tools,  etc.

The problem I have is that in synaptic, when I mark something for removal I get the odd message about dependancies have to be removed also, but these dont appear something I need.

However, scrolling down the list of "installed" packages I came across xubuntu-desktop and minimals, gdm and alike that it wanted to also remove yet I didnt see these appear??

I'm confused.

Is there a way to "start again" without trashing my system.

I dont want to reinstall again.

mmm? tricky

---

### Post by Fire_Chief on 2008-03-17
Hi Keratos,

You haven't really specified what your target or desired result looks like. You can trim stuff out left and right and get all the way down to a barebones command line only system with just the basic Linux commands available. Granted I'm not sure anyone would want to go this far but the point is made. What do you want to trim to?

Cheers

---

### Post by jken146 on 2008-03-17
A barebones installation could be a good idea.  That way you can pick only the packages you want.  You should really notice the difference in performance.  [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by keratos on 2008-03-17
Fire_Chief: The target is whatever is MINIMAL in the following:

* Networking o my ADSL router via ethernet ipv4.
* xfce GUI with vesa display module
* minimal xubuntu "backend"
* synaptic

Not bothered about apps,/clients themes, icons, firewalls, iptables, ipv6, 

If I need anything else, I can always get it via synaptic.

I just want the MINIMAL xubuntu WITHOUT having to install again like from a "mini ISO"

jken146: Thanks but see previous statement.

---

### Post by keratos on 2008-03-18
Okay , in the absence of any feedback I just went with:-

removed apckages matching or refering to:
*gnome* (gnome)
*bonobo* (gnome)
*dcom* (kde)
*desktop* (any desktop)
*x*, *X*, *xorg*, *xserver* (all X related)
*window* (anything to do with a window!! - hope that was GUI stuff)
*gtk* (anything to do with gtk engines)
*artwork*
*themes*
*icons*
*python* anything related to python (used in GUI apps)
*games*
...and more "unused useless apps" selected at will , all in synaptic.


Then, installed (plus any deps):
xfce4

Then downloaded 2.6.24.3 kernel source and tweaked the .config to create a custom kernel including only "typciall" code and modules. There's a lot intel/amd box doesnt need!!!

created with kpkg, new  kernel-source, kernel-image and kernel-header packages and installed these.

Rebooted (anxiously!!)

Voila.

Got a command prompt, a few X tweaks and install of gdm followed..then I was up and running on an *buntu/deb system with a very rapid and thin xfce4 desktop. Truly amazing and faster in my view than Zenwalk and Vector.

Very impressed, extremely.

If you dont like/need gnome and want to reduce bloat , and try it yourself

I like Zen + Vector however the deb derivatives, particulary *buntu, come with excellent package availability and management. Upstream suppliers also tend to "favour" deb package systems, from my experience.

Now I have a deb/*buntu based system outperforming standard Zen + Vector. GREAT!

---

### Post by kerry_s on 2008-03-18
dang, you should just go custom, get it your way from the start.

---

### Post by keratos on 2008-03-18
> **kerry_s said:**
> dang, you should just go custom, get it your way from the start.

Double dang,

I've just realised and made enlighteded by a post in the debian forums...

All I need to do is this 

[url]http://ubuntu.sabza.org/2007/09/04/my-cute-little-xfce-desktop-environment/[url]

I dont like gnome and I definitely do not care for kde3 or 4 !

Deb etch is what I need I think - it was *buntu hype that made me install it, but I like clean, trim and lean install with only what I need installed.

Duhhh

---

### Post by kerry_s on 2008-03-18
> **keratos said:**
> Double dang,

I've just realised and made enlighteded by a post in the debian forums...

All I need to do is this 

[url]http://ubuntu.sabza.org/2007/09/04/my-cute-little-xfce-desktop-environment/[url]

I dont like gnome and I definitely do not care for kde3 or 4 !

Deb etch is what I need I think - it was *buntu hype that made me install it, but I like clean, trim and lean install with only what I need installed.

Duhhh

that's more like it, i use a debian custom install etch/lenny.
i use the net installer for the base->
 [http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso]("http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso")

then just
apt-get install xorg synaptic jwm mc

that's enough to get me to the gui, where i open synaptic do a little clean up.

then i'll grab the rest of my stuff.
rox-filer leafpad iceweasel grun mtpaint scrot vlc

---

### Post by keratos on 2008-03-19
> **kerry_s said:**
> that's more like it, i use a debian custom install etch/lenny.
i use the net installer for the base->
 [http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso]("http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso")

then just
apt-get install xorg synaptic jwm mc

that's enough to get me to the gui, where i open synaptic do a little clean up.

then i'll grab the rest of my stuff.
rox-filer leafpad iceweasel grun mtpaint scrot vlc


Thats what I've done.

Although I did a minimal install I note the /usr partition is at 3.5GB whereas xbuntu was at 2GB (full install) ???

As a matter of interest, how come you post to the ubuntu forums and not linuxquestions or debian forums?

I think I'll be leaving here soon to goto one of these on a permanent basis.

I personally dont like the 6month updates and prefer the static stability of deb with the choice of taking from lenny / sid if required, and more importantly, when requried.

---

### Post by kerry_s on 2008-03-19
> **keratos said:**
> Thats what I've done.

Although I did a minimal install I note the /usr partition is at 3.5GB whereas xbuntu was at 2GB (full install) ???

As a matter of interest, how come you post to the ubuntu forums and not linuxquestions or debian forums?

I think I'll be leaving here soon to goto one of these on a permanent basis.

I personally dont like the 6month updates and prefer the static stability of deb with the choice of taking from lenny / sid if required, and more importantly, when requried.

i just prefer this forum, like you i gave ubuntu a run, but it didn't fit the needs of my machine. over here there are people who need more help, than in those other forums, i do have accounts on other forums.

just because you don't use ubuntu, doesn't mean you can't participate. you can just as well get debian help here if you need it, it will probably be alot faster than those other forums. 

i can't explain the /usr thing, mines at 320m(see pic)

---

### Post by keratos on 2008-03-19
Yes - I agree. Responses ove there take a good half day to come through although this could be down to the US/UK time difference.

Over here, there appears to be significant European and Eastern contributions. I've had responses here from Middlesex to Moscow. Quite sereal really and definitely not complaining.

Okay, you've convinced me. So long as people dont frown on posts relating to Deb (Etch/Lenny/Sid) then I'm okay here ..?

p.s. nice JWM setup. Where are the icons and gadgets from? Cool!

---

### Post by kerry_s on 2008-03-19
my icon's are from every where, i looked all over for a matching set of only the icons i wanted, mixed and matched till they all look right together. i didn't want a huge full icon set with icons ill never use, just a select few to cover what i have, anything missing will use the stock rox icons till i find 1 to cover it, but i got most covered, with just the few i have. rox makes it easy to set custom icons for each or all the mimes. 
this setup is empty compared to what i usually run, this time i don't have any icons in the task bar or my menu or desktop, except the 1 that turns the screen off, i only did rox.

here's the set where i got the folders->
[http://www.freeiconsweb.com/NX06_icons.htm](http://www.freeiconsweb.com/NX06_icons.htm)

attached my icon folder and gtkrc for the rox toolbar.

---


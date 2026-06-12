---
title: "Problem with Firefox after upgrade"
date: 2005-11-12
forum: Desktop Environments
---

### Post by miguelforero on 2005-11-12
Hi everybody, I have a problem with my firefox, I upgraded the linux with this sources.list

> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

## official backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

#plf
## deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-freee


it upgrade to Ubuntu 5.0, it cganged a lot of things.

After this, the firefox is not the same, when I try to listen a song preview of wma on Amazon.com, it doesnt use the "mplayer", it use "Totem movie player" and leave an error, before I upgraded the Ubuntu it used the "mplayer" and work perfectly, I dont know what happen. I checked on synaptic and the "mozilla-mplayer" is installed even "mencoder".
The other thing I could notice, is that when I go to [www.oldnavy.com](www.oldnavy.com), see it:

[IMG]http://img493.imageshack.us/img493/7447/oldnavyscreenshot5gm.jpg[/IMG]

I have re-installed the firefox and it doesnt work.

Could somebody help me?

---

### Post by spizkapa on 2005-11-12
Your problem has nothing to do with Firefox, it's Linux that the site doesn't support. Could you get to it before? You may be able to see it if you install the user agent extension in FF and pretend to be IE for a while.

Or use Opera which has that feature by default.

---

### Post by nix4me on 2005-11-12
Interesting.

I tried going to oldnavy.com with Firefox 1.5RC2, epiphany, galeon, and Opera and none of them work.

nix4me

---

### Post by Dr. Nick on 2005-11-12
Ill take a shot at the mplayer problem, I answered a same if not identical question recently

here is the full link
[http://www.ubuntuforums.org/showthread.php?t=72870](http://www.ubuntuforums.org/showthread.php?t=72870)

Possible solution: is to just remove the plugins manually out of FF for totem and have the mplayer ones installed. Read the above thread on the specifics . I dont reccomend removing totem-gstreamer though, Id try the other way listed about moving the files out of the plugin folder

Oh and oldnavy doesnt work here either
Reccomend maybe to contact the webmaster

---

### Post by Dr. Nick on 2005-11-12
Old navy will work with the above mentioned usergent switcher
get it here [https://addons.mozilla.org/extensions/moreinfo.php?id=59](https://addons.mozilla.org/extensions/moreinfo.php?id=59)

I think it should be an easy fix for them since it works but just block linux.

Here is their customer service which doesnt address the issue at all but gives a contact email
[http://www.oldnavy.com/customerService/info.do?cid=3330&mlink=,332071&clink=332071](http://www.oldnavy.com/customerService/info.do?cid=3330&mlink=,332071&clink=332071)

---

### Post by miguelforero on 2005-11-13
[QUOTE=spizkapa]Your problem has nothing to do with Firefox, it's Linux that the site doesn't support. Could you get to it before? You may be able to see it if you install the user agent extension in FF and pretend to be IE for a while.

Or use Opera which has that feature by default.[/QUOTE]

Yeah, I could get to it before, I'll try to install it.

And Dr. Nick, I'll will review that to see the solutions.

Thanks everyone, I'll tell you how was it.

---

### Post by miguelforero on 2005-11-13
Well, the user agent works very good.

And by removing the totem the mplayer works perfectly.

Thanks everyone.

PD: Sorry if I made some mistakes, I'm from Venezuela and I don`t speack very well the english.

---

### Post by hoodwink on 2005-11-13
[QUOTE=nix4me]Interesting.

I tried going to oldnavy.com with Firefox 1.5RC2, epiphany, galeon, and Opera and none of them work.

nix4me[/QUOTE]
Yeah, that site sucks. I'm using Firefox 1.5 Beta 2 and I get the same results. A pox on sites that don't work with Firefox!

---

### Post by Dr. Nick on 2005-11-13
Whats weird is they say they support FF for windows, dont see why it wouldnt work in linux as well.

miguelforero Glad you got it working

---

### Post by arnieboy on 2005-11-13
an easy way to replace totem player with mplayer wud be to use automatix

---


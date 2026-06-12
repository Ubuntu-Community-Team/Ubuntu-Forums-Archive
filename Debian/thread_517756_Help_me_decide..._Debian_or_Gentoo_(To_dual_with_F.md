---
title: "Help me decide... Debian or Gentoo? (To dual with Feisty, and eventually switch to)"
date: 2007-08-04
forum: Debian
---

### Post by sab0403 on 2007-08-04
Hello,

I've been with Ubuntu for a couple of months now. However this is not my first foray into Linux, as I had Mandrake (what is now Mandriva, IIRC) for about six months around 1999. I'm happy with Ubuntu, it's helped me remember a lot of the stuff I had forgotten about Linux (which isn't really that much, pretty basic stuff but at least I'm not as lost as I was a little while ago); however, the boot times are similar or superior than those in Windows (>1:30), and I'm interested in installing a lighter, quicker OS. While I still plan to install stuff in it that will probably drag it down a notch (a couple of desklets and Beryl come to mind), I think I'd be better off with one of these options.

However I'm still undecided as to which one to take on. I've tried Debian for a few days now and I've been pleased for the most part - btw, can someone explain the naming to me? I downloaded ISOs (netinst and CD 1) for Etch, but apparently that's not the latest... anyway, I've tried Debian, and gotten the wireless to work ok, can't seem to get Beryl working but that's besides the point. Debian is wicked fast to boot if I use the netinst CD (~ 30s), but slows down considerably (around Ubuntu's boot time) if I use the CD 1 to install it. Either way the fact that I can actually hibernate on it sells it to me over Feisty. And, although I haven't installed Gentoo (basically because I haven't had the time to leave it compiling, plus I can't find an install CD for the x86 architecture - I have a Pentium M in case you can help me out there) I've heard nothing but good things about it, both it being fast and extremely secure. So... what do you guys think?? 

Should I go with Debian or Gentoo?

Thanks in advance! :popcorn:

---

### Post by tturrisi on 2007-08-05
I prefer straight Debian.
I use the minimal net install of Etch (stable).
I boot it w/ "expertgui" at the boot prompt.
At the taskselect screen to select what software to install I use the spacebar to remove all X's.  This winds you up with just a minimal base system.  At reboot I do:
editor /etc/apt/sources.list
and add the  debian-multimedia.org repo, then grab & add the pgp key needed.  Then I do:
apt-get install xorg gnome-core synaptic alacarte build-essential linux-headers-`uname -r` module-assistant alsa-base alsa-utils alsa-oss mplayer w32codecs libdvdcss2 liblame0 xmms msttcorefonts iceweasel icedove 
This give the simplest minimal gnome installation & required files to build the kernel packages I need for wifi & other stuff.  I then pick & choose the rest of the software that I want & need.

---

### Post by odiseo77 on 2007-08-05
I've used both, Debian and Gentoo, but I prefer Debian. As for the Debian naming conventions: Etch is the latest stable release; Lenny is the testing release (has more up-to-date packages but is not supposed to be as stable as Etch); and Sid is the unstable, bleeding edge release. Note that although Lenny/Sid are supposed to be testing/unstable, I've dist-upgraded to lenny/sid and I haven't found big stability issues (maybe some little glitches when booting gnome, I guess caused by beryl).

---

### Post by sab0403 on 2007-08-05
Ok... thanks for the answers guys...

One more thing though. tturrisi mentions the debian-multimedia repos (and the corresponding key). Yet I can't seem to find this info googling (it just brings back results for sites that *mention* these repos/keys, but don't actually name them). Is there any site that has like a list of the available repos?

I think I'll reinstall Debian with the netinst, and give it a go to tturrisi's methods. However I do need to know how to add the repos/keys if I want to do this... :P

Oh, and another question. Etch includes the drivers for the Intel 2200 wireless card already (I just found this out at the last install I made). Does the netinst install this driver - and, for that matter, any other driver that I need? I'm inclined to say yes, but I don't know just how much the "minimal" installation takes away (AFAIK, it limits the install of services/software packages, but drivers stay as is).

Thanks again! :popcorn:

---

### Post by sab0403 on 2007-08-05
Oh, and odiseo77:

If you could point out what tutorial or general steps you followed to install beryl (including any dist-upgrades, if any), I'd be very thankful. You're using Etch, right?

I ask because I've had dependencies issues (saying that I already have libc6, for instance, but that I have an older version than the one needed... yet it won't be upgraded)

---

### Post by odiseo77 on 2007-08-05
Hi, well, I took the info on how to install beryl on Debian from the debian beryl wiki (the site is dead, probably because of compiz fusion, I'm not sure, but just in case, this is the link: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Debian](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Debian) ).

As for the debian-multimedia repo, all you have to do is to install the keyring: [http://www.debian-multimedia.org/faq.html](http://www.debian-multimedia.org/faq.html) , select one of the [mirrors]("http://www.debian-multimedia.org/mirrors.html") for your sources.list file, and run apt-get update.

About the netinstall cd and your wireless connection, I'm not sure your wireless card will be recognized (take a look at [this]("http://www.debian.org/distrib/netinst")). My PCI wireless card was not recognized by the netinstall cd when I reinstalled debian some months ago, but things might have changed.

Greetings, and good luck!! ;-)

---

### Post by Bachstelze on 2007-08-05
> **sab0403 said:**
> 
Oh, and another question. Etch includes the drivers for the Intel 2200 wireless card already (I just found this out at the last install I made). Does the netinst install this driver - and, for that matter, any other driver that I need?

The ipw2200 driver is in the official kernel tree so unless it's kernel has been heavily customized, any distro will have it.

---

### Post by tturrisi on 2007-08-07
In the net install the wifi won't work.  You will have to use a wired connection first.  If install module-assistant you can then easily install the driver & (possibly needed firmware).

re debian-multimedia.org, login as root & do:

editor /etc/apt/sources.list
Add the following repository address:
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main
Save the file.

Then do:
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907 | apt-key add -

Then do:
apt-get update

Then do:
apt-get install w32codecs libdvdcss2 liblame0 msttcorefonts mplayer

---


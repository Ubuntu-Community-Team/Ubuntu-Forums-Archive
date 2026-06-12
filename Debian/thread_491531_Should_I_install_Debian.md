---
title: "Should I install Debian?"
date: 2007-07-03
forum: Debian
---

### Post by tcoffeep on 2007-07-03
I've looked it over again and again.

I want to install it, but what's really required? I don't have much net speed to do the minimal disk, but is downloading all 23 cds? Any one got any suggestions?

[just to note that I'm on a mission to learn linux as much as possible. I understand the Ubuntu is based on Debian or something, and perhaps trying this out might teach me something]

---

### Post by odiseo77 on 2007-07-03
I'd say, if you want to get familiar with the command line and linux in general, you could install debian -which doesn't mean you can't learn new stuff with Ubuntu; one thing you won't find in debian is the 'click magic' ubuntu has for newbies (I mean, when you click on a mp3 on amarok on ubuntu, it automatically activates the multiverse repo and install the required library). You'll still find Synaptic and apt-get/aptitude on debian, so , if you're used to these tools, then you'll be comfortable with it. IMO, debian is not that hard as some people say (I've tried gentoo and slackware, and I'd say they a bit harder to install and overall, to setup); and it's not a bad idea to learn and discover new stuff.

As for the installation method, if you have broadband, you can try the netinstall cd instead of downloading all the 23 cd's; it will start with a minimal selection of packages and fetch the remaining ones from the internet. 

Other thing, I wouldn't suggest you to install debian over ubuntu, but install it aside with ubuntu, so you get used to it step by step.

And yes, ubuntu is based on debian, they both use .deb packages and dpkg, apt-get for package management.

Greetings, and good luck with debian.

---

### Post by tcoffeep on 2007-07-03
Thanks to your suggestions, I am now d/l'ing the netinstall of the testing-version (or w/e you call that). Just for some heads up, any good tutorial sites, just so I can become "formally" acquainted with Debian?

---

### Post by kerry_s on 2007-07-03
Debian rocks!

Full kde desktop, just like kubuntu> [http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso](http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso)

Full xfce4 install, just like xubuntu> [http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

Net installer> [http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-businesscard.iso)

If you got a slow internet, go custom, use the net install and just install the base(nogui). Then just build up from there at your leisure.

base install (unselect all the packages at the selection screen)
login as root
apt-get install xorg gdm synaptic fluxbox
reboot (ctrl+alt+delete)
select fluxbox in the session menu and login
open synaptic and grab what ever you want.

If you want the fancy installer, boot with> installgui

i use debian custom + fluxbox, mine is upgraded from etch to lenny/sid. I'm running on a old laptop upgrade ram to 256, upgraded drive to 20gig> [http://www.iq.sony.com/srvs/DocsConnect/docget.asp?manualid=14552&DL](http://www.iq.sony.com/srvs/DocsConnect/docget.asp?manualid=14552&DL)

---

### Post by odiseo77 on 2007-07-03
As for the installation, you probably want to read the [installation manual]("http://www.debian.org/releases/stable/installmanual") (just select your architecture, your language, and the format in which you want to read the manual), and as for the post-config tasks, and such, I'd suggest you to take a look at the variety of manuals available [here]("http://www.debian.org/doc/") (I have other useful links in my computer, but I'm at work right now).

Greetings.

---

### Post by CREEPING DEATH on 2007-07-07
> **tcoffeep said:**
> I've looked it over again and again.

I want to install it, but what's really required? I don't have much net speed to do the minimal disk, but is downloading all 23 cds? Any one got any suggestions?

[just to note that I'm on a mission to learn linux as much as possible. I understand the Ubuntu is based on Debian or something, and perhaps trying this out might teach me something]

The Debian site sucks, it has for years, that's why it took Ubuntu to get me using Linux.  I'm currently running Etch.  You only need the first CD for the standard Gnome desktop, there are alternatives CDs for XFCE and KDE.

CD

---

### Post by benuski on 2007-07-07
There's a very nice Debian forum [here]("http://forums.debian.net"), where people are always willing to help.  

Good luck with Debian!  I've found it to be a lot of fun.

---

### Post by tcoffeep on 2007-07-08
I tried installing Java and flash, and it seemed a tad more difficult than it is with Ubuntu.

I followed the instructions, and everything refused to work. I could only install Flash for Iceweasel, and not epiphany...which one is better by the way? Anyways, Java wouldn't work, no matter how hard I tried.

The worst part is that everytime I try to install something from the terminal, it keeps asking me to insert the cd...is there any way to stop that from happening?

Do I need to install ATI graphics card seperately, or is it compatible with Debian?

---

### Post by wariola on 2007-07-08
There is automatix for debian you can get at the automatix page. Also there's another call hakix at [http://code.google.com/p/hakix/](http://code.google.com/p/hakix/) for a more convenient installation. I use Ubuntu on my notebook as its a better desktop distro (automatically detect my wireless card etc) but I use Debian etch for all my servers as I only require the classic CLI for versatility and performance.

Regarding the installation from cd, you can un-comment the CD repository. 

From the terminal, type sudo gedit /etc/apt/sources.list

Then uncomment the CD repository

Then you can add other online repository.

---

### Post by odiseo77 on 2007-07-08
Hi tcoffee, congratulations, and welcome to debian! :D

First, in order to install stuff, administer your system and such, you must login as root before with ***su*** (note that unlike ubuntu, your user password and your root password are not the same, unless, of course, that you have set the the same password for both, your user and root).

Java:

```
apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin
```

After these packages are installed execute (as root):

```
update-alternatives --config java
```

and enter the number for java1.6 at the prompt.

As for the browser, I'd suggest iceweasel.

And as for the issue with the cd, you could comment with numerals (#) the lines for the cd in your /etc/apt/sources.list file and force this way apt to download the packages from the internet (not sure if this works, maybe you'll get some missing dependencies when trying to install packages, if this happens, then uncomment the lines).

Greetings.

---

### Post by tturrisi on 2007-07-10
> Regarding the installation from cd, you can un-comment the CD repository.

From the terminal, type sudo gedit /etc/apt/sources.list

Then uncomment the CD repository

Then you can add other online repository.
that should be COMMENT the cd repository, it is already uncommented!

---

### Post by kerry_s on 2007-07-10
> **tcoffeep said:**
> I tried installing Java and flash, and it seemed a tad more difficult than it is with Ubuntu.

I followed the instructions, and everything refused to work. I could only install Flash for Iceweasel, and not epiphany...which one is better by the way? Anyways, Java wouldn't work, no matter how hard I tried.

The worst part is that everytime I try to install something from the terminal, it keeps asking me to insert the cd...is there any way to stop that from happening?

Do I need to install ATI graphics card seperately, or is it compatible with Debian?


Sounds like your making it harder than it should be.
First for package management use the gui(su & apt-get install synaptic)
as far as package's, like ubuntu you need to turn on all the repos.

su & gedit /etc/apt/sources.list
add> contrib non-free
example:
```
deb http://ftp.debian.org/debian/ etch main contrib non-free  
```

oh, the cdrom can be unchecked in synaptic or # out in the sources.list

after you fix that just locate java in synaptic and mark it for install, select the plugin 1 it will pull in all the java you need.

You might also want to add the multimedia repo

```
deb http://www.debian-multimedia.org/ etch main  
```

---

### Post by t.liljenberg on 2007-07-28
No, Ubuntu is much better and straight forward and it still uses firefox which is alot better than iceweasel which has alot of security issues.

---

### Post by kerry_s on 2007-07-28
> **t.liljenberg said:**
> No, Ubuntu is much better and straight forward and it still uses firefox which is alot better than iceweasel which has alot of security issues.

so narrowed minded, firefox and iceweasel are "EXACTLY" the same, only the icons and name was changed to make it free.

---

### Post by odiseo77 on 2007-07-28
Not to mention that Ubuntu is based on DEBIAN, so, if you want to learn the real linux, you must use something like Debian (don't misunderstand me, it's only that Debian is the parent and skeleton of SO MANY distros out there (like Ubuntu) that wouldn't have been possible without it).

---

### Post by Qew on 2007-07-29
> **t.liljenberg said:**
> No, Ubuntu is much better and straight forward and it still uses firefox which is alot better than iceweasel which has alot of security issues.

You got that information from where? As said above, Iceweasel and Firefox are identical, bar the name, its identfication (easily changable) and some graphics. As for Ubuntu being better: it might be better for you, but you're not everybody. I'll stick with what's better for me and let you dig up some info to justify your claim that Iceweasel is less secure than Firefox. ;)

---


---
title: "I want a lean installation"
date: 2007-09-14
forum: Desktop Environments
---

### Post by joshnur on 2007-09-14
I have successfully installed Ubuntu 7.04 Desktop.

I now would like to have a lean installation for development. I already removed unnecessary applications through Synaptic, but would like to have more disk space.

How can I proceed to locate and remove extraneous libraries and applications for the leanest possible desktop?

Thanks,

Josh

---

### Post by Rupertronco on 2007-09-14
How lean do you want it? You could install xubuntu, or install a command line os from any of the alternate install cds which will enable you to build your own desktop. If you want the leanest possible ubuntu, I'd install a command line and use fluxbox to manage your windows. 

Ubuntu uses Gnome by default and it's nowhere near as lean as XFCE or Fluxbox/Blackbox/Openbox.

You could also keep the current configuration you have, and just install fluxbox and use GDM to select a fluxbox session. (when you go to login hit sessions and choose fluxbox). Install fluxbox by typing ```
 sudo apt-get install fluxbox 
```

---

### Post by joshnur on 2007-09-15
Thanks for the suggestion.

Actually I want to recover a maximum of disk space.

---

### Post by Warren Watts on 2007-09-15
Here is a HOWTO I wrote on setting up a minimal install using Xfce..
It only uses a little over 1BG of disk space.
Might be TOO minimal for you taste though, I dunno.

[HOWTO Build and install a compact (+/-) 1GB Xfce Based Ubuntu Desktop]("http://ubuntuforums.org/showthread.php?t=549958")

---

### Post by kerry_s on 2007-09-15
go custom>

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

just change the install line, to meet your needs.
example:
base install
sudo apt-get xserver-xorg-video-vesa xorg jwm mc
startx

if you select your vid card first xorg won't install all the others you won't need
jwm= very small full featured wm
mc= terminal filemanager with a editor, can be used with or without X

personally, i would use debian, the base is smaller and you can use testing/lenny and unstable/sid if you want more up to date stuff. there's no need to keep up with releases, as debian simplely continues to update via packages, so your not locked into a snapshot release.

---

### Post by kerry_s on 2007-09-15
> **Warren Watts said:**
> Here is a HOWTO I wrote on setting up a minimal install using Xfce..
It only uses a little over 1BG of disk space.
Might be TOO minimal for you taste though, I dunno.

[HOWTO Build and install a compact (+/-) 1GB Xfce Based Ubuntu Desktop]("http://ubuntuforums.org/showthread.php?t=549958")

nice how to, but you need more practice.

this line->
sudo apt-get install xserver-xorg xfonts-base xfonts-100dpi xfonts-75dpi xfonts-scalable ttf-bitstream-vera x-ttcidfont-conf

no need that much typing, most of that is dependent, that whole is as simple as->
sudo apt-get install xorg

that's it, you get all that stuff.

this line->
sudo apt-get install xfce4 xfce4-appfinder xfce4-artwork xfce4-goodies
only need
sudo apt-get install xfce4 xfce4-appfinder


combine it all you get->
sudo apt-get install xorg gdm synaptic xfce4 xfce4-appfinder

the other stuff, yes and no, there are lighter options. for instance file roller=unp unpacks almost everything.

i've got almost all that and not even near a gig.

practice makes perfect, your on your way.

---

### Post by Warren Watts on 2007-09-15
> **kerry_s said:**
> nice how to, but you need more practice....practice makes perfect, your on your way.

I appreciate your comments and suggestions. It is my first HOWTO, inspired by an install of Archlinux.

 I resisted installing the entire xorg package because I didn't want a whole bunch of extra junk installed that I might not need.  Same with Xfce.  I am at work right now (on a windows box) and i don't have access to my system to really look into what all is included in the xorg  and xfce packages.

I will do some research when I get home in the morning and edit/revise as I see necessary.  I was just trying to keep as much extra junk from getting installed as possible.

---

### Post by kerry_s on 2007-09-15
> **Warren Watts said:**
> I appreciate your comments and suggestions. It is my first HOWTO, inspired by an install of Archlinux.

 I resisted installing the entire xorg package because I didn't want a whole bunch of extra junk installed that I might not need.  Same with Xfce.  I am at work right now (on a windows box) and i don't have access to my system to really look into what all is included in the xorg  and xfce packages.

I will do some research when I get home in the morning and edit/revise as I see necessary.  I was just trying to keep as much extra junk from getting installed as possible.

yeah, i see your specs, your just like me you need light. mines a 450mhz 256ram, so i only do custom installs. don't worry the more you do it the better you'll get, you'll learn where you can and can not cut corners. i jump around to different wm's and setups every month or so, i get bored fast. :)
when you get around to it you should try other wm's to, they have there good and there bad. i've had full installs, open office, the works, as small as 500mb with certain wm's and serious trimming of the fat.
the fun part is the learning and those little oops moments, gota love it. :lolflag:

---

### Post by maybeway36 on 2007-09-15
For a mini-Kubuntu with very few packages, try these:
```
aptitude update
aptitude install -y kde-core kubuntu-default-settings xorg kde-style-polyester kde-guidance kubuntu-docs kde-systemsettings gtk-qt-engine kdm adept kio-apt kubuntu-konqueror-shortcuts
aptitude remove -y kpersonalizer kregexpeditor
```
This installs the core of KDE and most of the Kubuntu stuff (adept, system settings, etc.) but not a lot of programs, or the Kubuntu bootsplash.
If you are on a laptop, you might also want kde-guidance-powermanager.

P.S. Too look at packages online, use [packages.ubuntu.com]("http://packages.ubuntu.com")

---

### Post by Warren Watts on 2007-09-15
> **maybeway36 said:**
>  To look at packages online, use [packages.ubuntu.com]("http://packages.ubuntu.com")
maybeway36; Thanks for the link!  Just what I needed; an easy way to view exacly what is in each package!

> **kerry_s said:**
> 
this line->
sudo apt-get install xserver-xorg xfonts-base xfonts-100dpi xfonts-75dpi xfonts-scalable ttf-bitstream-vera x-ttcidfont-conf

no need that much typing, most of that is dependent, that whole is as simple as->
sudo apt-get install xorg


OK, I agree with you on that one.  It IS way easier to just install xorg.  but I stand by the two extra font packages I listed at the end.

I will revise it to:
```
sudo apt-get install xorg ttf-bitstream-vera x-ttcidfont-conf
```

> **maybeway36 said:**
>  this line->
sudo apt-get install xfce4 xfce4-appfinder xfce4-artwork xfce4-goodies
only need
sudo apt-get install xfce4 xfce4-appfinder


Here i disagree.  I am going to leave it that way it stands.  I think xfce4-artwork and xfce4-goodies need to be installed as well just to give the user a few more basic tools and applets to work with.

---

### Post by RedSquirrel on 2007-09-15
> **joshnur said:**
> I now would like to have a lean installation for development. I already removed unnecessary applications through Synaptic, but would like to have more disk space.

How can I proceed to locate and remove extraneous libraries and applications for the leanest possible desktop?

I think it's easier to start from a minimal install and build up from there as suggested above. Here's another [guide]("https://help.ubuntu.com/community/Installation/LowMemorySystems") for you to consult.

You might also want to have a look at K.Mandla's [guide]("http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/"). It has to do with tweaking for *speed*, but it still might be of some use to you. Just be sure to do some research (read man pages, search with Google, etc.) before trying anything that looks unfamiliar. ;)

---

### Post by BobCFC on 2007-09-15
Yes on my old laptop I installed the minimal Ubuntu Server edition at about 500mb and just added the packages I wanted.

If you want to save space from an existing gnome install open Synaptic  and order the packages by the size column, you may want to enable the 'installed size' column in the prefs. because download size is a bit misleading.

(System->Administration->Synaptic Package Manager)

You will see the open office family takes up over 230mb, that can go... also there are lots of fonts for other languages that you will never use, they begin with TTF, there are arabic, chinese, hindi and all sorts which take up dozens of mb.

Evolution email is another big one nearly 100mb.  I use gmail so that's superfluous,

Other stuff you will have to delete as appropriate for you, for instance I remove all printing stuff such as cups, hp etc.

I can save about 500mb and still have most of the useful stuff like gimp and chess etc.

---

### Post by joshnur on 2007-09-15
Many thanks for all the excellent tips. I've already installed the default Gnome installation, and I'll go from there and remove additional packages.

If I install the minimal KDE packages, could I remove the Gnome ones?

---

### Post by BobCFC on 2007-09-16
Yes but when installed KDE next to gnome it installed DOZENS of applications.  If there is such a minimal package this would work lol.

---

### Post by RedSquirrel on 2007-09-17
What about **kde-core**?

>  This metapackage includes the core official modules released with KDE. This
 includes just the basic desktop (browser, file manager, text editor, control
 center, panel, etc.) and important libraries and data, in addition to the
 aRts soundserver.


---


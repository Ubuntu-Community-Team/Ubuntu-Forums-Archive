---
title: "Debian Guru Needed"
date: 2007-10-10
forum: Debian
---

### Post by Fred_E _krugar on 2007-10-10
Ok here is the situation, I decided ( against my better judgment ) to try and install the bear minimum of Debian. Well I got it install but I have no desktop I did apt-get fluxbox but it says that XServer  faild to start what do I need to do to get that going?? 

  I am really wanting to learn how to do this with only the bear essentials, can someone plz help me out??

---

### Post by notwen on 2007-10-10
Try this at the CLI:

```
apt-get install fluxbox menu x-window-system-core aterm
```

This should install flux, the debian menu, x and also aterm so you'll have a terminal available once you're in flux.  Post back and let me know  how things go.  Good luck. =]

---

### Post by tgalati4 on 2007-10-10
Do you have an X server installed?

>man xorg

If nothing then:

>sudo apt-get install xserver-xorg

>startx

(pray)

---

### Post by kerry_s on 2007-10-10
su <if your not root
**apt-get install xorg fluxbox**

if you really want to fine tune it so you only get the vid driver you need.

apt-get install xserver-xorg-video-vesa xorg fluxbox

replace "vesa" with your driver if needed
my cards a neomagic, so i use

apt-get install xserver-xorg-video-neomagic xorg synaptic jwm
startx

jwm is my prefered WM

---

### Post by Fred_E _krugar on 2007-10-10
Thanks for the quick responses , let me boot back into and see what happens.

---

### Post by Fred_E _krugar on 2007-10-10
ok got Xserver installed started X and I get a gray screen with an X mouse cursor nothing else happens what else do I need to do to get to the Desktop??

Thanks again guys :guitar:

---

### Post by kerry_s on 2007-10-10
remove fluxbox
apt-get purge fluxbox
then install it again
apt-get install fluxbox

it's a common problem, you have to install X before or at the same time as the WM or there's no file for it to set itself as the default.

or you can try creating a ~/.xinitrc file
with
**startfluxbox**
in it

also just to let you know fluxbox stock setup is just plain gray with a panel at the bottom, right click for menu.

---

### Post by az on 2007-10-10
If you want X to start on boot, install a display manager (XDM, WDM GDM or KDM, for example)

---

### Post by Fred_E _krugar on 2007-10-10
> **az said:**
> If you want X to start on boot, install a display manager (XDM, WDM GDM or KDM, for example)

 So I take it Fluxbox is not one of them then, So which one of those works best for Fluxbox??

---

### Post by Fred_E _krugar on 2007-10-10
> **kerry_s said:**
> remove fluxbox
apt-get purge fluxbox
then install it again
apt-get install fluxbox

it's a common problem, you have to install X before or at the same time as the WM or there's no file for it to set itself as the default.

or you can try creating a ~/.xinitrc file
with
**startfluxbox**
in it

also just to let you know fluxbox stock setup is just plain gray with a panel at the bottom, right click for menu.

ok will try that now, That makes alot of sense.    BRB

---

### Post by kerry_s on 2007-10-10
> **Fred_E _krugar said:**
> So I take it Fluxbox is not one of them then, So which one of those works best for Fluxbox??

you don't need that, but if you want it "gdm" is the best(apt-get install gdm).

---

### Post by Fred_E _krugar on 2007-10-10
ok did all of that and when I start X I still get only a gray screen with a X for a mouse cursor and right clicking does not bring up a menu.

---

### Post by kerry_s on 2007-10-10
> **Fred_E _krugar said:**
> ok did all of that and when I start X I still get only a gray screen with a X for a mouse cursor and right clicking does not bring up a menu.

okay, try the .xinitrc then.
**nano .xinitrc**
put
**startfluxbox**

ctrl+x+y & enter to save
note the "." meaning it's a hidden file.
make sure you leave a empty space for the last line, as in type> startfluxbox and hit enter/return. all files need 1 blank line at the bottom to signify the end.

at least your a little smarter now, next time you'll do it the right way and won't have to go through all this. :)

---

### Post by Fred_E _krugar on 2007-10-10
[QUOTE=

at least your a little smarter now, next time you'll do it the right way and won't have to go through all this. :)[/QUOTE]

 I think not I am still stupid when it comes to this lol. Anyway That still didnt work so I guess that I will just start all over. 

What do ya think about that??

 BTW I am using the Business card install.

 What all does it install if I leave the Desktop Environment checked??

---

### Post by kerry_s on 2007-10-10
> **Fred_E _krugar said:**
> I think not I am still stupid when it comes to this lol. Anyway That still didnt work so I guess that I will just start all over. 

What do ya think about that??

 BTW I am using the Business card install.

 What all does it install if I leave the Desktop Environment checked??

that's a good idea. i use that installer to.
install the base, that means when it comes to package selection, uncheck everything.
when that's done and you reboot.
log in as root
apt-get install xorg gdm synaptic fluxbox
reboot (ctrl+alt+delete)
select fluxbox in the session menu and log in as your user not root.
open synpatic and get what ever else you want

this will give you a bare bone's graphical install, still super light, just not as light as it can be.

What are your specs?

---

### Post by Fred_E _krugar on 2007-10-10
> **kerry_s said:**
> that's a good idea. i use that installer to.
install the base, that means when it comes to package selection, uncheck everything.
when that's done and you reboot.
log in as root
apt-get install xorg gdm synaptic fluxbox
reboot (ctrl+alt+delete)
select fluxbox in the session menu and log in as your user not root.
open synpatic and get what ever else you want

this will give you a bare bone's graphical install, still super light, just not as light as it can be.

What are your specs?
  

 My specs are: E6700 conroe , Dual 7900GTX's, BFG Nvidia i680 MB, 2gig Crucial Balistixs, 4 Samsung 40gig Hd's and Samsung SyncMaster 930b

---

### Post by kerry_s on 2007-10-10
> **Fred_E _krugar said:**
> My specs are: E6700 conroe , Dual 7900GTX's, BFG Nvidia i680 MB, 2gig Crucial Balistixs, 4 Samsung 40gig Hd's and Samsung SyncMaster 930b

wholly crap! you want to fly. you could have just gone with xfce4.

for that i recommend->
apt-get install xorg gdm synaptic fluxbox thunar mousepad iceweasel feh

synaptic is your package manager
thunar is your file manager
mousepad is your editor
iceweasel(aka:firefox) is your webbrowser
feh is is to view images and fluxbox's fbsetbg uses it to set the background.

---

### Post by Fred_E _krugar on 2007-10-10
OK i am going to try this again before I go to work Thx for all your help.

 Trust me If I have problems I will be back to ask for hellp lol

---

### Post by kerry_s on 2007-10-10
> **Fred_E _krugar said:**
> OK i am going to try this again before I go to work Thx for all your help.

 Trust me If I have problems I will be back to ask for hellp lol

i know you'll be back, i can even guess your first question "how come i don't have no icons in thunar?"

[B]apt-get install gtk2-engines-spherecrystal

mousepad .gtkrc-2.0[/B]
put

```
include "/usr/share/themes/SphereCrystal/gtk-2.0/gtkrc"
gtk-icon-theme-name = "SphereCrystal"
```

log out and back in.

i'll check on you later tonight, the sun's coming up, so it's time to hit the sack. :)

---

### Post by Fred_E _krugar on 2007-10-10
Ok cya btw I am now here using Debian

---

### Post by tgalati4 on 2007-10-10
That's a lot of effort to get a working system.  Try Mint with XFCE.  It will fly on that system and everything you want will be preloaded.

---

### Post by kerry_s on 2007-10-10
> **tgalati4 said:**
> That's a lot of effort to get a working system.  Try Mint with XFCE.  It will fly on that system and everything you want will be preloaded.

that's the idea, there's nothing like starting from the command line and building a gui system up. you learn how things are put together. the main goal is to get what you want, not what someone else thinks you should have. once you learn how to do a custom install, it gets very easy, you can try all kinds of things.

i just redid mine a couple of days ago, i was using xfce4, but now i'm back to jwm, only this time i've decided to go with no slow apps and i've given it a windows like look. also i'm trying alot of different things under the hood, for example: my swap partion is disabled, i'm using a program called "swapd" what it does is creates swapfiles to use as memory when my free memory falls below a certain amount. in doing it this way i make my system use only ram which is faster. i'm using a 450mhz 256ram laptop.

---

### Post by Fred_E _krugar on 2007-10-11
well i got everything running but sorry man I had to go with gnome-core,still seems to run pretty fast.I had problems with sound but I fixed them already.





I in love with a gnome<-------------- from a song, Im In Love With A Stripper lol

---

### Post by plb on 2007-10-12
> **tgalati4 said:**
> That's a lot of effort to get a working system.

Eh..not really. He didn't know what to do at first. In actuality all he had to do was...

> apt-get install xorg fluxbox

setup X
> dpkg-reconfigure xserver-xorg

> 
echo startfluxbox > ~/.xinitrc

> startx

---

### Post by b4k4 on 2007-10-31
> **kerry_s said:**
>  i'm using a program called "swapd" what it does is creates swapfiles to use as memory when my free memory falls below a certain amount. 

sounds just like a swap partition, only not safely away from your system files.

---

### Post by Fred_E _krugar on 2007-11-06
OK I now have a simple problem. How do I install .deb files that are not in the repositories. In Ubuntu you just D/L and install.
 
It uses a  GDebi Package Installer. What do I need install to use something like that??

---

### Post by Fred_E _krugar on 2007-11-06
N/M I just being stupid,I just found it lol

---


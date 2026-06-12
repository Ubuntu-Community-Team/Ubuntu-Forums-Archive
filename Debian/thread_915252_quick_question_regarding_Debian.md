---
title: "quick question regarding Debian"
date: 2008-09-09
forum: Debian
---

### Post by ceno-byte on 2008-09-09
ok here is the deal i have a old compaq presario 1235 laptop that works perfectly when i have damn small linux on it but i dont need half the stuff on DSL and it is not as customizable as debian is. now i tried doing a minimal install of ubuntu on the laptop but after a few days the partition somehow gets corrupted and i get a grub error 17 and even with SGD it wasnt able to resolve it so i was wondering if i can do a minimal install of debian which would include the following apps i like to use most

File Manager:
Midnight Commander

Web Browser:
Links2

Music Player:
C*mus

IRC/AIM:
naim

Games:
NetHack

BitTorrent:
rtorrent

Terminal:
Xterm

Window Manager:
Fluxbox

and if so can someone please point me to a HOWTO install debian (minimal) i will also like to use the 2.4 kernel with the custom install

---

### Post by ronnielsen1 on 2008-09-09
[http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)
I've done it myself. Some of the games you might have to install after you get the fluxbox thing installed.
I'm also going to do a shameless plug for lxde - more configurable and just as lightweight as fluxbox

---

### Post by Thanoulis on 2008-09-09
You can try the SlashEm version if NetHack...its more fun! :)

---

### Post by ceno-byte on 2008-09-09
sounds good ronnielsen1 but can you install kernel 2.4 with the minimal install

as for slashem Thanoulis i have played it it is fun but i perfer to play classic nethack

---

### Post by ronnielsen1 on 2008-09-10
> sounds good ronnielsen1 but can you install kernel 2.4 with the minimal install
I think this will do it but I haven't tried it
>                                                    To install using the 2.4 kernel press F3 when you
boot off the minimal CD and follow the instructions for installing the 2.4 kernel (type bf24 at the
boot: prompt and press enter). Note that you may need to manually select the right drivers for your
network card using this kernel version.


---

### Post by ronnielsen1 on 2008-09-10
Do the older ubuntus using 2.4 have a minimal install option?

---

### Post by kerry_s on 2008-09-10
net install will do it for you, but unless you use a old debian version, there is no 2.4 kernel and no current software to support it.

net installer:
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso)

at package selection uncheck everything.

log in as root
apt-get install xorg fluxbox menu mc links2
update-menus

log out of root, type> exit

log in as user
type> startx


with only a 266mhz cpu and 96mb ram max, it really pays to love the command line. :lolflag:

also google for tricks used on embedded systems, it will help to lesson hd use and keep things speedy, another trick i used when i was using a system with 128mb was to use a flash drive for swap instead of the hd, that's if you got 1 to spare, there fairly cheap these days i just picked up a couple at kmart for $2.00 a piece, there only 64mb, but still usable. :)

---

### Post by ceno-byte on 2008-09-10
"with only a 266mhz cpu and 96mb ram max, it really pays to love the command line. "

it really does help when you have a passion for the command line im not anti-GUI im on a GUI right now with my 64-bit system running ubuntu 8.04 but on older hardware i find a CLI enviroment backed by fluxbox to be a utopia because everything is so fast and clean llok at this fluxbox menu for example on how minimal i like things to be on old hardware 


[begin] (Fluxbox)
   [exec] (Terminal) {xterm} </usr/share/pixmaps/xterm-color_32x32.xpm>
      [config] (Configuration)
   [submenu] (Styles) {}
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
   [submenu] (Backgrounds)
      [wallpapers] (~/home/steve/backgrounds) 
   [end]
   [workspaces] (Workspaces)
   [reconfig] (Reconfigure)
   [exec] (Xkill) {xkill} <>
   [restart] (Restart)
   [exit] (Exit)
         
[end]


as for the 2.4 kernel i guess i could try running the 2.6 kernel it shouldnt be that bad thnxs to everyone for the suggestions

---

### Post by darrelljon on 2008-09-11
Isn't there a minimal Damn Small Linux install?

---

### Post by ronnielsen1 on 2008-09-11
> Isn't there a minimal Damn Small Linux install?

Didn't see one but since dsl is less than 50 Megs, how minimal do you want to go?

---

### Post by darrelljon on 2008-09-12
Command line minimal.
You might be interested in TheLittleDebian but it might be in Spanish.

---


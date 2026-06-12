---
title: "Fluxbox fails to load - Ubuntu 8.10"
date: 2008-11-19
forum: Desktop Environments
---

### Post by qyot27 on 2008-11-19
I ran some searches about the particular error message I got, but I could only find one link to a site in Russian...and since I can't read Russian, I figured I'd post here.

I recently freshly installed Ubuntu 8.10. When trying to install Fluxbox, I grabbed it, fluxconf, and gsetroot from Synaptic.  Then, when trying to log in to it through gdm, it fails, giving me this error message:
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
exec: 1: /usr/local/bin/fluxbox: not found
```
I'm not sure if the 3rd and 4th lines are actually supposed to be one line, so I typed it in the way it appeared.

This doesn't match the previous warning on the wiki about startup problems with the version of Fluxbox from the repositories, as when I attempted to fix it according to that method, it still failed.

Any ideas?

---

### Post by Simian Man on 2008-11-19
Either you don't have fluxbox installed, or it is somewhere other than /usr/local/bin/fluxbox.  My guess is that it is in /usr/bin/fluxbox instead.  You can enter the command 'which fluxbox' to verify this.

If that is indeed the problem, hopefully someone can tell you how to tell gdm where fluxbox really is.

BTW I'm from St. Pete :)

---

### Post by kerry_s on 2008-11-19
i would do> whereis fluxbox
then check all the paths.

don't forget you also need to grab "menu" (sudo apt-get install menu) then run> sudo update-menu
before you log into fluxbox or you won't have no right click menu.

---

### Post by qyot27 on 2008-11-20
I did figure out what was wrong, thanks to inspiration on the part of the responses here.  The instructions on the wiki concerning the .desktop file (which, admittedly, is for Dapper first and foremost) are *almost* right when it comes to Intrepid, in that it does needs to be adjusted, but instead of what it says to do, the line
```
Exec=/usr/bin/startfluxbox
```
needs to be changed to
```
Exec=/usr/bin/fluxbox
```
and all is well again.  I figured I'd post the solution so anyone else searching for this problem can find it.

Oh, I know about the initial issues with the menu.  I used Fluxbox as my default environment a couple years ago, and simply prefer to write up the menus myself while previewing the changes using Xnest (which for some reason seems to not want to work now, and neither does Xephyr).

---

### Post by kerry_s on 2008-11-20
> Oh, I know about the initial issues with the menu. I used Fluxbox as my default environment a couple years ago, and simply prefer to write up the menus myself

me to, but in my case i do it on jwm now, gave up fluxbox awhile back. i prefer separate menus for the different sections, so i'm using 4 menus. :)

---

### Post by RedSquirrel on 2008-11-21
> **qyot27 said:**
> I did figure out what was wrong, thanks to inspiration on the part of the responses here.  The instructions on the wiki concerning the .desktop file (which, admittedly, is for Dapper first and foremost) are *almost* right when it comes to Intrepid, in that it does needs to be adjusted, but instead of what it says to do, the line
```
Exec=/usr/bin/startfluxbox
```needs to be changed to
```
Exec=/usr/bin/fluxbox
```and all is well again.  I figured I'd post the solution so anyone else searching for this problem can find it.

If that solved your problem, I'd say the issue lies in your **~/.fluxbox/startup** file. Check the exec line in that file. It should look something like this:

```
exec /usr/bin/fluxbox
```You shoudn't have to modify /usr/share/xsessions/fluxbox.desktop. It's generally better to leave the Exec line in that file as

```
Exec=/usr/bin/startfluxbox
```**startfluxbox** is a script that will create the files and directories under ~/.fluxbox (if they don't already exist) and then run ~/.fluxbox/startup.

(When you have Exec=/usr/bin/fluxbox in /usr/share/xsessions/fluxbox.desktop instead of Exec=/usr/bin/startfluxbox, your ~/.fluxbox/startup file is not used.)

If something related to Fluxbox isn't working, one quick way to get back to a working setup is to rename your current ~/.fluxbox directory, then logout and log back in again.

```
mv ~/.fluxbox ~/.fluxbox_old
```The startfluxbox script will create a fresh ~/.fluxbox directory for you with safe default settings. ;)



> **kerry_s said:**
> don't forget you also need to grab "menu" (sudo apt-get install menu) then run> sudo update-menu
before you log into fluxbox or you won't have no right click menu.

Two things:

1) The **menu** package is a dependency for fluxbox, so there is no need to install it separately. ;)


2) On Hardy and Intrepid, the Fluxbox menu is created automatically after installing the fluxbox package, so there is no need to run 'sudo update-menus' on those two versions of Ubuntu. (Isn't it nice they finally fixed that. :))

---

### Post by kerry_s on 2008-11-21
> Two things:

1) The menu package is a dependency for fluxbox, so there is no need to install it separately.


2) On Hardy and Intrepid, the Fluxbox menu is created automatically after installing the fluxbox package, so there is no need to run 'sudo update-menus' on those two versions of Ubuntu. (Isn't it nice they finally fixed that. )

that's good to hear, less typing when instructing. :lolflag:
so RedSquirrel, what you using now a days?
you know me, debian & jwm still has me by the dangles. :)
i tried arch again about 2 or 3 weeks ago, it just still doesn't feel right. :(
i'm just to use to debian. :)

---

### Post by RedSquirrel on 2008-11-22
> **kerry_s said:**
> so RedSquirrel, what you using now a days?

For most of this year, I have had some sort of dual boot. I like this approach. It allows me to keep one OS for "getting things done" and another for playing. Also, if I manage to totally screw up one of the systems, I have a fallback. I could just use a rescue CD, but having another OS on the hard drive is handy.

These days, my main OS is Gentoo and I'm tinkering with Slackware.

I've gotten in the habit of putting the new OS's installer kernel (and initrd) on Gentoo's partition and using grub to boot it from there. This saves me having to download a large image and burn yet another CD. ;)




> **kerry_s said:**
> you know me, debian & jwm still has me by the dangles.

I generally alternate between dwm and Openbox. I'm using mostly dwm these days. I spend a great deal of time in terminals and I find the tiling layout is handy for that, especially with dwm's bstack (bottom stack) patch.




> **kerry_s said:**
> i tried arch again about 2 or 3 weeks ago, it just still doesn't feel right.
i'm just to use to debian. 

Arch has some good features and ideas, but I'd prefer security announcements or (even better) a security team of some sort. At times, it just doesn't seem like they have the manpower to keep on top of the project. I had a few other concerns about it that gave me sufficient momentum to move along. On the plus side, I don't read their forums much these days, but I did find them fairly enjoyable when I was using the distro.

I ran a dual boot of Debian sid and etch for a few months and enjoyed it.

With Ubuntu, I like to install each new release about two weeks before it comes out just to see what's new. After a couple of weeks of playing around with it, I replace it with something else.

The more "hands on" approach of Gentoo and Slackware seems to fit me a bit better. Maybe I have too much free time. :lol:

Edit: Here's a pic I posted last month on the Gentoo forums. Hope you don't mind me recycling it. [pic]("http://omploader.org/vdGZ2")

---

### Post by kerry_s on 2008-11-22
i was thinking of going back to gentoo to, but man it's around 6 hours to compile my kernel on this old rig, other things weren't to bad, while i was installing it, i suddenly just decided i didn't want to wait and the speed was faster than debian, but only by seconds. gentoo was my main os before i got into debian. 
i was trying to compile this->
[http://web.tiscali.it/tito-wolit/](http://web.tiscali.it/tito-wolit/)

when i called it quits on gentoo, i did the gentoo before arch.

---

### Post by mbsullivan on 2008-11-22
> 
I generally alternate between dwm and Openbox. I'm using mostly dwm these days. I spend a great deal of time in terminals and I find the tiling layout is handy for that, especially with dwm's bstack (bottom stack) patch.

Got any experience with Haskell? XMonad's a joy if you're into Functional Programming. 

Even if you don't have any Haskell experience, you might want to try it... it'd fit in well with your Gentoo/Slackware lots of free time lifestyle :)

As for other tiling window managers, AwesomeWM used to be quite nice, anyway... I stopped paying attention around v3.0, because I didn't feel like redoing my config file in Lua.

> Arch has some good features and ideas, but I'd prefer security announcements or (even better) a security team of some sort. At times, it just doesn't seem like they have the manpower to keep on top of the project.

The importance of user-made packages is probably the best and worst thing about Arch, right now. There's so much stuff in the repositories/AUR, but you're right... There's very little oversight.

> i suddenly just decided i didn't want to wait and the speed was faster than debian, but only by seconds. gentoo was my main os before i got into debian.

The question is... whether Gentoo's faster than Debian with 6 hours of tweaking :)

Mike

---

### Post by win4thebin on 2008-11-23
open terminal and try *sudo apt-get install fluxbox* or *sudo apt-get install fluxbox-desktop*:KS

---

### Post by RedSquirrel on 2008-11-23
> **kerry_s said:**
> i was thinking of going back to gentoo to, but man it's around 6 hours to compile my kernel on this old rig, other things weren't to bad, while i was installing it, i suddenly just decided i didn't want to wait and the speed was faster than debian, but only by seconds. gentoo was my main os before i got into debian. 
i was trying to compile this->
[http://web.tiscali.it/tito-wolit/](http://web.tiscali.it/tito-wolit/)

when i called it quits on gentoo, i did the gentoo before arch.

Six hours for the kernel? On my Duron 600 MHz machine, my custom kernel compiles in 25 minutes.

For me, Gentoo is more about fun and less about performance. I know my hardware well, and I enjoy picking appropriate settings and drivers. While there may be some small boost from this, I'm not expecting it to be "a thousand times faster" than other distros (at least not for the basic programs I run on my machine ;)).

By the way, I tried jwm a little while ago. It is pretty nice. For a "floating" WM, I prefer Openbox and its full range of customization options.

---

### Post by RedSquirrel on 2008-11-23
> **mbsullivan said:**
> Got any experience with Haskell? XMonad's a joy if you're into Functional Programming.

No, thanks. I'm still suffering from Scheme-induced brain damage! :evil:



> **mbsullivan said:**
> Even if you don't have any Haskell experience, you might want to try it... it'd fit in well with your Gentoo/Slackware lots of free time lifestyle

:lolflag:

I might try it someday. I've heard some good things about it. stumpwm is also a candidate. For those of us who don't spend a great deal of time programming in Haskell and/or Lisp, it seems silly to install all that stuff just for a WM. :D



> **mbsullivan said:**
> As for other tiling window managers, AwesomeWM used to be quite nice, anyway... I stopped paying attention around v3.0, because I didn't feel like redoing my config file in Lua.

I tried the pre-3.0 awesomeWM. It seemed OK, but it's more than I need. The basic dwm (with bstack) is sufficient for me. Some time ago, I read a few comments from the awesomeWM developer about the plans for awesome 3 and it didn't look like a good fit for me. No rush on that one.

---

### Post by mbsullivan on 2008-11-25
> For those of us who don't spend a great deal of time programming in Haskell and/or Lisp, it seems silly to install all that stuff just for a WM. 

Agreed. GHC's a massive dependency to have at this point. They've got a "Xmonad lite" in the works, that basically reads a config file like the old versions of Awesome. That might make it more of a general-purpose tiling manager.

> Some time ago, I read a few comments from the awesomeWM developer about the plans for awesome 3 and it didn't look like a good fit for me.

Yeah... I agree that the aim of Awesome seems to be going towards that of a more fully featured WM, which is not always a good thing. I once tried to install v3.0 from the source tree but got stuck in dependency hell, so I can't say much from experience.

Mike

---


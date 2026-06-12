---
title: "S-video cable to my TV"
date: 2008-06-27
forum: Desktop Environments
---

### Post by monnick on 2008-06-27
Hey fellow Ubuntu users,

I'm new to Ubuntu and to this forum, so hey all! :)

Well, let's start with my first problem. I bougt myself a s-video cable to watch my divx movies on my television. In Windows XP the cable works fine, but in Ubuntu I can't get it to work.

I've plugged the cable in to my grafic-card, a ATi RADEON x800 gt. After that I tried to enable 'duplicate screen' at the system->preferences->screenresolution (I don't know if that are the right words because I use the Dutch language pack), I also tried to let Ubuntu detect the TV, but no luck...

When I went searching I found that I might need to edit my /etc/X11/xorg.conf file. But I don't know how to do that, so can someone please tell me if the best solution is to edit xorg.conf and how to do it?

Thanks in advance!

---

### Post by Dr Small on 2008-06-27
I think you need atitvout

---

### Post by monnick on 2008-06-28
Thanks for the tip. I downloaded the program from the repos and I installed it. After that I went experimenting in the terminal with the problem. But it seems like I'm doing something wrong but I don't know what.

See below for what I tried, I hope you (or someone else) can help me! :)

```
tom@tom-desktop:~$ atitvout
atitvout 0.4 :: ATI Rage/Radeon TV Out configuration program
    Lennart Poettering <mz617469@poettering.de> 2001,2002
    http://www.stud.uni-hamburg.de/users/lennart/projects/atitvout/
    Licensed under the GNU General Public License, 
         http://www.gnu.org/licenses/gpl.html#SEC1

Supported commands:
    help: Shows this help.
    vbe: Show some information about the VESA BIOS Extension (VBE).
    tvout: Shows some information about the TV Out connector.
    standard: Shows some information about the used TV standard.
    pal*: Sets PAL mode.
    ntsc*: Sets NTSC mode.
    detect: Shows a list of attached displays.
    active: Shows a list of all active displays.
    auto: Activates all attached displays, deactivates all others.
    off: Deactives all displays.
    l,c,t,lc,lt,ct,lct: Activates the specified display, deactivates all
                        others. (l = LCD; c = CRT; t = TV)

Use the flags -f and -r for forcing Rage Mobility/Rage LT resp. Radeon/R128 mode.
* Not available on Radeon/Rage 128.

You may specifiy more than one command on the command line. An example:

    atitvout pal auto

This command line automatically enables an attached TV and sets it to PAL mode.

PLEASE NOTE: When using the ati driver of XFree 4.1 you should rerun this
utility always after having changed the screen resolution with C-A-+ or C-A--.
Otherwise the displays may go nuts.

PLEASE NOTE: Not all ATI adapters support all of these commands. Please try them
all before complaining.

PLEASE NOTE: Most cards do not allow to activate non attached displays. All calls
to atitvout will fail if you try to enable displays which do not show up in
'atitvout detect'.

PLEASE NOTE: Not all adapters seem to support simultaneously using TV and LCD from
within Linux. Thus 'lt' may fail, while 'l' and 't' succeed. In this case 'auto'
will fail too. In fact 'auto' works only on very few adapters.
tom@tom-desktop:~$ atitvout help
open /dev/mem: Permission denied
Could not initialise LRMI.
tom@tom-desktop:~$ sudo atitvout help
Failed to detect adapter type.
Use either -f or -r for forcing either Rage Mobility/Rage 3D Pro LT or Radeon/Rage 128 mode.tom@tom-desktop:~$ sudo atitvout help -r
Failed to detect adapter type.
Use either -f or -r for forcing either Rage Mobility/Rage 3D Pro LT or Radeon/Rage 128 mode.tom@tom-desktop:~$ sudo atitvout help -f
Failed to detect adapter type.
Use either -f or -r for forcing either Rage Mobility/Rage 3D Pro LT or Radeon/Rage 128 mode.tom@tom-desktop:~$ sudo atitvout tvout
Failed to detect adapter type.
Use either -f or -r for forcing either Rage Mobility/Rage 3D Pro LT or Radeon/Rage 128 mode.tom@tom-desktop:~$ atitvout help
open /dev/mem: Permission denied
Could not initialise LRMI.
tom@tom-desktop:~$ atitvout detect
open /dev/mem: Permission denied
Could not initialise LRMI.
tom@tom-desktop:~$ sudo atitvout detect
Failed to detect adapter type.
Use either -f or -r for forcing either Rage Mobility/Rage 3D Pro LT or Radeon/Rage 128 mode.tom@tom-desktop:~$ sudo atitvout detect -r
Failed to detect adapter type.
Use either -f or -r for forcing either Rage Mobility/Rage 3D Pro LT or Radeon/Rage 128 mode.tom@tom-desktop:~$ sudo atitvout auto
Failed to detect adapter type.
Use either -f or -r for forcing either Rage Mobility/Rage 3D Pro LT or Radeon/Rage 128 mode.tom@tom-desktop:~$ sudo atitvout active
Failed to detect adapter type.
Use either -f or -r for forcing either Rage Mobility/Rage 3D Pro LT or Radeon/Rage 128 mode.tom@tom-desktop:~$ 
```

---

### Post by monnick on 2008-06-28
Here's an update. Someone gave me the advice to download ATi Config tool from the repos. Well, after I succesfully installed it, the s-video cable and TV works fine! :)

---

### Post by tornado89 on 2008-06-28
You Can Also Download A Full Ati Catalyst Control Center 
Created By AMD..
go to Applications->Add/Remove Programs
And Search For It

U Can Use It To Control a Lot of 3D Effects and The Overall
Performance of Your Card...

Please Mark This Thread as SOLVED...

---

### Post by ragip on 2008-09-07
this post helped me a lot
thanks :)

---


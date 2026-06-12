---
title: "Cygwin and Remote Gnome-Session"
date: 2005-06-24
forum: Desktop Environments
---

### Post by Billybob on 2005-06-24
Hello,

I recently installed Ubuntu on a newly re-construsted slave machine. After a bad CD I got everything installed and working quite nicely :)
So I've moved on to my real goal which is to make this machine a slave, serving up remove sessions.
I've done this successfully before. Basically I have Cygwin/X installed on a Windows machine, I start up the X server on Windows, ssh into the slave machine with X forwarding, and then start kde/gnome.
So I modified my script a lil' to work with gnome (used KDE previously) and it worked successfully, but there's a few things I'd like to tweak and I'm hoping someone can help.

First off, Cygwin/X opens up a window on my primary monitor, and sizes it to that, which actually isn't what I want. I'd like to be to place the Cygwin/X window on my secondary monitor and have it full sized on that screen. The secondary is at a higher resolution (1280x1024. Primary is 1280x960). Is this possible?

Second, and this is an issue that has just come up with Ubuntu, worked fine on my old slave machine (Gentoo). When I try to log out it takes more time than normal. Normally it shouldn't take more than a second to display (are you sure?) the dialog, but now it's taking 10 to 20 seconds. Also, it never completes the logout. Gnome goes away, but the Ubuntu background remains and I have to ctrl+alt+backspace to close Cygwin/X window. Not a big deal...but if it could be fixed that'd be great.

Any help is greatly appreciated.

---

### Post by Michele Moglia on 2005-07-26
Sorry I cannot help you for your problem,
but perhaps you can help me because your results
are better than mine. Can explain me (step-by-step) how to have
a working remote session with cygwin ?
In my case I have 3 windows one for the desktop and two for the panel bars
and everything is very crazy.
Thanks for your help

Michele

---

### Post by moopere on 2007-01-05
> **Billybob said:**
> First off, Cygwin/X opens up a window on my primary monitor, and sizes it to that, which actually isn't what I want. I'd like to be to place the Cygwin/X window on my secondary monitor and have it full sized on that screen. The secondary is at a higher resolution (1280x1024. Primary is 1280x960). Is this possible?

$ X --help
use: X [:<display>] [option]

[snip]

-screen scr_num [width height [x y] | [[WxH[+X+Y]][@m]] ]
        Enable screen scr_num and optionally specify a width and
        height and initial position for that screen. Additionally
        a monitor number can be specified to start the server on,
        at which point, all coordinates become relative to that

         -screen 0 800x600+100+100@2 ; 2nd monitor offset 100,100 size 800x600
         -screen 0 1024x768@3        ; 3rd monitor size 1024x768
         -screen 0 @1 ; on 1st monitor using its full resolution (the default)

[snip]

This is probably what you want to know.  Better late then never huh? :)  

Cheers

---


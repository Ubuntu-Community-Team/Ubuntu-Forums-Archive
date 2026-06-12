---
title: "Confine mouse movement (&quot;mouse jail&quot;)"
date: 2009-06-07
forum: General Help
---

### Post by moritz-s on 2009-06-07
I'm looking for a utility that confines mouse movement to a certain area (e.g. a window or manually set coordinates). Seemed like a really simple problem, but I haven't found anything that would accomplish it. Note that a couple of programs have the ability to lock the mouse cursor to their own window built-in, mostly emulation software like VirtualBox -- that's exactly what I want, but for other windows.

My first thought was to see if Compiz offers anything, and indeed the Enhanced Mouse Zoom plugin lets you zoom in on a window and restrain mouse movement to the "field of vision". This kinda sorta works, but it's not elegant at all, and in fact only works when the window has the same aspect ratio as the screen. I also need to disable my right-hand display (run in TwinView), otherwise the cursor will move off the right side of the screen. And of course, the window is zoomed.

Another thing I found was on the Gentoo wiki: [http://en.gentoo-wiki.com/wiki/HOWTO...in_the_monitor](http://en.gentoo-wiki.com/wiki/HOWTO...in_the_monitor)

There's a link to a fairly simple C program which is supposed to confine the cursor to the current screen. Well, first of all this doesn't work for me, assumedly because TwinView registers both displays as one large screen. Apart from that, I assume the code could be adapted to limit movement to an arbitrary rectangle. On the other hand, it seems to work simply by polling, and, if necessary, resetting the position every millisecond, which is far from an elegant approach. The archive contains an executable as well as the code; I couldn't compile the code because I haven't, so far, installed the X development packages.

So yeah. I found numerous people who had the same problem, and I found approximately 100 programs which lock the mouse to a window/region in Windows, but apparently it's not as easy on Linux.

Any help is appreciated.

---

### Post by danitool on 2010-04-01
Same problem here, very annoying to have two displays and the mouse run away to the other screen.

I really want this feature: trap the mouse in a defined area.

Since to have two separate displays (DISPLAY=0.0 DISPLAY=0.1) with xorg and a desktop environment working on both is very difficult, there are no options now.

Please anyone has a workaround?

---

### Post by danitool on 2010-04-06
Well i found a script which uses xdotool to reset the mouse position. It consumes a lot of cpu, i added a sleep command to solve it. It is dirty fix but at least it works

[http://files.myopera.com/danitool/linux/restrainmouse.sh](http://files.myopera.com/danitool/linux/restrainmouse.sh)

```

sudo apt-get install xdotool
./restrainmouse.sh 500 500 1000 1000

```

of course you must use your coordinates of interest where to lock the mouse

---

### Post by pfanne on 2010-05-28
i wrote an additional script.
this allows you to automatically lock your mouse to the window that is focused at  the moment.
it will unlock if you dont focus the window
just bind the script to a hotkey.
if you run the script again it will kill the previously started instance of the script.
you need zenity, xdotool and xwininfo(which should already installed be on your computer)
[http://dl.dropbox.com/u/1250216/mousejail.tar.gz](http://dl.dropbox.com/u/1250216/mousejail.tar.gz)
just unzip all the files into the same folder.
i hope you will find this useful.

---

### Post by danitool on 2010-11-07
more stuff we can try:

mouse-wrapscreen

[http://digamma.cs.unm.edu/trac.dmohr/wiki/DualscreenMouseUtils](http://digamma.cs.unm.edu/trac.dmohr/wiki/DualscreenMouseUtils)

The site provides this software we can compile
[http://dsp.mcbf.net/releases/dualscreen-mouse-utils-0.5.tar.gz](http://dsp.mcbf.net/releases/dualscreen-mouse-utils-0.5.tar.gz)

---

### Post by woop12 on 2011-02-23
Hi

I had the same problem so I modified a small C program that i found on the gentoo wiki to do this job. It has the same idea as the script here but performs a bit better performance-wise in my opinion.

Hope it helps someone. Just modify the size of the "jail" in the shell script. It's set to (0|0) - (1280|1024) right now.

I am in no way a C expert, so use at your own discretion. Source is included.

---


---
title: "Expose in Openbox"
date: 2012-01-24
forum: Desktop Environments
---

### Post by Pharnavaziani on 2012-01-24
Hey,

I recently started using Openbox, xcompmgr, and AWN as an environment.  It performs great and once I iron out a few kinks I'd like to make it my default WM/session.  One of those kinks, however, is proving very intractable.

My biggest priority across all workspace environments - KDE, Gnome 2, Gnome Shell, and Unity - has been an 'expose' feature.  The ability to hit a button, the idly at my leisure see all/some of my windows, then select some is, for me, far superior to any Alt-Tab style task switcher.  It's also quick when needed, (sometimes :/) keyboard friendly, and can make sense from either a keyboard or mouse oriented view.

A few days ago I stumbled across *skippy *and *skippy-xd.  *I downloaded from source and I supposedly meet all the requirements, but my make command returns the following message (for either program):

> 
~/.skippy/skippy-xd-0.5.0$ sudo make
gcc -I/usr/X11R6/include `pkg-config xft xrender xcomposite xdamage xfixes --cflags` -g -pedantic -Wall -DXINERAMA -o skippy-xd skippy.c wm.c dlist.c mainwin.c clientwin.c layout.c focus.c config.c tooltip.c -L/usr/X11R6/lib -lX11 -lm `pkg-config xft xrender xcomposite xdamage xfixes --libs` -lXext -lXinerama
In file included from skippy.c:20:0:
skippy.h:26:29: fatal error: X11/Xmu/WinUtil.h: No such file or directory
compilation terminated.
In file included from wm.c:20:0:
skippy.h:26:29: fatal error: X11/Xmu/WinUtil.h: No such file or directory
compilation terminated.
In file included from dlist.c:20:0:
skippy.h:26:29: fatal error: X11/Xmu/WinUtil.h: No such file or directory
compilation terminated.
In file included from mainwin.c:20:0:
skippy.h:26:29: fatal error: X11/Xmu/WinUtil.h: No such file or directory
compilation terminated.
In file included from clientwin.c:20:0:
skippy.h:26:29: fatal error: X11/Xmu/WinUtil.h: No such file or directory
compilation terminated.
In file included from layout.c:20:0:
skippy.h:26:29: fatal error: X11/Xmu/WinUtil.h: No such file or directory
compilation terminated.
In file included from focus.c:20:0:
skippy.h:26:29: fatal error: X11/Xmu/WinUtil.h: No such file or directory
compilation terminated.
In file included from config.c:20:0:
skippy.h:26:29: fatal error: X11/Xmu/WinUtil.h: No such file or directory
compilation terminated.
In file included from tooltip.c:20:0:
skippy.h:26:29: fatal error: X11/Xmu/WinUtil.h: No such file or directory
compilation terminated.
make: *** [skippy-xd] Error 1


None of my Google searches have turned up with anything....
I'm running Ubuntu 11.10 64-bit.  My system has plenty of hardware power and everything has always worked out of the box with Linux, equalling or beating the OEM Windows 7 install on everything.  I'm wondering if my current version of X11 doesn't support this missing library skippy is finding, and if so what I can do about it (either help with skippy or replacement suggestions would be appreciated).  If I could combine the flexibility of AWN and Openbox with the awesomeness of expose window management and lightweight compositing, I'd be a happy, happy person.

Note:  thanks to ridetheteapot, the above problem is now solved! However, I am having another problem that prevents the programs from working correctly, which is described below.

---

### Post by ridetheteapot on 2012-01-24
You'll need to get the libxmu-dev package to fix that.
Thanks for the heads up on skippy - I just switched to openbox as well.

ps you shouldnt normally have to sudo make.

---

### Post by Pharnavaziani on 2012-01-24
Thanks for the help, I got skippy-xd compiled.

However, I still have a problem, and the program breaks as a result.  It compiled with the following warning: 
> 
~/.skippy/skippy-xd-0.5.0$ make
gcc -I/usr/X11R6/include `pkg-config xft xrender xcomposite xdamage xfixes --cflags` -g -pedantic -Wall -DXINERAMA -o skippy-xd skippy.c wm.c dlist.c mainwin.c clientwin.c layout.c focus.c config.c tooltip.c -L/usr/X11R6/lib -lX11 -lm `pkg-config xft xrender xcomposite xdamage xfixes --libs` -lXext -lXinerama
wm.c: In function &#8216;wm_get_stack&#8217;:
wm.c:261:20: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]



And when I attempt to use it, nothing happens.  I've already started the program in the terminal, which provides the following output:
> 
~/.skippy/skippy-xd-0.5.0$ ./skippy-xd
WARNING: Couldn't load config file '/home/matthew/.skippy-xd.rc'.
 
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  3 (X_GetWindowAttributes)
  Resource id in failed request:  0x0
  Serial number of failed request:  105
  Current serial number in output stream:  106


The first section is simply my starting the program with a warning, the second is what happens after I attempt to use the hotkey.  Any more suggestions or pointers would be great.

Note:  I have tried basically the same thing with the regular skippy program and gotten similar results:  it compiles with a warning, then crashes in use.

---

### Post by ridetheteapot on 2012-01-24
Ok that compile error \could\ be a gcc bug. what version of gcc are you running? 4.6 supposedly has fix - ubuntu 11.10 is rocking 4.6.1, but if your openboxing on crunchbang your probably running 4.4.5 and that could be your problem.

I'll try to compile on #! when I get home.

---

### Post by Pharnavaziani on 2012-01-24
Nah, I do have Oneiric and my gcc is 4.6.1

I'll check out the source code where the problem is happening later, see if that yields any clues.  It's a real surprise to me that skippy didn't get maintained...a lightweight app that can duplicate Expose seems to me like it'd be a winner.  I guess most people like Expose and Dashboard zooming interfaces for the eye candy more than the functionality, though.  But if I could get either version of skippy to work on this, it'd be perfect....the flexibility of Awn, low power of Openbox, and advanced window management is a hell of a combo.

---


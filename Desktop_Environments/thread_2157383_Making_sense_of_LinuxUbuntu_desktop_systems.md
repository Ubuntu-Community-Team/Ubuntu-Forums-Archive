---
title: "Making sense of Linux/Ubuntu desktop systems"
date: 2013-06-25
forum: Desktop Environments
---

### Post by argvar on 2013-06-25
X11
Nautilus
Compiz
gtk
gnome
unity
..


What the heck am I using in Ubuntu? All? What role does every one of those serve? I'm trying to make sense of all these terms and how the windowing system is built up.

---

### Post by Cheesemill on 2013-06-25
These may help...

[http://forums.linuxmint.com/viewtopic.php?f=90&t=54945#p314893](http://forums.linuxmint.com/viewtopic.php?f=90&t=54945#p314893)
[http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce](http://www.renewablepcs.com/about-linux/kde-gnome-or-xfce)

---

### Post by argvar on 2013-06-25
Still very confusing. I have no idea how everything works together. I have Ubuntu 13.04 desktop default setup, what am I using and how does it work together? How is this layered?

---

### Post by The Cog on 2013-06-25
OK, I'll have a stab:

X11:
The low-level graphics driver library. I think it provides functions allowing you to draw rectangles, circles etc. It may also have a basic ability to create a window to draw the graphics in. What is does not have is a window manager. 

Window manager: 
Without a running window manager, you can't move or resize windows at all: each window appears top-left and hides previous windows. The window manager provides the intelligence to move and resize windows according to mouse or keyboard input. I think it's the window manager that draws the borders and title round the windows too. 

Desktop:
A Desktop adds to the window manager by showing widgets like program launchers, menus, wallpaper, clock and so-on on the screeen. It is this that really provides the look and feel to the GUI.

Unity:
Unity is one of the available window managers/desktops. Actually, I think Unity is a desktop, and I don't know what window manager it uses underneath.

Gnome:
Another desktop. There are gnome2 and gnome3 at the moment. gnome2 is largely abandoned by the gnome community in favour of gnome3 which looks completely different. Plenty of room for which-is-best arguments. KDE, XFCE and LXDE are other competing desktops, each with a very different look and feel.

Nautilus:
A file manager, like the windows explorer. Written by the gnome people. Use it to look in directories, drag/drop/open/delete files. I think some of its ability to display an icon view of a folder is sometimes used by the gnome desktops to put icons from the Desktop directory on the screen just in front of the wallpaper.

Compiz:
An extra plugin that can add eye candy to the display. I guess it classes as a window manager. It can make windows disappear in a burst of flame when you close them, or wobble like jelly as you drag them around. It can also do the desktop cube where the whole screen seems to be on the side of a cube that rotates to show you a new face when you change desktops. [http://www.youtube.com/watch?v=de3eiwKqnUs](http://www.youtube.com/watch?v=de3eiwKqnUs)

GTK:
Gnome ToolKit. There are versions 2 and 3 still around. Software library full of utilities for drawing widgets like buttons, checkboxes, sliders etc. These are used by many programs. Programs using these toolkits to draw their widgets will all look very consistent when running on a gnome desktop but mak look slightly out-of-place when running on other desktops such as KDE. They seem to look fine to me running under XFCE. There are several other toolkits out there, notabbly the KDE one but GTK is probably the most popular.

With a default recent Ubuntu, you will be using Unity desktop, don't-know window manager, layered over X11 graphical drivers. Nautilus will be your file explorer. Most of the applications installed will be using GTK buttons and sliders. You will not be using compiz.

I probably have a lot wrong and will probably get a lot of corrections. But I hope that gives you a start, anyway.

---

### Post by grahammechanical on 2013-06-25
To put it simply. Ubuntu is not an operating system it is a Linux distribution. The Gnu/Linux OS is made up of many components, just like the Windows operating system. Whichever Linux distribution you choose, you will find that it is using similar, if not the same, components as the Ubuntu distribution.

It is a feature of Free and Open Source software, that anyone can take software written by someone else and use it with software written by other people. So, long as they keep to the terms of the licence agreements.

This is why we speak of the Open Source Community. You should look upon Linux distributions as community-cooperative products with different groups of developers taking responsibility for different parts of the software universe.

With Linux we get to see more of the underlying components then we do with proprietary operating systems. But strange sounding components are there in proprietary operating systems just the same.

Look at these strange names as a manifestation of the sense of humour of open source developers.

Regards.

---

### Post by argvar on 2013-06-25
I've been around long enough to know what Linux is, was using slackware with x11 back in 1996, but only for a short while as it was useless. So been in windows ever since.

But recently started using it again for the desktop and I'm wondering how all these different parts fit together to bring me this windowing system that I am using. I'm interested because I'm a programmer, with emphasize on user interface design and graphics programming (opengl and such).
I hear terms as x11, compiz, unity, gnome, gtk(+), but don't know who is doing what, who is providing me with this and that, drawing those lines or those buttons. Would be interesting to see some diagram or flowchart or whatever.


I'm just trying to understand the current state of affairs in the windowing system for linux. It seems to me there are a lot of libraries out there and variations/distros that have a different desktop. There's a lot of work being put into bunch of mediocre alternatives, but little work into making a proper desktop environment. I think it's kinda sad.

Alright :)

---

### Post by vasa1 on 2013-06-25
I think people here have made a decent attempt to explain things :)

---

### Post by SeijiSensei on 2013-06-25
> **argvar said:**
> I'm just trying to understand the current state of affairs in the windowing system for linux. It seems to me there are a lot of libraries out there and variations/distros that have a different desktop. There's a lot of work being put into bunch of mediocre alternatives, but little work into making a proper desktop environment. I think it's kinda sad.

It's also pretty uninformed.  I have used KDE for years and do not consider it "mediocre" in any way.  The vanilla Ubuntu desktop has undergone a lot of changes in the past couple of years occasioned by the transition to GNOME3 and the adoption of Unity.  KDE is built on Qt which continues to be maintained even after it was abandoned by Nokia when that firm became the phone division of Microsoft.  As a developer you might want to read this:  [http://qt.digia.com/](http://qt.digia.com/).

KDE is often accused of being "bloated," but that's hardly the case today, especially on modern hardware.

Yes there are lots of different distros out there, but the mainstream ones like Fedora, Ubuntu, and SuSE use either a GNOME derivative or a version of KDE.  XFCE and LXDE are nice for machines with weaker hardware, but they command a much smaller share of Linux desktops than KDE or GNOME derivatives.

Furthermore there are lots of us who use Linux as a server operating system.  In that setting the graphical desktop matters hardly at all.  When managing servers, I spend most of my time at the command prompt in an SSH session.

---

### Post by vasa1 on 2013-06-25
[http://pclosmag.com/index.html](http://pclosmag.com/index.html) has a series of articles meant for those migrating from Windows. For example, see page 7 in this pdf: [s][http://pclosmag.com/download.php?f=2013-06.pdf](http://pclosmag.com/download.php?f=2013-06.pdf)[/s]

Oops! The second link should be [http://pclosmag.com/download.php?f=2013-04.pdf](http://pclosmag.com/download.php?f=2013-04.pdf)

---

### Post by MG&amp;TL on 2013-06-25
> OK, I'll have a stab:

It's an impressive stab. I hope you won't mind me making a few points for information's sake. :)

> X11:
The low-level graphics driver library. I think it provides functions allowing you to draw rectangles, circles etc. It may also have a basic ability to create a window to draw the graphics in. What is does not have is a window manager. 


X11 is an implementation of an [X_Window_System]("http://en.wikipedia.org/wiki/X_Window_System"), which is a standard that allows seamless operation of graphical programs across any system that implements X. It provides networking capabilities, windowing (keeping track of window attributes), hardware devices (what exactly should typing on a keyboard do in a graphical world? A mouse?), and optionally extended features such as hardware acceleration.
However, X itself does not control how windows are displayed or managed. That is the job of the window manager.

> Window manager: 
Without a running window manager, you can't move or resize windows at all: each window appears top-left and hides previous windows. The window manager provides the intelligence to move and resize windows according to mouse or keyboard input. I think it's the window manager that draws the borders and title round the windows too. 

Window managers are programs that run on top of X11 and control how the windows are presented and managed. For example, *KWin*, a window manager, produces an entirely different look and feel to, say *ratpoison*, another window manager. Window managers are arguably the most visible part of the stack that you mention.

> Unity:
Unity is one of the available window managers/desktops. Actually, I think Unity is a desktop, and I don't know what window manager it uses underneath.

Unity is unusual in that is both a window manager *and* a desktop. Usually, these parts are split, but the *unity* program draws both the interface and the windows. (See 'not using compiz')

> Compiz:
An extra plugin that can add eye candy to the display. I guess it classes as a window manager. It can make windows disappear in a burst of flame when you close them, or wobble like jelly as you drag them around. It can also do the desktop cube where the whole screen seems to be on the side of a cube that rotates to show you a new face when you change desktops. [http://www.youtube.com/watch?v=de3eiwKqnUs](http://www.youtube.com/watch?v=de3eiwKqnUs)


Compiz is a compositing window manager. *Compositing* window managers are quite different internally from other window managers. 'Normal' window managers manage where the applications draw pixels to screen directly, by telling them where in memory to draw to. Compositing window managers tell applications to draw their pixels into a buffer, then the window manager itself handles the drawing of the windows to the screen.
This allows the window manager to perform effects such as 'wobbling' windows when they are moved, or the famous 'desktop cube', simply by manipulating the display they themselves are drawing, which is obviously not possible with conventional indow managers.

> GTK:

Gnome ToolKit. There are versions 2 and 3 still around. Software library full of utilities for drawing widgets like buttons, checkboxes, sliders etc. These are used by many programs. Programs using these toolkits to draw their widgets will all look very consistent when running on a gnome desktop but mak look slightly out-of-place when running on other desktops such as KDE. They seem to look fine to me running under XFCE. There are several other toolkits out there, notabbly the KDE one but GTK is probably the most popular.

The 'KDE one' is known as Qt.

> You will not be using compiz.


Slightly incorrect. Unity is (I believe, Unity development hops about a bit) implemented as a somewhat monolithic Compiz plugin. So really, you are using Compiz, but Unity does a lot of its own things, so it's very difficult to tell that you are in fact using Compiz. Compiz, however, does draw the windows, but the two have become so intertwined that running Unity without Compiz is impossible and Compiz without Unity is radically different.

> I probably have a lot wrong

Not at all! Just my inner pedant grumbling as per usual. Hope I got it right.:)

---

### Post by VanillaMozilla on 2013-06-25
OK, closing in on this.  Just a few comments to keep it simple.

GTK (Gnu toolkit -- or Gnome toolkit?) is a *programming* toolkit.  You'll never need to use it or install it, and ordinarily you don't need to be concerned with it.  If you are told that a program is built with gtk or qt, however, that describes how the program looks.

Gnome version 2 has been replaced in most distributions with Gnome version 3, or "Gnome 3".  The Gnome Shell runs on top of Gnome 3, and it essentially gives you the panel or bar that you use to run the computer.  Unity is Ubuntu's alternative, and is somewhat similar.

Oh--and very important.  If you don't like Unity, you can install gnome-fallback or something (varies by version) and select Gnome Classic without effects at the login page.

Just to make it even more complicated, Compiz has been largely replaced, I think by something called "Mutter".  And X11 will be going away, to be replaced by either of *two* replacements.

Simple, no?  :(  :)

---

### Post by CharlesA on 2013-06-25
> **VanillaMozilla said:**
> OK, closing in on this.  Just a few comments to keep it simple.

GTK (Gnu toolkit -- or Gnome toolkit?) is a *programming* interface.  You'll never need to use it or install it, and ordinarily you don't need to be concerned with it.  If you are told that a program is built with gtk or qt, however, that describes how the program looks.

It also tells you what dependencies it will likely use (Gnome vs KDE). More info on GTK if anyone is interested can be found on their website. ;)
[http://www.gtk.org/](http://www.gtk.org/)

---

### Post by VanillaMozilla on 2013-06-25
> **CharlesA said:**
> It also tells you what dependencies it will likely use (Gnome vs KDE). More info on GTK if anyone is interested can be found on their website. ;)
[http://www.gtk.org/](http://www.gtk.org/)
OK, some more explanation.

Fortunately, with Linux you don't have to worry about dependencies, because they are handled automatically.  ("Dependencies is a funny computerese way of specifying what components are required to run a program.)

Most programs come in one of two different types -- Gnome or KDE (Gnome uses GTK; KDE uses QT, but you don't have to write that down).  The two types look a little different and the menus, etc. may act a little different.  (Remember that KDE is a different desktop and looks different from Gnome.)

Ubuntu comes with Gnome programs, but don't let that stop you.  Some of the best programs are KDE programs.  If you want to install and use a KDE program (example:  K3b), go right ahead.  The first KDE program you install will cause a little extra stuff to be installed (not much, really), but that is ordinarily not any problem at all unless you are extremely low on disk space.  It won't make any difference in the way your computer runs, and you might not even notice anything different about the KDE program.

---

### Post by tgalati4 on 2013-06-25
Linux is simply made up of frameworks.  It takes 10 years to understand how the frameworks work together.  And by that time, the frameworks will change.

---

### Post by SurfaceUnits on 2013-06-26
[http://www.freedesktop.org/wiki/](http://www.freedesktop.org/wiki/)

---

### Post by argvar on 2013-06-26
Thanks :)

Bunch of framesworks and libraries, each doing their part.

---

### Post by Skara Brae on 2013-06-26
> **argvar said:**
> X11
Nautilus
Compiz
gtk
gnome
unity
..


What the heck am I using in Ubuntu? All? What role does every one of those serve? I'm trying to make sense of all these terms and how the windowing system is built up.
As a programmer, you seem to know very little about GNU/Linux. I am just a "stupid" Linux user, I know zilch about programming, hacking, compiling, you name it :p, and I seem to know more than you (I don't mean this in a bad way). You should start reading up about the "parts" of Linux.

---

### Post by buzzingrobot on 2013-06-27
The answers to the OP's questions are going to come from developer resources and (gasp!) books, not from a user forum.

Apple maintains considerable online resources explaining the OS X stack, for an alernative approach.

The use of Windows as the standard for goodness and beauty in software is,of course, incorrect.

---

### Post by buzzingrobot on 2013-06-27
> **argvar said:**
> I've been around long enough to know what Linux is, was using slackware with x11 back in 1996, but only for a short while as it was useless. 

Unless you wanted to run a Unix system.  In that case, Slackware was very useful, whie DOS/Windows was a waste of time and money.

---

### Post by SeijiSensei on 2013-06-27
> **buzzingrobot said:**
> Unless you wanted to run a Unix system.  In that case, Slackware was very useful, whie DOS/Windows was a waste of time and money.

Indeed.  I was buiilding routers and servers in 1996, first on Slack and later on RedHat (RPM was an enormous step forward).  I guess my clients who were using these "useless" machines must have been deluded.

---


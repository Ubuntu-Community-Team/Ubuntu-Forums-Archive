---
title: "Window Managers?"
date: 2005-02-02
forum: Desktop Environments
---

### Post by Kakalto on 2005-02-02
I hope this is the right place, I'm wanting to find out about Window Managers, hopefully someone will provide a comparison.

At the moment, I've only used KDE and GNOME, and have liked GNOME better, but I'm curious about other ones like IceWM and XFCE. Are they any good?

---

### Post by Randabis on 2005-02-03
[QUOTE=Kakalto]I hope this is the right place, I'm wanting to find out about Window Managers, hopefully someone will provide a comparison.

At the moment, I've only used KDE and GNOME, and have liked GNOME better, but I'm curious about other ones like IceWM and XFCE. Are they any good?[/QUOTE]

You're going to get a million different answers. Try a few and decide for yourself. You can always remove them later.

XFCE is my favorite. It does everything I need it to and looks awesome (expecially the latest release).

---

### Post by darkoptix on 2005-02-03
I agree with XFCE being great, It's small, simple, and works flawlessly on my p3.
I have not got a chance to use ICEwm.

---

### Post by Kakalto on 2005-02-03
Is XFCE hard to install?

Can you think of any other window managers?

---

### Post by frontline3k on 2005-02-03
XFCE 4.2 is really great.
Don't use Os Works repository (cause me lots of troubles), use XFCE from Backports ([http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net)).
Backports has version 4.1.1099.2+cvs.20041211, and basically, this is the same thing like 4.2.

Give it a try, you'll love it.

---

### Post by Randabis on 2005-02-03
I used the OS works graphical installers to install XFCE 4.2...No problems whatsoever. Just had to install the dependencies.

Other window managers:

Windowmaker, Fluxbox, blackbox, openbox, enlightenment, and some others.

---

### Post by Quest-Master on 2005-02-03
XFCE is, in my opinion, the best lightweight desktop out there. ;)

---

### Post by poofyhairguy on 2005-02-03
[QUOTE=Quest-Master]XFCE is, in my opinion, the best lightweight desktop out there. ;)[/QUOTE]


By far.....if only it had desktop icons.....I get spoiled to Gnome putting my USB drive on the desktop.

---

### Post by Kakalto on 2005-02-03
[QUOTE=frontline3k]XFCE 4.2 is really great.
Don't use Os Works repository (cause me lots of troubles), use XFCE from Backports ([http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net)).
Backports has version 4.1.1099.2+cvs.20041211, and basically, this is the same thing like 4.2.

Give it a try, you'll love it.[/QUOTE]
Thanks. I will try it.

[QUOTE=Randabis]I used the OS works graphical installers to install XFCE 4.2...No problems whatsoever. Just had to install the dependencies.

Other window managers:

Windowmaker, Fluxbox, blackbox, openbox, enlightenment, and some others.[/QUOTE]
Since I don't know what the "OS works graphical installer" is, I think I'll just use the backport, unless you could give me an explanation?

I've heard of enlightenment before, but is it any good?

---

### Post by eBopBob on 2005-02-03
In my opinion the best are XFCE and Gnome.

What I love about XFCE is that it is simple and it looks soo much better than KDE in my opinion - however it is not simply in a bad way, however a very good way. It's very easy to use, very lightweight and very logical - great if you don't have a very fast computer.

Gnome is also great, however you already know that. ;)

If I were to say which I think is better, it'd be a very hard choice. I like XFCE because it's faster IMO. However what I like about Gnome is all the programs - although you can use Gnome's programs in XFCE. Also what is great about Gnome is Gnome-Look - Shame XFCE doesn't have one AFAIK.

---

### Post by vcg3rd on 2005-02-04
[QUOTE=Kakalto]I hope this is the right place, I'm wanting to find out about Window Managers, hopefully someone will provide a comparison.

At the moment, I've only used KDE and GNOME, and have liked GNOME better, but I'm curious about other ones like IceWM and XFCE. Are they any good?[/QUOTE]

I agree that XFCE is by far the best of the lightweight window managers.  I like Afterstep, also, though.  My Ubuntu disk is on its way --on dial-up downloading even one disk is a three day BitTorret job--and it seems from what I'm reading that Gnome is the default/only provided desktop manager.

Is this right?  I like Gnome, but for full-blown desktop managers I prefer KDE.  Is KDE in the repositories?

---

### Post by Randabis on 2005-02-04
[QUOTE=vcg3rd]I agree that XFCE is by far the best of the lightweight window managers.  I like Afterstep, also, though.  My Ubuntu disk is on its way --on dial-up downloading even one disk is a three day BitTorret job--and it seems from what I'm reading that Gnome is the default/only provided desktop manager.

Is this right?  I like Gnome, but for full-blown desktop managers I prefer KDE.  Is KDE in the repositories?[/QUOTE]
Virtually all of the popular WMs/DEs are in the universe repository.

---

### Post by Randabis on 2005-02-04
[QUOTE=Kakalto]Thanks. I will try it.


Since I don't know what the "OS works graphical installer" is, I think I'll just use the backport, unless you could give me an explanation?

I've heard of enlightenment before, but is it any good?[/QUOTE]

[http://www.xfce.org](http://www.xfce.org)

Click Graphical Installers

---

### Post by poofyhairguy on 2005-02-04
[QUOTE=Randabis][http://www.xfce.org](http://www.xfce.org)

Click Graphical Installers[/QUOTE]


using their debian repo worked great for me!

I will admit it needed packages that are in the backport repo though. 

The graphical installer is cool.....but still doesn't fix its own dependancies.

---

### Post by Randabis on 2005-02-04
[QUOTE=poofyhairguy]
The graphical installer is cool.....but still doesn't fix its own dependancies.[/QUOTE]
I don't follow. What do you mean?

---

### Post by poofyhairguy on 2005-02-04
[QUOTE=Randabis]I don't follow. What do you mean?[/QUOTE]

when you install something using apt-get (or synaptic, same thing), the program goes and installs all of the other packages (programs) you need for the program you want to install to run. What a program needs to run other than itself is called a dependancy. 

The graphic installer automatically compiles XFCE and installs in on your computer. What it does not do is find all the dependecies it needs to install. Such as a compiling program for instance.

When you install with apt-get/synaptic it gets everything you need. Its the easiest way.....I tried using XFCE graphic installer but I quit when I was forced to manually get every dependancy myself. I'm lazy.

But I have XFCE working great right now on my laptop. I added these three lines to my sources.list:

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe
deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports-staging main universe
deb [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main

steps to add that are found here:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

The I opened synaptic, clicked refresh, and searched for and installed XFCE 4.2


It works great. Easier to do than using the installer, an it will be easier to update oneday.

Edit: be sure to add all three lines. The os-works' repo needed things that were in jdongs (the backport repo).

---

### Post by Randabis on 2005-02-04
[QUOTE=poofyhairguy]when you install something using apt-get (or synaptic, same thing), the program goes and installs all of the other packages (programs) you need for the program you want to install to run. What a program needs to run other than itself is called a dependancy. 

The graphic installer automatically compiles XFCE and installs in on your computer. What it does not do is find all the dependecies it needs to install. Such as a compiling program for instance.

When you install with apt-get/synaptic it gets everything you need. Its the easiest way.....I tried using XFCE graphic installer but I quit when I was forced to manually get every dependancy myself. I'm lazy.

But I have XFCE working great right now on my laptop. I added these three lines to my sources.list:

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe
deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports-staging main universe
deb [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main

steps to add that are found here:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

The I opened synaptic, clicked refresh, and searched for and installed XFCE 4.2


It works great. Easier to do than using the installer, an it will be easier to update oneday.

Edit: be sure to add all three lines. The os-works' repo needed things that were in jdongs (the backport repo).[/QUOTE]
No need for a lecture. :) I already knew all that. I just wasn't exactly sure what you meant. 
I just installed the dependencies myself. It tells you what's missing. It would be nice for it to grab them itself yeah.

---

### Post by ratpoison on 2005-02-04
[QUOTE=Randabis]I used the OS works graphical installers to install XFCE 4.2...No problems whatsoever. Just had to install the dependencies.

Other window managers:

Windowmaker, Fluxbox, blackbox, openbox, enlightenment, and some others.[/QUOTE]
"some"??  more like over 100 others ;-)
For really lightweight try ion or wmi, or one of my favorites, **ratpoison**....

---

### Post by regeya on 2005-02-14
I'm running Window Maker...well, really, back to running Window Maker after not having used it for darn near three years.

There's enough going on there that you can't learn everything there is to know about Window Maker by just firing it up, wrinkling up your nose, and saying "eww, gross, ugly" as you plan to run back to GNOME and your vast collection of gDesklets. ;)

Then again, I've been using OS X for a while so Window Maker does seem a bit quaint these days.  However, it has some features I really love, such as Workspaces and the Clip.  Rather than just having a Pager, you have a dynamic number of virtual desktops, changable through the Applications menu.   You also have Alt+Number access to the Workspaces, but that's another story.  Really, the brilliant thing about Workspaces is that the Clip can collect appicons much as you can collect appicons on the Dock, but you can set up different collections of appicons based on Workspace.  For example, I have a Main desktop, where I've clipped Grip, Synaptic, Emacs, and a few other apps.  Then there's the Internet Workspace, where I've clipped Firefox and Evolution, among other apps.  And I have a Video workspace, a Graphics workspace, and an IRC workspace, with their own set of clipped apps.

I could go on to other things such as GUI configuration, assigning keystrokes to various tasks, etc. but I think it'd be more appropriate for me to do a separate writeup on the Best Windowmanager Ever(TM). ;)

Really, I haven't found a more powerful, user-friendly environment in Free *n?x space, and I'm wondering if it will be surpassed in this decade.  With the current emphasis on user-friendliness and simplification, I'm thinking not.  :-)

---

### Post by KiwiNZ on 2005-02-16
I am awaiting the next release from Gnome , I like the way they are heading.

---

### Post by somuchfortheafter on 2005-02-16
come on what about all the fluxbox users out there, now that is a window mananger

---

### Post by slackerj on 2005-02-16
Was a GNOME man. Then XFCE. Changed to Blackbox (very nice). And now back to GNOME.

Started back with GNOME 2.4 under SUSE. But greatly hated that. But decided to continue on using it. In all honesty the reason I picked Ubuntu for my OS was because it had GNOME 2.8 installed as the default GUI :)

The most important thing for me is having plenty of screen real estate to play with (hate having a cluttered desktop). As long as thats the case Im a happy penguin :cool:

---

### Post by Kakalto on 2005-02-17
Is there a relation between fluxbox and blackbox?

---

### Post by QzarBaron on 2005-02-17
[QUOTE=Kakalto]Is there a relation between fluxbox and blackbox?[/QUOTE]

I think Fluxbox is based off Blackbox with more features.

How does one go and install Fluxbox in Ubuntu? I tried using Synaptic but the version they have is horribly out of date. I would compile my own but I don't know if it will move over menus and add Fluxbox to the gdm. Any ideas?

---

### Post by Kakalto on 2005-02-17
I'm just about to try out fluxbox... I downloaded the debian package from [here](http://logicvortex.net/debian/fluxbox/), and I'm hoping it isn't too hard to get working.

---

### Post by QzarBaron on 2005-02-18
[QUOTE=Kakalto]I'm just about to try out fluxbox... I downloaded the debian package from [here](http://logicvortex.net/debian/fluxbox/), and I'm hoping it isn't too hard to get working.[/QUOTE]

I tried to instal that package but it won't work because of some menu issue.

---

### Post by somuchfortheafter on 2005-02-18
try compiling your own, the fluxbox documentations is great and there are numerous threads on the forum about adding it to gdm

---

### Post by Kakalto on 2005-02-21
I installed that package, and it came up on the list at the login screen. Works Great.

---

### Post by SurreaL on 2005-02-26
I've been meaning to give a different window manager a shot after seeing how gnome can be a bit sluggish on my p3 laptop.. XFCE sounds like just the ticket, but after adding the 3 repositories to my sources list I get the following errors when trying to use synaptic to install XFCE 4.2:

"Could not mark all packages for installation or upgrade.
xfce4:
 Depends: xfprint4 but it is not going to be installed
 Depends: xfce4-cpugraph-plugin but it is not going to be installed"

Are there perhaps any other sources I should be adding to my apt-get sources list?

Thanks :)

---

### Post by rosslaird on 2005-02-26
The most efficient way to install xfce is by way of the graphical installers available from os-cillation.com. Get 'em [here](http://www.os-cillation.com/article.php?sid=42)

---

### Post by ]Nbx*cmD[ on 2006-02-09
I'm looking for ratpoison ubuntu users to create a thread and exchange scripts, aliases, bindings... and help, sure :)
But i'd need to know how many of you use it, maybe we are only two person and, in that case, we can e-mail each other lol

---

### Post by kabus on 2006-02-09
I'm a ratpoison user.
I basically just use it to switch between a fullscreen terminal running screen and a second window running Firefox, so I haven't put much work into configuration

I'd be interested in a thread about more advanced uses of ratpoison, though.

---

### Post by bluevoodoo1 on 2006-02-13
I don't think anyone has posted this link yet... (??)

[http://xwinman.org/](http://xwinman.org/)

but there are a bunch of WMs listed there.  (I'm partial to Blackbox) :)

---

### Post by horsefactory on 2006-02-17
I find Gnome awesome as a total package but Fluxbox is a great minimalist wm and as a mac nerd I have an appreciation of Windowmaker.

---

### Post by fuscia on 2006-02-17
i'm a big fan of ratpoison, but i'm also a drunk (making it pretty rough to remember all that keyboard stuff), so i go with openbox.

---


---
title: "Compiz freezes with ATI on KDM"
date: 2006-06-10
forum: Desktop Environments
---

### Post by elbryan on 2006-06-10
Let's start ..
I need to configure my compiz with ati and kde a little more ..
I know.. i've almost done it .. i can feel it!! ^^

First of all I've followed this guide:
[http://ubuntuforums.org/showthread.php?p=845077]("http://ubuntuforums.org/showthread.php?p=845077")
I've set up all that in order to make it working with my ATI (Acceleration 3D ok, fglrx driver works very well).

Now.. when kdm starts I can only see the mouse pointer (with clock pointer, the same when normally linux loads something) on a weird screen (it's seems green/grey a lot of strange color).
After that my system stops .. no hard disk movement .. nothing.

I've found the problem is that:
```

ServerCmd=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer 

```
if I comment this out and I reactive old ServerCmd everything works but no Xgl or compiz.

There are a lot of guide about compiz (someone modify ..kde3/kdmrc, someone Autostart and someone else make a .Xsession).

I've a terrible confusion in my head but, with your help, I'm sure that I can rid it of!

Omg .. my english :P sorry!

---

### Post by elbryan on 2006-06-10
up :'( help me!

---

### Post by gogators on 2006-06-10
I have had alot of issues with your configuration.  I have gotten farthest using this guide: [http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)

I might undo those changes as best as I could and try that.  Its only a 3 step process since it uses the dapper repository.  My only problem is that once I get kde all up and running with compiz, my window decorations are missing.  I have a thread on here working on that right now.

---

### Post by gogators on 2006-06-11
So an update.  I got my window decorations working in kde but in a kinda scrappy way.  If you use the method described in the link but instead of using compiz-kde, use compiz-gnome.  Also you need to start the gnome-window-decorator instead of kde-window-decorator.  This will make it all work in kde!  Here is a copy of my .Xsession for an example:

```

#!/bin/sh
# start up Xgl, compiz, and KDE
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
# Start Compiz window manager
gnome-window-decorator &
compiz --replace gconf decoration fade minimize cube rotate zoom scale move resize place switcher water &
# Start KDE
exec startkde

```

Please let me know if you find a way to get this to work with kde-window-decorator

---

### Post by elbryan on 2006-06-11
I've done what you have wrote down..
I've rebooted my machine and logged in KDE as normal .. I can see no difference.

All seems normal .. how can I see if my compiz works?

---

### Post by gogators on 2006-06-11
Quick check:  Are you running gdm or kdm?
Did you set the permissions for the .Xsession file?
In KDM make sure you are using the "default" window manager.

If its working you should see cool effects all over the place... like when you use the k-menu and stuff.  You should be able to rotate your desktops with ctrl+alt+left/right and the alt tab screen has changed too.  The KDM default window manager thing I mentioned above has been a problem for some people.  Lemme know if these things might apply to you.

---

### Post by elbryan on 2006-06-11
I'm running kdm at start (kdm I think is the login-manager, no?)
After I log in KDE with user and password.
I've set the permissions for .Xsession to 755 (+x).

I don't know what does mean "default" window manager.
Maybe there are some errors in xorg.conf.

However I can't see effects or I can't rotate desktops...

Thank you for your supporting .. I know we could make it!

---

### Post by gogators on 2006-06-11
Kmenu->Logout->End Current Session

At KDM

Menu -> Session Type -> Make sure that default is selected.  Hopefully this was your problem!

---

### Post by elbryan on 2006-06-11
No no .. the default is KDE! :'(

---

### Post by gogators on 2006-06-11
Oh well I was just checking because if the option "default" isn't selected then it doesn't load your .Xsession file.  

What I would do next is try to find any other guide that does this for kde/ati.  Next, find the changes they make to kdmrc and apply them to your own kdmrc file.  This is the alternate way of starting xgl/compiz.  I haven't tried it but if you can't find what I am talking about I would be glad to lead you in the right direction.  

I am getting the impression that using the dapper current repository for xgl/compiz is the way to go.  If anyone has a reason otherwise I really want to know.  It is working great for me.  So many other guides have other repositories but I have been under the impression that they were outdated.

---

### Post by elbryan on 2006-06-11
Ok I'm stupid!
I've selected default and I can see now that something is being loading ..
During that (slow) process a dialog show up that say (it's in italian, I try to translate it for you):
"the process of the system protocol has died suddently".

After all system seems hanged although not at all.. the menus show up but refresh is slow and my bottom panel can't load programs in the tray ..

What could it be?

EDIT: 3D acceleration is on with fglrx driver..

---

### Post by elbryan on 2006-06-11
Maybe this could be helpful:
```

elbryan@ubuntu:~$ compiz.real: Screen 0 on display ":1.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real: No managable screens found on display :1.0

```

now I'll try to do that replace .. uhm i hope in a hand from the sky :P

EDIT: Negative .. nothing works: the aren't window's title bar ...

---

### Post by gogators on 2006-06-11
Hmmm.. from your attempts before did you remove the old versions of compiz and xgl?  Then take them off your sources.list file, then install with the dapper version?  Also are you using the .Xsession file I posted?  If not post me yours.

---

### Post by gogators on 2006-06-11
Oh also, I have no programs in the task bar below either.  I think this is just part of running this in KDE.  When I have some time I want to see if these issues are in Gnome.  Well lets fix your other problems first before we get to this.

---

### Post by elbryan on 2006-06-11
old version?
I've installed compiz, compiz-kdm and compiz-gnome (version is: 0.0.2-4ubuntu2) downloaded with synaptic..
My xgl (xserver-xgl) version is 7.0.0-0ubuntu4 ..

I'm using your .Xsession :)

---

### Post by gogators on 2006-06-11
When did you get this error? :

```

elbryan@ubuntu:~$ compiz.real: Screen 0 on display ":1.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real: No managable screens found on display :1.0

```

---

### Post by elbryan on 2006-06-11
I logged into Default and started the Terminal..
Then I launched compiz and I've posted you the feedback..

Now that I think.. my xorg.conf is the default one.. I've only modified the "ati" into "fglrx" to enable 3D acceleration..

---

### Post by gogators on 2006-06-11
Do you have this entry somewhere in your xorg.conf?

```

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a

```

I hear the the dri part is very important for ati cards.

---

### Post by elbryan on 2006-06-11
My module configuration into xorg.conf
```

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

```

---

### Post by gogators on 2006-06-11
:( I have no idea!  Lemme sit on it for a while.  I'll keep in touch with this thread.

---

### Post by elbryan on 2006-06-11
Thank you so much for you effort ..
I appreciate this very much :)

---

### Post by gogators on 2006-06-11
Its s stretch -- but to see if it has to do with how its working with kde, try it for gnome.

---

### Post by elbryan on 2006-06-11
Wait .. tomorrow I'll format and redo a fresh install..
After that I'll follow what have you done for your ubuntu.

I have other problems with keyboard and other stuff (my system crashes when I reboot it and I have to press reset and redo fsck every time .. it's quite annoying).

Maybe you have MSN or ICQ so we will do this early..

If in this way the things won't resolve, I'll give up definitively..

Good Night :)

---

### Post by elbryan on 2006-06-12
Ok i'm back! ^^

I'm ready to try another time ..

---

### Post by elbryan on 2006-06-12
Hurraaah.. it works .. not very well but it works ..
I can't see the window's title bar and it gives me an error but I can swap my desktop with effects and menus have effects too ..

What should I do now? There's a way to resolve at this?

---

### Post by gogators on 2006-06-12
Oh awesome.  I didn't notice this post.  :( :( I got stuck pretty much where you are.  I am a KDE person but I've switched to gnome because of this on my desktop.  I'll switch right back to KDE once I figure out what is wrong.  I do want to solve this though.  Maybe we can meet like I said in the PM to work on this and post it on the board later for others.  

I just want to show this off to all the linux haters I know who cry that linux is ugly. hahahaha

---

### Post by elbryan on 2006-06-12
lol .. it works but .. now I will try with gnome ..

---


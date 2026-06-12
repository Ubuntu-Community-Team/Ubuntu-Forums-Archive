---
title: "Gnome installed itself with Banshee????"
date: 2008-05-20
forum: Desktop Environments
---

### Post by fINTiP on 2008-05-20
***SHORT VERSION BELOW***

I run a very, very slim system on my laptop.

I used the mini install CD, and I intentionally did not install a graphical login manager ("display manager"); I login in the terminal in tty1, and start fluxbox with 'startx'.

I was trying to short term install a program to rip some songs off of a friend's ipod shuffle, so I did

```

sudo aptitude install gtkpod
```

Used gtkpod, but it wouldn't find it, was having problems.

So I did 

```

sudo aptitude remove gtkpod
```

Which should have completely removed everything installed with gtkpod, as well as gtkpod itself,

and then decided to try Banshee.

```

sudo aptitude install banshee

```

It wanted to install 400+ packages with it, but I figured, "it's fine, I'm using aptitude, so when I uninstall, all will be wiped again". I thought it was a bit excessive, but I just figured it was a heavy program.

I couldn't get banshee to work either (appeared to be a dbus problem...), so I did

```

sudo aptitude remove banshee
```

And expected all to be right... but I did notice that I still had about 600+ extra megabytes of data on my system that wasn't there before.

I was in a bit of a rush though, so I turned comp off and decided to come back later.

I came back, turned it on, logged in, ran startx...

...and a jacked up version of GNOME starts up, only, no frames around windows, and no terminal accesible from the menu system.

Mind you, I can't access my tty's, which is another problem, so I have no terminal once I use startx.

WHAT the HELL. 

?!?!?!!?!?

Please help?

----------------------

1. Why did Banshee install gnome with it?
2. Why didn't aptitude remove gnome with banshee?
3. How do I correct this? Is there a way to uninstall everything installed within a certain time frame?
4. ?!?!?!?!

thanks.

.L

---

### Post by peitschie on 2008-05-20
1. Banshee would have installed some gnome libraries (quite a lot actually) which may be enough to cause your linux to try and boot Gnome (but this is an issue regardless)
2. Gnome won't be automatically removed as it isn't yet unneeded.  Once you remove banshee, there are other applications it installs (e.g., gconf2) which are not just libraries.  These will remain installed as the system cannot assume that just because the user no longer wants banshee, they don't want some of the other utilities it depended on (such as gconf).
3. To uninstall... this is a little manual, but apt records a log over time which is available in /var/log/apt/term.log (readable to root only).  To open this you need to do something like "gksu gedit /var/log/apt/term.log".  Find the log section where you installed banshee, and it should indicate what other packages were also installed that you can now remove. WARNING!!! You should make sure you have another webcapable browser nearby as uninstalling gnome *may* not force fluxbox to be used again.  You might need to follow the link listed below to restore fluxbox as the default windows manager.

I am intruiged as to why this chose to launch Gnome of fluxbox though.  If you want to force it back to fluxbox without uninstalling gnome, there are some tips here: [http://forums.debian.net/viewtopic.php?t=5382](http://forums.debian.net/viewtopic.php?t=5382)

---

### Post by fINTiP on 2008-05-22
I'm fine doing that, that's not too hands on or anything.

Do apt & Aptitude both record to the same file? I've never used apt-get on this system, always Aptitude.

.L

---

### Post by peitschie on 2008-05-22
> **fINTiP said:**
> Do apt & Aptitude both record to the same file? I've never used apt-get on this system, always Aptitude

Yes.  From my experiments, aptitude seems to update the file in the same manner as apt-get. The differences between aptitude and apt-get are rather minimal in terms of functionality.

---

### Post by joninkrakow on 2008-05-23
I don't know how aptitude works, but with apt, after I remove a package, I do a sudo apt-get autoremove, and that removes all the extra packages that were installed with it. I suppose that, if in the interim, I've installed something else that needs something that would be autoremoved, that it leaves it, so maybe everything isn't removed, but from my quick checking, it's worked every time I've tried it. I presume that aptitude has similar functionality.

-Jon

---

### Post by fINTiP on 2008-05-24
I found in the log where all of this was installed...

...but how do I easily select all of these packages to uninstall? 

--

Jon, do I type in "sudo aptitude autoremove banshee"? Others- is that viable right now/is that information correct?

.L

---

### Post by joninkrakow on 2008-05-24
I can't find any function for aptitude that works like autoremove in apt-get. I would try using apt-get and see what happens. Just type:
```

sudo apt-get autoremove

```

And see what it does.

Otherwise, if you know what packages you have installed with Banshee, just do an aptitude remove [packagename] and do them one-by-one.

I just discovered something by accident, though. Aptitude has an interactive interface. Try just typing "aptitude" on the command line, and you'll see what I mean. Maybe that will help you?

-Jon

---

### Post by peitschie on 2008-05-24
Its worth giving autoremove a shot.  I suspect in this case it won't clean up the packages properly however...


If autoremove doesn't clean it properly, try the following:

You can do something like the following to remove 3 (or more) packages simultaneously:
```
sudo apt-get remove pckg1 pckg2 pckg3
```

So in theory you can just copy & paste the package list from the apt log file directly to the end of the command :)
Once you have removed the ones it auto-installs manually, then run the autoremove function:
```
sudo apt-get autoremove
```

---

### Post by peitschie on 2008-05-24
*removed dupe*

---


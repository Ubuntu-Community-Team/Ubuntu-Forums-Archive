---
title: "Getting *to* the desktop"
date: 2006-07-04
forum: Desktop Environments
---

### Post by cr0ss on 2006-07-04
Ok, I installed Ubuntu.  I was able to login, etc.  But now I'm at the stinking command line, not knowing what to do.  How the heck am I to get into the GUI desktop environment of Ubuntu?

This "wrecked" my experience, as I had to go and install windows again, just so I could post this!  Command please?

*can't get past those command line interfaces!"
Thought this was supposed to be easy to use...

---

### Post by scxtt on 2006-07-04
if you don't have the liveCD (which you could have used to make this post, unless you have issues connecting to the web) and you installed a version w/o a GUI (namely the server version) then you'da been out of luck ...

otherwise you can type **startx** at the "command line" to start up X -- assuming your videocard is properly configured, which may have been the issue to begin with - what is it? ...

---

### Post by JoshHendo on 2006-07-04
What version of Windows are you running?
How much RAM do you have?
Did the live CD work?
Also, what is your graphics card?

---

### Post by cr0ss on 2006-07-04
I did use the LiveCD to begin with, but it froze when I tried installing it (lack of memory)  And while using it - was slow.

I burned a server CD a couple days later, and installed fine.
Both CD's had no error from writing, so that's not a problem.

RAM was a problem with the LiveCD install.  Graphics are shared (unfortunately) but do work.  The ServerCD, again, had no problems.

 
What version of Windows are you running?  XP.  THough I tried installing pure Linux.  (because I hate Win)
How much RAM do you have?  Approx. 256MB, I'm planning on getting 1024M
Did the live CD work?  Yes, as above did have issues.
Also, what is your graphics card?  Shared memory, but that's not the issue.  It's the RAM, and I know it.  Though I could invest in a graphics card...

I'm not having problems running other hardware-intensive distros (aLinux worked)... so I think it's just some minor things that need to be done.  I'll run the server CD again with that command given and see how it turns out.

---

### Post by scxtt on 2006-07-04
**startx** isn't gonna do anything for you if you installed the server version (the point of the server CD is to save the space that a gui uses) ... you can install it via **apt-get install ubuntu-desktop** (i think) ... but you'll have other issues i'm sure ...

---

### Post by taurus on 2006-07-04
If you install a server version, it will boot into a console because that's what it does!!!  Don't expect to have any window manager running until you install one like
```

sudo apt-get install ubuntu-desktop <-- for Gnome
sudo apt-get install kubuntu-desktop <-- for KDE
sudo apt-get install xubuntu-desktop <-- for XFce4

```
Since you said that you don't have enough RAM, I recommand you use XFce4 window manager instead...

---

### Post by joelito on 2006-07-04
I'm running Ubuntu with gnome on 256Mb of ram and Intel integrated graphics, so I don't think memory is your problem, your problem is either a non supported chipset or not having the graphical system as suggested above

Oh and BTW:

If you want to have a non-live CD that install with a desktop in the end, you should get the alternate cd

---


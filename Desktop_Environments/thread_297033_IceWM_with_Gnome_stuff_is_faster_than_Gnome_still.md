---
title: "IceWM with Gnome stuff is faster than Gnome still?"
date: 2006-11-10
forum: Desktop Environments
---

### Post by aysiu on 2006-11-10
As some of you may know, I've recently fallen in love with IceWM. I'll still dabble in Gnome and KDE sometimes. Occasionally, on rare occasions, I'll even try out XFCE again.

But mainly IceWM is my gig.

I have a question, though, for your savvy folk out there: 

I run my IceWM with some pretty heavy stuff. In my *~/.icewm/startup* file, I ask to start *gnome-settings-daemon*, *gnome-volume-manager*, and *klipper*. I also have the OpenOffice quickstarter icon in my system tray. I use Thunar, Thunderbird, OpenOffice, Rhythmbox, and Firefox--some pretty heavy applications (with the exception of Thunar; though even that is still heavier than Rox).

**Why is my IceWM still so damn fast?**

I'm running a ton of services and heavy applications. What slows Gnome down? Metacity? Nautilus managing the desktop? The Gnome panel and applets? Are those the things that make Gnome slower than IceWM + a ton of services? Or are there other things, too?

**I'm just curious.**

---

### Post by an.echte.trilingue on 2006-11-10
Well, I am not sure I quite fit the definition of savvy, but I recently replaced metacity with openbox as a WM, and that made a huge difference.  Everything else is Gnome, including nautilus and the gnome-panel, so I think the slowdown is metacity.

It takes CPU power to draw ugly black lines all over the screen.

---

### Post by aysiu on 2006-11-10
Thanks for the input. I figured it might have been Metacity.

Can anyone else confirm this?

Stormy Eyes has [a pretty detailed tutorial on using OpenBox instead of Metacity in Gnome](http://ubuntuforums.org/showthread.php?t=75471), but I've been too lazy to try it. IceWM seems to work just fine for me.

---

### Post by an.echte.trilingue on 2006-11-10
> **aysiu said:**
> Thanks for the input. I figured it might have been Metacity.

Can anyone else confirm this?

Stormy Eyes has [a pretty detailed tutorial on using OpenBox instead of Metacity in Gnome](http://ubuntuforums.org/showthread.php?t=75471), but I've been too lazy to try it. IceWM seems to work just fine for me.

Something else you can try for a quick demonstration of just how much metacity slows down gnome:

The next time you are logged into plain old gnome, try this:

```
sudo apt-get install sawfish-gnome ; killall metacity ; sawfish 
```

It does not integrate perfectly like that, but it is good for a demonstration.

---

### Post by aysiu on 2006-11-10
Thanks. I may just give that a try, for kicks.

---

### Post by aysiu on 2006-11-11
I'm not a big fan of Sawfish or Openbox, but I did try replacing Metacity with IceWM, and it's *much* snappier. I think I might be using Gnome with IceWM for a while...

---

### Post by BLTicklemonster on 2006-11-17
aysiu, I saw you mention icewm a while ago, and have been trying it out, and I have to admit, it's quick as heck. I'm still learning my way around, and only this morning found that if I go to kde and click computer, (in icewm-gnome) I can get my desktop with icons back. Now how can I alter the behaviour of icewm, and how can I get stuff on my taskbar so I can launch stuff? Right now icewm behaves like an old mac desktop, which is totally messing with me, because I do not like mac at all.

Is there somewhere where one might go to learn more about using icewm?

---

### Post by aysiu on 2006-11-17
All of IceWM's files live in ~/.icewm and are simple text files you can manipulate.

For some tips, check out [this thread](http://ubuntuforums.org/showthread.php?t=263710&highlight=icewm+dig).

---

### Post by BLTicklemonster on 2006-11-17
Thank you!

---

### Post by BLTicklemonster on 2006-11-17
oops, ignore me

---

### Post by BLTicklemonster on 2006-11-17
Now that I'm home and looking, nice link. So I have to open stuff and edit things. What about if I have no idea what I want to put where? Is there some interface available for those of us who are multiple brain cell challenged?

---

### Post by aysiu on 2006-11-17
There's *iceconf*, but I find that GUI tool more confusing than the text files, honestly.

---

### Post by BLTicklemonster on 2006-11-17
It's okay, I've played around with themes, and have things navigable now. I like the liquid one pretty much. This is really quick!

---

### Post by BLTicklemonster on 2006-11-18
> **FRUSTRATEDMONSTER said:**
> **At present, I'm back to gnome until I can get time to sit down and read and read and read all the typing stuff I'll have to do to get icewm to some semblance of normality for me. I just get tired of "having" to type anything to get something done, though admittedly, icewm with its speed and all should be well worth it.**

:(

---

### Post by aysiu on 2006-11-18
I wrote [a script](http://ubuntuforums.org/showpost.php?p=1549508&postcount=58) that configures IceWM to be friendly to the ex-Gnome Ubuntu user. Try it out.

---

### Post by BLTicklemonster on 2006-11-18
Yes, I'd found that and used it before posting, and it works great, but using stuff I copied and pasted to a text file and saved in /home, I attempted to do mundane things such as get my wallpaper changed, etc. While I still see a black desktop, no icons, I did see some of the changes I made to preferences take effect. One really wild thing I did, when I log out, I get a white page with no option to change sessions, only a log in! lmao@meh, I'll have to go look over what I did and change it. 

Anyway, I'll mess around and see what all I can do to get it more moron friendly, and thanks for the script. It worked great as far as I can tell.

---


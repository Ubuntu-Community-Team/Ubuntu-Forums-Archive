---
title: "Fluxbox reverts to GNOME"
date: 2009-04-04
forum: Desktop Environments
---

### Post by teeshep on 2009-04-04
Hey, I just installed Fluxbox, and it seems to work great.
However, I opened Nautilus, and it partially reverted to GNOME... The toolbar at the bottom is still Flux, and the window decoration is still flux, but the wallpaper, desktop icons, and right click menu are all GNOME. What have I done wrong? Thanks in advance!
-Teeshep

---

### Post by fabricator4 on 2009-04-04
> **teeshep said:**
> Hey, I just installed Fluxbox, and it seems to work great.
However, I opened Nautilus, and it partially reverted to GNOME... The toolbar at the bottom is still Flux, and the window decoration is still flux, but the wallpaper, desktop icons, and right click menu are all GNOME. What have I done wrong? Thanks in advance!
-Teeshep


Nothing, I think.  I found the same thing when I tried fluxbox on an old 1Ghz celeron.  If the application needs more functionally than fluxbox provides, I think it loads up Gnome, or at least the bits of it that it needs.

If you open the GIMP you'll probably find that you'll also get just about _all_ of Gnome.  I don't think the GIMP (and others) can actually work in an all-fluxbox environment.  I'm guessing that if you want a minimal GUI it's expected you'll be using minimal apps also, since it defeats the purpose otherwise.

Chris.

---

### Post by teeshep on 2009-04-04
fabricator4: Thanks, that makes sense to me. So is there a list of applications somewhere that will not revert to Gnome? I don't want to ask for each individual application, cause that gets annoying :D
But what can I replace Nautilus with, and is it pre-installed?

---

### Post by fabricator4 on 2009-04-04
For file managers I've seen Gentoo, Thunar, rox-filer, and worker recommended.  I have no direct experience with any of them.  I ended my fluxbox experiment because ultimately the GIMP will be a mission critical app for me, so it didn't seem like a viable environment for what I wanted.  I like the minimalist concept but practicality took over.  The Celeron got retired and I scrounged up an AMD 1800+ that will run Gnome (and the GIMP) nicely.

I never found a list of recommended apps for fluxbox, but there _should_  be.  You could try fluxbox-wiki.org, and fluxbox.org.  If the wiki doesn't have a list of recommended apps, maybe as a fluxbox user you could recommend it, or start one.  It's just the sort of thing that new users really need.  Failing that, googling fluxbox and the type of app you're looking for should produce a few possibilities.


Chris.

---

### Post by teeshep on 2009-04-04
Thanks again, fabricator4. I got Thunar, and it seems to work. I don't really like it, but it works. But, now so does Nautilus (without reloading Gnome...)
And, so does GIMP. Go figure... I haven't changed anything, so I have no idea why it would work now... Hmm...
But okay, I'll look for a list, thanks!
-Teeshep

---

### Post by fabricator4 on 2009-04-04
> **teeshep said:**
> Thanks again, fabricator4. I got Thunar, and it seems to work. I don't really like it, but it works. But, now so does Nautilus (without reloading Gnome...)
And, so does GIMP. Go figure... I haven't changed anything, so I have no idea why it would work now... Hmm...
But okay, I'll look for a list, thanks!
-Teeshep

Now that's interesting.  I have no idea why Nautilus should now be working without loading the Gnome desktop.  Maybe I gave up on Fluxbox too quickly.  It seems like there was something in the config that wasn't quite complete until you loaded Thunar.

Chris.

---

### Post by teeshep on 2009-04-04
Ah it's back to switching to Gnome (partially)
So I haven't fixed it! Oh well, I'll try to get used to Thunar.
-Teeshep

---

### Post by rick71 on 2009-04-05
> **teeshep said:**
> Ah it's back to switching to Gnome (partially)
So I haven't fixed it! Oh well, I'll try to get used to Thunar.
-Teeshep

Did you turn off Nautilus' desktop drawing in gconf?

---

### Post by fabricator4 on 2009-04-05
> **rick71 said:**
> Did you turn off Nautilus' desktop drawing in gconf?

I presume you mean gconftool?  I've had a look and it's not obvious how to configure this.  Can you be more specific?

I think the point is, that we both chose to try fluxbox for specific reasons.  We didn't really expect Gnome to come along with it.  It some respects it's really clever that the system will load the bits of Gnome that programs need, but in our cases it would have been more appropriate to get an error message, not Gnome.

Which just goes to show that you can't please everyone.  :-)

Chris

---

### Post by rick71 on 2009-04-05
> **fabricator4 said:**
> I presume you mean gconftool?  I've had a look and it's not obvious how to configure this.  Can you be more specific?
Chris

gconf-editor.. I thought I included the directions...

apps -> nautilus -> preferences -> show desktop

IIRC, if flux is used as the Gnome window manager, Nautilus is still drawing the desktop (wall paper and icons) unless that is turned off.

IIRC, if flux is used as a standalone window manager and Nautilus is started, it will still try to draw the desktop unless started with --no-desktop.

---

### Post by RedSquirrel on 2009-04-05
Run nautilus with the --no-desktop option:  ```
nautilus --no-desktop
```  That will prevent it from taking over.

---


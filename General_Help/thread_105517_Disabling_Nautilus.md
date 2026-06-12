---
title: "Disabling Nautilus"
date: 2005-12-18
forum: General Help
---

### Post by prizrak on 2005-12-18
Is there a way to disable Nautilus as the default file manager for Gnome, I have some custom shortcuts that use Gnome-commander instead but if I mount a network share and double click it still runs in Nautilus. Another thing is is it possible to make Nautilus stop trying to take over my wallpaper? I edited the session file to have the -no-desktop option and when the comp starts I get no wallpaper (which is what I wanted) but as soon as Nautilus opens even once the wallpaper comes back. I'd also like to be able to put wallpapers on w/o using Nautilus but still keeping Gnome (if that's impossible it's OK)

---

### Post by John Jason Jordan on 2005-12-18
[QUOTE=prizrak]Is there a way to disable Nautilus as the default file manager for Gnome[/QUOTE]
After it ate 14 Gb of my files one day I disabled Nautilus. 

I uninstalled the pos.

Now I use Konqueror. I also have Gnome Commander, but I can't select discontinuous files (holding down Ctrl key).

---

### Post by cdhotfire on 2005-12-18
Not real sure what you where looking for but here it goes.
You could try uninstalling nautilus, go to Sessions and go to Current Session, then change Nautilus to Normal, from Restart. Then
```

$ sudo apt-get remove nautilus

```
But Im sure this will leave the folders than open with nautilus to display a no directory of /usr/bin/nautilus blah blha blah.
About mounting things, I think the mounted things are set to run under nautilus. Try making your own launchers for the mounts.
For the wallpaper without nautilus, dont think thats possible.  But you can always remove the icons. Go to Configuration Editor, then "app->nautilus->preferences" then uncheck show_desktop.

I hope this helps. :\

---

### Post by Evil Whisper on 2005-12-18
to have a wallpaper without the nautilus desktop install feh:

```

sudo apt-get install feh

```

and then look here for how to set your wallpaper under the background section: [https://wiki.ubuntu.com/Openbox?highlight=%28Openbox%29](https://wiki.ubuntu.com/Openbox?highlight=%28Openbox%29)

Hope This Helps,
- Evil Whisper

---

### Post by prizrak on 2005-12-19
Thanks, I don't really want to remove Nautilus since it seems to be fairly tightly integrated into GNOME. From your responses it actually seems that getting rid of Nautilus kills some of the useability, it is very convinient to be able to open a mounted drive (especiall USB) from a shortcut on the desktop rather than navigating to the media folder. I think I'm going stick with the default setup for now. Maybe if I ever bite the bullet and actually go the *box route I'll be able to tweak it all to what I want it :)
Jason Jason Jordan, you should try getting the newest version of GNOME Commander from [here]("http://rpmfind.net/linux/rpm2html/search.php?query=gnome-commander&submit=Search+...") and install it with alien (which is what I used) I do get discontinues file selection in it.> go to Sessions and go to Current Session, then change Nautilus to Normal, from Restart
Reading is fundamental :) Just read your post the second time and checked that out, this is EXACTLY what I'm looking for. I don't want it to restart if I turned it off. Thanks 
Evil Whisper, in light of the above discovery I shall try the feh route at some point. My main issue was that if I had the animated wallpaper running (the screensaver as background) starting Nautilus would paint it's own background over it. Now that I have a way of guarding against that I'm only gonna do the wallpaper sans Nautilus on the lappy :) Thanks for the tip :)

---

### Post by egon spengler on 2005-12-19
to stop nautilus drawing the desktop

```
gconf-editor
```

apps>nautilus>preferences untick "show_desktop"

in breezy you also need to go to desktop>gnome>background and untick "draw_background"

---

### Post by cdhotfire on 2005-12-19
I tried, what I posted above, in the Configuration Editor. If you uncheck the show_desktop, it will disable nautilus, and leave the wallpaper as is. So go to "Applications->System Tools->Configuration Editor" then go to "apps->nautilus->preferences" then uncheck show_desktop, as instructed in my last post.  This will disable the menus and icons, as well as take off nautilus from the sessions menu.  Try it out, by taking it off session manager theres no need to change it to Normal, but do it anyways, so if it starts up when clicking on a mount or w/e, it will shutdown and not restart after it is closed down. :)

---

### Post by John Jason Jordan on 2005-12-19
[QUOTE=prizrak]Jason Jason Jordan, you should try getting the newest version of GNOME Commander from [here]("http://rpmfind.net/linux/rpm2html/search.php?query=gnome-commander&submit=Search+...") and install it with alien (which is what I used) I do get discontinues file selection in it.[/QUOTE]
Thanks for the URL. I have 1.01 now, installed with Synaptic. But that site lists a lot of different files. I have 64-bit Breezy on AMD-64. There are several that say they are x86-64, but which one do I use? And why are there no .deb files? And if there are no .deb files, how do I use Alien? I remember using Alien once, but it didn't work and left me with a lot of trash in the folder -- it's all I can do to figure out how to untar something. Color me with serious n00bitude.

I do kind of like Gnome Commander, although I now finally have Konqueror configured and it is OK. But Konqueror takes forever to load and Gnome Commander comes up very fast. That is important because I use Ubuntu on my laptop which is always being shut down and restarted.

---

### Post by dninja on 2008-07-01
> **cdhotfire said:**
> Go to Configuration Editor, then "app->nautilus->preferences" then uncheck show_desktop.

I hope this helps. :\

Can anyone tell me what file this changes. I don't have gnome installed and don't have gconf-editor so will have to make this change by hand.

---


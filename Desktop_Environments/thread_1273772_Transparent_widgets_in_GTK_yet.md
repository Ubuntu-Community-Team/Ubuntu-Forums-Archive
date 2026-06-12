---
title: "Transparent widgets in GTK yet?"
date: 2009-09-23
forum: Desktop Environments
---

### Post by mazz0 on 2009-09-23
So a search on the subject of transparent widgets in GTK brings up lots of results dating back to 2006/7 and talking about how "GTK already supports this" and "the next release of Murrine will include it".  So where is it?

Anyone know what's going on with this?  I just want to have my tool-bars and menus and what not to be see-through and match my window border, so it could look like my whole application is made of glass or whatever transparent material, with buttons and pages and stuff on top or carved in it.

Is it available now somehow?  Will it be in Gnome 3, do you know?  I haven't seen it in any of the screen-casts (all I've seen is weird and, as far as I can see, pointless, changes to the way you launch and switch between applications).

I think the lack of this feature makes Gnome look kind of old-fashioned, even with a beautiful theme and fancy Compiz effects.  It's the one aspect where I lose in my shallow "my desktop's prettier than yours" debate with Windows Vista / 7 users.

---

### Post by blackened on 2009-09-23
You've just been looking in the wrong places. The Murrine engine does support rgba transparency on a per-application basis. There is a list of compatible applications [here]("http://www.cimitan.com/murrine/rgba-support/list"). Some will work after you get rgba going, others you will need to install a plugin.

The main problem that you're likely running into is that, AFAIK, there are no themes with rgba enabled by default. So you'll have to find a theme, then edit the gtkrc appropriately (hint: change RGBA = FALSE to RGBA = TRUE). A good example would be [Pucko Modern]("http://lassekongo83.deviantart.com/art/Pucko-Modern-101791479").

For an extra (g)classy look, enable Alpha Blur in CCSM for the transparent applications for some nice occlusion effects. Sucks that the translucency is not adjustable though.

---

### Post by mazz0 on 2009-09-24
Ah ha!  Thanks for that - I'll look into it!  Oooh, and that theme's pretty!!  I'm downloading it right now!

I'm kind of hoping for something more complete though, something that doesn't require any hacking to make it work.  And to be honest, if it doesn't work in Nautilus, Firefox (I know it's not GTK so would require a Firefox plugin such as the one for Windows Vista/7), GIMP and Evolution it's going to be pretty much useless to me :(

No news on this becoming a standard part of the gnome desktop then?

---

### Post by blackened on 2009-09-25
> **mazz0 said:**
> ...something that doesn't require any hacking to make it work.

Hehe, you must've taken a blow to the head and forgotten what forum you were on. :)

> ...And to be honest, if it doesn't work in Nautilus, Firefox (I know it's not GTK so would require a Firefox plugin such as the one for Windows Vista/7), GIMP and Evolution it's going to be pretty much useless to me :(

Sorry about that, I can't point you to stuff that doesn't exist yet, and unfortunately what you want doesn't. The only applications that have been patched or have plugins are on Cimi's list.

> No news on this becoming a standard part of the gnome desktop then?

I very seriously doubt that'll ever happen.

---

### Post by mazz0 on 2009-09-25
Oh well :(

At least there are some flipping beautiful themes! :)

---

### Post by mazz0 on 2009-09-25
Oh, speaking of pretty themes - how do I install that pretty [Pucko Modern]("http://lassekongo83.deviantart.com/art/Pucko-Modern-101791479") theme?  I'm not a total noob (honest!) - I've installed themes before, but usually just by dragging the archive into my Appearance Preferences, but I can't do that with this.

Honestly, I'm not a noob, really! :(

---

### Post by blackened on 2009-09-26
Pucko Modern is really a group of recolorations of one main theme. If you'll extract the archive that you downloaded, then you'll see that it contains individual folders for Pucko Modern Blue, Pucko Modern Brown, Pucko Modern Green, and Pucko Modern Pink.

To install each one individually, just drop its folder into ~/.themes (or /usr/share/themes for global installation).

---

### Post by 3rdalbum on 2009-12-13
Sorry to bump an old thread, but somebody told me today that Darkroom supports RGBA. They are right. And with a single line edit in the gtkrc, you can make any Murrine theme (for instance, my favourite Dust) support RGBA too.

It still depends on the program being updated or patched for this. Gedit, Rhythmbox and Eye Of Gnome can have plugins added to them to enable RGBA. Gnome-Terminal and Gnome-System-Monitor have RGBA already. Many other programs can be patched (at source code level) to get this working.

---

### Post by blackened on 2009-12-13
Funny you should revive this thread. I read somewhere that they were working on system-wide RGBA support for 10.04. Granted I'm not sure how true this is, but I would be happy indeed if this were the case.

**Edit:** Looks to be true, just google "rgba support 10.04" for tons of write-ups.

---

### Post by mazz0 on 2009-12-14
Oooh, I /really/ hope that thing about it being included in 10.04 is true, the screenshot on [http://www.ghacks.net/2009/12/11/what-will-ubuntu-10-04-bring-to-the-table/](http://www.ghacks.net/2009/12/11/what-will-ubuntu-10-04-bring-to-the-table/) looks gorgeous!

You got a link to some instructions on doing what your described 3rdalbum?  To be honest without Nautilus, Eclipse and Firefox/Chrome support it won't be very handy to me, but I do use Gedit a lot, so that'll be nice!

Speaking of eye-candy - anyone used a recent version of AWN?  It's lovely!

---


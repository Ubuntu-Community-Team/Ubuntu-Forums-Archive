---
title: "Windows Aero-like effect in 10.04 Lucid Lynx"
date: 2010-04-30
forum: Desktop Environments
---

### Post by Karl1982 on 2010-04-30
According to every source Google could throw at me, transparency going beyond just window borders was supposed to be on by default in Lucid (most called it rgba I think).  I upgraded from 9.10 to 10.04 LTS today, and it looks *exactly* the same (it broke several things in fact, my graphics and wireless drivers among them).  Anyway, current situation is I've gotten my drivers sorted out.  Desktop effects are fully enabled (set to extra).  I don't see any new appearance options.  My window control buttons were on the left instead of the right, but I was able to correct that by just reapplying a theme.  I looked through several themes, and the level of transparency doesn't seem to vary between them.

What do I need to do to enable the menu and window transparency I've heard so much about?  I've seen a YouTube video of it working.

EDIT: Forgot to mention, I have all apt updates installed.

---

### Post by kvarley on 2010-04-30
Install the compiz fusion manager via the Ubuntu Software Centre.

---

### Post by Karl1982 on 2010-04-30
I have CompizConfig Settings Manager installed already.  I don't see a Compiz Fusion Manager in the software center.

---

### Post by kvarley on 2010-04-30
You can do it via the compiz settings manager - It will be in System>Preferences

---

### Post by xxeper on 2010-04-30
I don't see any options like that in Compiz.

Any more info?

---

### Post by Karl1982 on 2010-04-30
I also don't see any such settings in Compiz.

I did find this, but I tried it and it doesn't work: [https://wiki.ubuntu.com/DesktopTeam/RgbaGtkWithPPA](https://wiki.ubuntu.com/DesktopTeam/RgbaGtkWithPPA)
In step 3, the Gnome Color Chooser never appears in the menu.

I've come across a couple reports that the new transparency effects have been postponed until something called Lucid+1 (does that mean Ubuntu 10.10?).  I have been unable to verify this.  Seems to me like this forum and the rest of the internet would be on fire with discussions or announcements about it if that were true.

---

### Post by Karl1982 on 2010-05-02
Is anyone able to confirm or deny this?

---

### Post by CrimsonBizarre on 2010-05-02
> **Karl1982 said:**
> I also don't see any such settings in Compiz.

I did find this, but I tried it and it doesn't work: [https://wiki.ubuntu.com/DesktopTeam/RgbaGtkWithPPA](https://wiki.ubuntu.com/DesktopTeam/RgbaGtkWithPPA)
In step 3, the Gnome Color Chooser never appears in the menu.

I've come across a couple reports that the new transparency effects have been postponed until something called Lucid+1 (does that mean Ubuntu 10.10?).  I have been unable to verify this.  Seems to me like this forum and the rest of the internet would be on fire with discussions or announcements about it if that were true.

Yeah, postponed until gtk+. 

To get gnome colour chooser:

sudo apt-get install gnome-color-chooser

---

### Post by techunit on 2010-05-02
I thought it would be cool for about 5 minutes before I decided the less Ubuntu is like windows the better. I would welcome it if it became part of it, but really I don't care. I like the new default theme in Lucid...

---

### Post by infamous-online on 2010-05-02
> **techunit said:**
> I thought it would be cool for about 5 minutes before I decided the less Ubuntu is like windows the better. I would welcome it if it became part of it, but really I don't care. I like the new default theme in Lucid...

Not everybody shares your view, so no need to criticize anyone who wants their desktop to look a certain way.

---

### Post by Karl1982 on 2010-05-03
> **techunit said:**
> I thought it would be cool for about 5 minutes before I decided the less Ubuntu is like windows the better. I would welcome it if it became part of it, but really I don't care. I like the new default theme in Lucid...

Windows 7 has a beautiful desktop environment.  Say what you want about Microsoft, but they can make a good-looking OS.  Even the default fruit basket theme of Windows XP doesn't look bad.  It would be a very good thing for Ubuntu if it could look as good as Windows 7.

I'm not sure I like the screenshots I've seen of the RGBA though.  They had the buttons and other controls in the windows translucent.  I think for the best visual effect, text areas and all window controls should be opaque with the rest of the window translucent.

---

### Post by CrimsonBizarre on 2010-05-03
> **Karl1982 said:**
> Windows 7 has a beautiful desktop environment.  Say what you want about Microsoft, but they can make a good-looking OS.  Even the default fruit basket theme of Windows XP doesn't look bad.  It would be a very good thing for Ubuntu if it could look as good as Windows 7.

I'm not sure I like the screenshots I've seen of the RGBA though.  They had the buttons and other controls in the windows translucent.  **I think for the best visual effect, text areas and all window controls should be opaque with the rest of the window translucent.**

It does look like that:
[*Large Image*]("http://www.cimitan.com/blog/wp-content/murrine_rgba-2.jpg")

I think both operating systems look good in different ways. Windows 7 aero is great-looking but offers no customization, while ubuntu offers a heck of a lot of customization and looks good out-of-the box without being too flashy.

---

### Post by Karl1982 on 2010-05-04
Well, you're half right -- look closely at the top window in that picture.  Half of the controls are opaque, and half of them aren't.  And in the bottom window, the entire window is opaque except for the title bar (and I think the borders, but it's hard to see).  All the space between the controls/lists/etc is 100% opaque.  That inconsistency just catches my eye every time I see it.  But maybe they'll fix that before they make it official.

I'm glad to see they're working on that, though.  Maybe I can finally have glassy taskbars too.  I know the feature is already there for transparency, but I just can't use it if it makes all the buttons and controls transparent too.  I tend to gravitate toward light window themes and dark backgrounds, and that makes it difficult to see.  Windows 7 does an excellent job with taskbar and start menu transparency (some of the controls themselves are transparent, but not the text/icons on them), but on windows, they only do title and borders.

I did get it working to some extent on my laptop, but I ended up disabling it because the only window I could really find that turned transparent was the terminal, and it drove me nuts in short order. :(

---

### Post by vaiocomputer on 2010-05-05
If you want, there is actually a windows aero-like effect in Compiz.  I was ridiculously slow on my laptop, so I don't use it, but if you have the proprietary drivers installed, it might work.

If you use I think 'Blur Windows' and you set it up right and while using an Emerald theme with transparency, it will 'blur' instead of being see through.

---

### Post by 3rdalbum on 2010-05-06
It can be done on Lucid and Karmic by adding a PPA and using "gnome-color-chooser" to render widgets using Murrine; but some programs don't work with RGBA and you end off having an RGBA blacklist as long as your arm (Pitivi, Firefox, Openoffice.org, all video players, anything that runs Ubuntu One Music Store, anything that uses XUL, and probably lots of programs I've never tried).

And sometimes when you install a program that simply doesn't work, you spend ages adding it to the blacklist and finding all possible program components for it to add to the blacklist, and then at the end of it all the program STILL doesn't work... and you still don't know whether it's due to RGBA or just that the program is buggy.

Yeah, it looks nice and I hope everything gets sorted for Maverick, but if you're not confident with your Linux skills or you depend on everything working, then you shouldn't try it.

---

### Post by CrimsonBizarre on 2010-05-08
> **Karl1982 said:**
> Well, you're half right -- look closely at the top window in that picture.  Half of the controls are opaque, and half of them aren't.  And in the bottom window, the entire window is opaque except for the title bar (and I think the borders, but it's hard to see).  All the space between the controls/lists/etc is 100% opaque.  That inconsistency just catches my eye every time I see it.  But maybe they'll fix that before they make it official.

Oh, I thought it was showing a before/after thing, or one windows with RGBA enabled, one with it disabled.

> **Karl1982 said:**
> I'm glad to see they're working on that, though.  Maybe I can finally have glassy taskbars too.  I know the feature is already there for transparency, but I just can't use it if it makes all the buttons and controls transparent too.  I tend to gravitate toward light window themes and dark backgrounds, and that makes it difficult to see.  Windows 7 does an excellent job with taskbar and start menu transparency (some of the controls themselves are transparent, but not the text/icons on them), but on windows, they only do title and borders.
Depening on the GTK theme you have, you can make the taskbar transparent by giving it a transparent background image.

> **Karl1982 said:**
> I did get it working to some extent on my laptop, but I ended up disabling it because the only window I could really find that turned transparent was the terminal, and it drove me nuts in short order. :(
I think you have to enable RGBA from within the program (ie. it has to support it),

---


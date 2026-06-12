---
title: "A few Fluxbox questions..."
date: 2008-01-19
forum: Desktop Environments
---

### Post by eapache on 2008-01-19
I have an old but decent P3 computer that will run Xubuntu fine, however I'm a bit of a performance freak, so I recently switched to fluxbox. It's mostly working fine, but I have a few questions:

1. Fluxbox doesn't need GDM, so theoretically I can disable it, however it handles autologin, which I use. Is there a way to disable gdm and still have it automatically login and start fluxbox on boot?

2. I'm having a peculiar issue that whenever I start totem or rhythmbox, a gnome process is started that replaces my desktop background with the default Ubuntu one, as well as theming my windows. I think it has something to do with gstreamer starting gdm which is taking over fluxbox, but it's pretty bizarre. Is there any way to disable this, or are there any media players that won't do this?

3. I currently use f-spot. Are there any lighter photo managers (gthumb doesn't do what I need)

4. Are there lighter office apps than OO.org? I use Google Docs for writing, but the spreadsheet and presentation components won't run in opera, which I find faster than FF. If there is a opera-fast browser  that works with google docs, that would also solve this problem.

None of these are vital (although #2 is annoying). Any help is appreciated.

---

### Post by p_quarles on 2008-01-19
1. Autologin, I don't think so. I could be wrong, but I think this would require you entering your password at some point.

2. I use Amarok with FB, and I have no problems whatsoever. I have noticed the same behavior when trying to run Nautilus, and I believe that Rhythmbox may be tightly integrated with that (i.e., instead of using an SQLite database like Amarok does). Pretty much any other media player will work without doing this: Exaile, Banshee, Sonata, etc.

3. Gwenview is great. What does gthumb not do that you need?

4. GnomeOffice or KOffice.

---

### Post by eapache on 2008-01-19
Of Exaile, Amarok, Banshee and Sonata, which is the lightest? I don't need much feature-wise, just a music browser and a search box. I don't even use playlists.

It's been a while since I last used gthumb, so I don't remember anything specific. I'll take another look at it as well as Gwenview.

---

### Post by p_quarles on 2008-01-19
Sonata, since it's actually just a front-end for the CLI music player MPD. 

Exaile is pretty light for a full-featured player.

---

### Post by glotz on 2008-01-19
3. I like GQview.

4. Perhaps Gnumeric?

---

### Post by eapache on 2008-01-19
The problem I find with gthumb and gwenview is that they're basically glorified file browsers. I much prefer F-spot allowing me to view my entire library even though they aren't all clumped in one folder.

Only amarok doesn't cause the gnome thing. All the others do.

---

### Post by eapache on 2008-01-20
I actually quite like Amarok now. I didn't know what I was missing 'till I found it :P It uses more ram because it has to load all the kde libs, but actually uses less cpu than rhythmbox. I also like the on-screen notification, however it appears behind all my currently open windows. Is there a way to get it to raise above everything else?

I just have the one fluxbox question left: autologin without GDM. Does anybody know a way to do this?

---


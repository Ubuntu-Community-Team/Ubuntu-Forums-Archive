---
title: "Nautilus &amp; gThumb don't open pictures"
date: 2005-10-16
forum: Desktop Environments
---

### Post by Madpilot on 2005-10-16
I use gThumb rather than eog to view pictures in Ubuntu, and Breezy has introduced a very irritating bug...

Currently in Breezy, if you're using Nautilus and double-click on an image, rather than opening it directly in gThumb, gThumb displays another thumbnail view, with your selected picture highlighted!

This is frankly stupid, as Nautilus shows thumbnails anyway. If I click on something, I want to actually see it, not see another thumbnail of it!

EOG actually opens the real image, but it's otherwise so feature-lacking compared to gThumb that I don't want to switch back to using it!

Where is the option hiding to turn this irritating behaviour off?

---

### Post by Madpilot on 2005-10-17
bump... nobody else has this problem, or am I just the only one who thinks it is a problem?

---

### Post by bluck on 2005-10-17
[QUOTE=Madpilot]bump... nobody else has this problem, or am I just the only one who thinks it is a problem?[/QUOTE]

yes, experiencing the same thing. 

im trying to discover the command line option to make gthumb go straight to "image" view mode.

the closest i got is:

gthumb --slideshow %s

but of course that will revert back to the browser mode after 4sec (or whatever your slideshow interval is).

ill let ya know if i find it.

---

### Post by Madpilot on 2005-10-17
I just searched bugzilla.ubuntu.com, and this irritant has been noted and is corrected upstream - but Breezy shipped with an old version of gThumb...

[http://bugzilla.ubuntu.com/show_bug.cgi?id=15963](http://bugzilla.ubuntu.com/show_bug.cgi?id=15963)

... so we're going to have to swear at it for the next five months or so until Dapper gets released...

This isn't the only app where I've noticed Breezy shipping with a buggy, out of date version; Screem wasn't updated at all between Hoary and Breezy, and the Ubuntu version of Screem is now considerably behind the current release...

---

### Post by David A Knight on 2005-10-18
[QUOTE=Madpilot]
This isn't the only app where I've noticed Breezy shipping with a buggy, out of date version; Screem wasn't updated at all between Hoary and Breezy, and the Ubuntu version of Screem is now considerably behind the current release...[/QUOTE]

screem got caught up in the debian freeze for sarge.  the debian package required updating but couldn't be done due to a dependancy on gnome 2.10.  as ubuntu packages come from sid breezy was also effected.  the time in between sid coming out of freeze and breezy going into freeze was rather short so it probably just missed out because of that.

---


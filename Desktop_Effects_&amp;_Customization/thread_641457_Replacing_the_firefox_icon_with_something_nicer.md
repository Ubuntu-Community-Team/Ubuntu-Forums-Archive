---
title: "Replacing the firefox icon with something nicer"
date: 2007-12-15
forum: Desktop Effects &amp; Customization
---

### Post by isecore on 2007-12-15
This might be a hopeless wish, but I would like to replace the default icon with something nicer. I do love the Firefox-icon, but I'm annoyed by how pixelated it appears in various higher-resolution circumstances - most visibly through the Application Switcher in Compiz Fusion. See the attached screenshot for an example of what I mean.

Most of all I'd like to replace it with an SVG-image (which I found on Wikimedia) but I haven't figured out quite how to achieve this yet. Surely there's some more intelligent person than me who knows how to do this? I found an[ old (probably deprecated) script]("http://ubuntuforums.org/showthread.php?t=34354") from 2005 to replace the generic blue globe with the proper icon, but I doubt it applies to my situation.

I've googled the web as well as searched this forum to no avail. Any good tips? I would preferably like to do the same with the Thunderbird-icon, which is equally ugly.

Or is this even feasible? Should I just wait until Hardy Heron which will supposedly be SVG-only?

---

### Post by Brindled on 2007-12-15
have you tried right-clicking on the icon and then clicking *Change Icon*, or clicking properties of the shortcut and clicking the icon in the top-left corner?

---

### Post by isecore on 2007-12-15
Yup, of course I tried that first of all. It only changes the icon for the shortcut/launcher, not the actual application icon.

It would seem that the application icon is /usr/share/pixmaps/mozilla-firefox.png, but it's replacing that one with an SVG which seems to be the real trick.

---

### Post by Brindled on 2007-12-15
maybe try converting an svg into a png with gimp?

i just successfully changed a random svg into a png file. maybe replace the default with the one of your choice that is named the default name?

edit: oh yeah, backup your original************

---

### Post by isecore on 2007-12-15
> **Brindled said:**
> maybe try converting an svg into a png with gimp?
Yes, of course that's an option. But it just seems so unelegant to use a PNG which after all is unscaleable.

But this is probably the route I'll take when I've exausted all other options.

---


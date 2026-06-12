---
title: "Where is gnome-font-viewer"
date: 2008-12-08
forum: Desktop Environments
---

### Post by dserodio on 2008-12-08
In Hardy, I could browse the installed fonts at the **fonts:///** "magic" URL, and I could view a TrueType font by double-clicking on a .ttf file in Nautilus.

In Intrepid, I can't. I researched a little and found that "gnome-font-viewer" is responsible for these features, and that Hardy's **gnome-control-center** package contained it, but I can't find it on Intrepid. Was this program removed from Ubuntu? If so, what's its replacement?

Thanks in advance,
Daniel Serodio

---

### Post by hictio on 2008-12-08
There is no Font Viewer anymore, you can use "Charmap" for that...

The "fonts:/// way" doesn't work anymore, take a look here to install fonts: [Where is the fonts folder?](http://ubuntuforums.org/showthread.php?p=6260422)

---

### Post by dserodio on 2008-12-08
Thanks for the information, but why was this harmless application removed?

---

### Post by nikgare on 2008-12-08
> In Hardy, I could browse the installed fonts at the fonts:/// "magic" URL,

No you couldn't, it was removed before Hardy.
It was handy, but my understanding was that it was a **LOT** of work to keep it working.

---

### Post by glennric on 2008-12-09
> **nikgare said:**
> No you couldn't, it was removed before Hardy.
It was handy, but my understanding was that it was a **LOT** of work to keep it working.

I don't know why you are claiming this.  gnome-font-viewer is definitely still in Hardy.  It is also my understanding that it will be back in Gnome 2.26.  There is a current issue with the linking of certain libraries that is being worked on.  It may be difficult to keep it working, but that is certainly no reason to drop it entirely.

---

### Post by glennric on 2008-12-09
I see.  You are claiming the "fonts:///" magic url is no longer in Hardy.  That is true, that was removed in Hardy (or before).  My mistake.

---

### Post by dserodio on 2008-12-09
Thank you all for the clarifications. I've been a Debian user for a long time, but I'm relatively new to the Ubuntu community.

Where does this sort of discussion take place? Or is this a "upstream" Gnome issue, discussed on the Gnome mailing lists?

---

### Post by hdfssk on 2008-12-17
desrodio: The font viewer and thumbnailer were in a directory of other stuff that was removed shortly before the 2.25 release; after some disagreement about whether they were necessary at all they were added back into the svn trunk for the next release, but haven't been backported to the gnome-2-24 branch yet. There doesn't seem to be much urgency to do so from the maintainers, and the gnome-bugsquad people told me that there's nothing outsiders can directly do at this point.. but leaving a comment on bug 555215 politely asking for it to be put back might speed things up. Here's a link to the bug:

[http://bugzilla.gnome.org/show_bug.cgi?id=555215](http://bugzilla.gnome.org/show_bug.cgi?id=555215)

---

### Post by el_itur on 2009-01-21
Anyone knows if it can be backported somehow?

---


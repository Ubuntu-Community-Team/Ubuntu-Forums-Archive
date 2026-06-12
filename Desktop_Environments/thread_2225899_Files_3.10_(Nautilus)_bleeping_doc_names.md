---
title: "Files 3.10 (Nautilus) bleeping doc names"
date: 2014-05-24
forum: Desktop Environments
---

### Post by mayagrafix on 2014-05-24
Gnome Files is a great file manager and I am happy with it except for one small detail. When I use the search function, it replaces the file name with three dots as shown in the image below. 

When I open Files 3.10 the document names show up complete but as soon as I type a search term, bam! the name colum collapses into 3 dots and wont let me expand the name field using the double arrow within the mouse pointer. I have to either:

1- Expand the window to fill the whole screen, which I dont like because most of the time I have two windows opened side by side, which is nice but after expanding them I'll have one in front of the other which is a pain to work with, or
2- Switch to icon mode which I dont like because it makes it harder for me to find things.

[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/Filesmissingnames_zpsed8fa371.png[/IMG]
Is there any hope there will be a fix for this sometime this century?

---

### Post by deadflowr on 2014-05-24
Expand the Name field.
Whoops, missed that part.

Seems weird that you can't?
Is there something in edit > preferences you can set?

---

### Post by vanadium on 2014-05-24
I have noticed this also. This works badly. If the issue is reported, then I guess it will be fixed sooner or later.

---

### Post by mayagrafix on 2014-05-24
'Kay, so I'm not the only one. So I'll file a bug report now and see what happens :>)

---

### Post by pfeiffep on 2014-05-24
I am unable to duplicate these symptoms:
[INDENT]Files ... 3.10.1
Ubuntu 14.04 LTS (32 bit)
3.13.0-24-generic #47-Ubuntu[/INDENT]

---

### Post by vanadium on 2014-05-24
> **pfeiffep said:**
> I am unable to duplicate these symptoms:

1) Switch to list view <Ctrl+1>
2) Start a search, e.g. for odt files. <Ctrl+f>odt
All Libreoffice writer files appear. As they appear, the left column may be narrowed down to the extent that the name is being replaced by "...". This is because the width of the "Location" column is adjusted (widened). When the other columns are at their minimum, you can't change their size anymore.
When you maximize the nautilus window, things get better of course, because there is more place. The location column keeps taking a whoping 60% of the withh, and its width can't be decreased to give more room to the file name, for example.

When performing another search, the widths are changed again. No way of keeping the withs of the colums like you prefer them at the moment.

Bug report here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1243806](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1243806) and for gnome: [https://bugzilla.gnome.org/show_bug.cgi?id=693459](https://bugzilla.gnome.org/show_bug.cgi?id=693459)

---

### Post by mayagrafix on 2014-05-26
Meanwhile this gets fixed, here is a workaround that works for me (your mileage may vary):
I right click in the name field and deselect the options one by one till the doc name comes back :<( I know it kinda defeats the purpose, but at least you can id which doc you are looking at. I further identify by manually pressing control - i for the properties box, which tells me where the thing is located. Only a workaround, but better than streching the windows to extra huge one end to the other end of the monitor.

---

### Post by mc4man on 2014-05-27
> **vanadium said:**
> 1) Switch to list view <Ctrl+1>
2) Start a search, e.g. for odt files. <Ctrl+f>odt
All Libreoffice writer files appear. As they appear, the left column may be narrowed down to the extent that the name is being replaced by "...". This is because the width of the "Location" column is adjusted (widened). When the other columns are at their minimum, you can't change their size anymore.
When you maximize the nautilus window, things get better of course, because there is more place. The location column keeps taking a whoping 60% of the withh, and its width can't be decreased to give more room to the file name, for example.

When performing another search, the widths are changed again. No way of keeping the withs of the colums like you prefer them at the moment.

Bug report here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1243806](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1243806) and for gnome: [https://bugzilla.gnome.org/show_bug.cgi?id=693459](https://bugzilla.gnome.org/show_bug.cgi?id=693459)

While the screen in post one doesn't indicate this bug at all certainly it is an issue when using the gnome search tool in nautilus while in list view.
Can't see the gnome/redhat devs fixing this for 3.10, at best may be for whatever current version they use.

The only real solution here was to remove 'location' from the search columns displayed in *search view* & enable it only when needed
(- listview & 'search view' have their own default set of columns displayed, search view's set can be altered after doing a search via a r. click in the column name bar.
The  OP 'appears' to also be using rather large icons for window size, maybe try a smaller size to gain a little room - 
edit > preferences > default zoom level

---

### Post by mayagrafix on 2014-05-27
Basically the problem lies in that the colum width cannot be adjusted after using the find function. Everything else about files is great, but this one glitch is a real damper on usability. For the latest version of Ubuntu, (14.04) the developers changed the find function to a totally unusable option in order to side step the problem.

---

### Post by mc4man on 2014-05-27
> **mayagrafix said:**
> Basically the problem lies in that the colum width cannot be adjusted after using the find function. Everything else about files is great, but this one glitch is a real damper on usability. For the latest version of Ubuntu, (14.04) the developers changed the find function to a totally unusable option in order to side step the problem.
Only when the "location" is maxed out, otherwise columns can be resized.

Not sure what you mean by 'find'. If it's type-ahead find (interactive search) then the columns are the same as normal & don't change from pre-search layout - scr. 1 (more like what you show in screenshot
If it's gnome's search then you get a different set of columns & they can resize to accommodate location. -  scr. 2 (the current bug
Plus maybe you are using a relatively narrow window to allow 2 side by side...

---


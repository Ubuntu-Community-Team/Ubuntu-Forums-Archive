---
title: "I need some basic help using FSpot!"
date: 2009-04-18
forum: General Help
---

### Post by gabriella on 2009-04-18
Here's my question. I imported some photos into FSpot. They are tagged with a suitable name, lets say xxxx. However, in realty when I look at them via the file browser they are stored in a whole multitude of folders/subfolders by date. 

This I find very confusing. I can see the logic of a date structure but I would like to store all of them in one single folder named xxxx regardless of date. I tried doing this via the file browser but then Fspot cant read them. Well it reads them and displays thumbnails but wont open them when I click, just the black file page symbol. 

So is there any way of storing them under a single folder xxxx without the date structure?  Or for that matter I'd consider another photomanager if need be. My one of choice is the Cannon utility that came with my camera but that only works under Windows

Thanks

---

### Post by Brucevdk on 2009-04-19
> **gabriella said:**
> So is there any way of storing them under a single folder xxxx without the date structure?

I thought I'd take a look and see if this is possible but it looks like it isn't. It seems some people have modified F-Spot to do be able to do this but it looks like these modifications have not yet been accepted by the F-Spot developers. 

The only workaround I can think up of is creating symbolic links, which is relatively easy to do with a simple command but I'd consider that a power user type thing. 

Here are the relevant bug reports:

[LIST]
[*][Bug #182858 in F-Spot: “support custom directory structures”](https://bugs.launchpad.net/f-spot/+bug/182858)
[*][Bug #195773 in f-spot (Ubuntu): “Allow custom folder structure”](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/195773)
[*][Import to directory structure (f-spot)](http://bugzilla.gnome.org/show_bug.cgi?id=329040) (this is the actual upstream bug, i.e. with the actual developers of F-Spot)
[/LIST]

Sorry!

---

### Post by Brucevdk on 2009-04-19
Actually wait a second. Looks like it might work if you choose not to copy the photos over an import (untick the box). The F-Spot photo database (~/.gnome2/f-spot/photos.db) will then contain the following:

```

sqlite> SELECT * FROM photos;
69|1146228144|file:///home/bruce/Desktop/IMG_1006.jpg||2|1|0|hCESj4qB/1SBUxHtZe8FNQ==

```

As you can see it references the original location of the photo, this is also the reason why you were previously unable to open photos after moving them even though thumbnails were still being displayed. Which I think means you can still organize your photos while keeping the directory structure you want.

---

### Post by gabriella on 2009-04-22
> **Brucevdk said:**
> Actually wait a second. Looks like it might work if you choose not to copy the photos over an import (untick the box). The F-Spot photo database (~/.gnome2/f-spot/photos.db) will then contain the following:

```

sqlite> SELECT * FROM photos;
69|1146228144|file:///home/bruce/Desktop/IMG_1006.jpg||2|1|0|hCESj4qB/1SBUxHtZe8FNQ==

```

As you can see it references the original location of the photo, this is also the reason why you were previously unable to open photos after moving them even though thumbnails were still being displayed. Which I think means you can still organize your photos while keeping the directory structure you want.

THanks for that! I'll try and figure out if that works for me. 
As I said earlier I'm not necessarilly committed to FSpot, there may be better alternatives out there? just haven't had time to check them out.

---

### Post by joepz on 2009-11-18
I tried F-Spot for 3 days, hoping I could do without a pseudo Linux version of Picasa, but turned back to Picasa in the end.
Somehow it runs much faster on my machine (picture browsing) and doesn't impose anything with respect to location, folder structure or what have you.

Cheers,
Joep

---


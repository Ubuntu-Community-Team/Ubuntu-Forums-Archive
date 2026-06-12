---
title: "Thunar Questions"
date: 2006-09-25
forum: Desktop Environments
---

### Post by ahaslam on 2006-09-25
Hi,

I primarily use GNOME but prefer Thunar to Nautilus purely for its speed in opening large folders. I would like to be able to set it as the default file browser, but I have a few questions before I do:

1. Is it possible to increase the size of picture thumbnails? They look very small in comparison to files & folders. Zooming in makes the folders too large.

2. I've noticed that the file/folder spacing is inconsistent between directories, can this be made more universal?

3. The text under files & folders is centralised until there's two or more lines of text, then it's aligned to the left. Why is this & can it be kept centralised?

4. When hovering over a file/folder, the text is under-lined in conjunction with the icons pre-light, can the under-line be removed?

I have attached some screenshots to show what I mean, they're all in the same size window & at the same zoom level:

[ATTACH]16325[/ATTACH][ATTACH]16326[/ATTACH][ATTACH]16327[/ATTACH][ATTACH]16328[/ATTACH]

Thunar would be prefect for me if I could address these inconsistency's.

Fianally, how would I go about making Thunar my default file browser?

Thanks in advance,
Tony.

---

### Post by aysiu on 2006-09-25
I've never experienced #4 in Thunar. Maybe it has something to do with the icon theme you're using?

The others I don't believe you can fix. People use Thunar because it's lightweight, not configurable.

Maybe to make Thunar your default browser, you might have to do this: ```
sudo dpkg-divert --divert /usr/bin/nautilus.old --rename /usr/bin/nautilus
sudo ln -s /usr/bin/thunar /usr/bin/nautilus
```

---

### Post by ahaslam on 2006-09-25
Thanks for the reply.
I understand the second command, but what's with the first one, is it basicly just renaming the nautilus binary? I just want to know what I'm doing, so that I can undo it if I don't like it ;)

Cheers,

Tony.

---

### Post by aysiu on 2006-09-25
Yes, it's basically renaming the old one. To undo it: ```
sudo rm /usr/bin/nautilus
sudo dpkg-divert --rename --remove /usr/bin/nautilus
```

---

### Post by ahaslam on 2006-09-25
My lappy doesn't like it, if I 'gksudo nautilus' Thunar opens, but 'nautilus' causes a short hang & loads nothing. The permissions seemed ok, so I rebooted. Upon boot it hung for a long time while trying to load nautilus. Also without nautilus, there's no desktop :( - How does xfce address this?

Cheers,

Tony.

---

### Post by aysiu on 2006-09-25
Hm. Good point. Nautilus isn't just a file browser. It manages the desktop as well.

XFCE doesn't really need Nautilus to load, unlike Gnome, so it's a non-issue for XFCE.

What about Nautilus do you dislike? (Just curious)

---

### Post by ahaslam on 2006-09-25
There's only one thing that I dislike and that's the speed (or lack of it). Nautilus takes a very long time to load large directories (as in # of files, not size), especially if there's a lot of images to preview. Thunar seems to handle this situation much better & I often use it if I expect to be trawling through my photo archive.

Tony.

---

### Post by aysiu on 2006-09-25
Maybe not the ideal solution, but perhaps you could use an external application like F-Spot to manage photos and images?

---

### Post by ahaslam on 2006-09-25
> **aysiu said:**
> Maybe not the ideal solution, but perhaps you could use an external application like F-Spot to manage photos and images?
I find it useful for a few things but importing a folder takes a similar time to Nautilus & then it catalogues it, taking a little longer. It's only Thunar that opens up these folders with the desired speed :( At least I can use it when desired ;)

Cheers.

PS. Why do people use Picassa, when there's F-Spot & The GIMP? Saying that, why have I got it installed :-k

---

### Post by aysiu on 2006-09-25
You can also turn off image previews in Nautilus for larger files. Not sure if that'd help.

---

### Post by ahaslam on 2006-09-25
Unfortunatley, it's the previews that I need to find the photo. My camera just saves the file as a number in a date labeld folder. I like this method, It'd take ages to rename the pics so that they had some meaning.

I'll just keep Nautilus how it is for now & invoke Thunar as & when it's required (or log in to xfce).

Thank you for your suggestions, feel free to keep them coming, but I've got to get some sleep now - I only got 3 hours yesterday :(

Tony.

---

### Post by aysiu on 2006-09-25
I guess I was thinking that you'd use Nautilus for general file management and F-Spot for photo management.

---


---
title: "Nautilus list mode woes"
date: 2006-12-26
forum: Desktop Environments
---

### Post by Jacky_J on 2006-12-26
This "feature" has been a part of nautilus for as long as I can remember:  Nautilus doesn't know the exact file type until you click on a file.  

The problem is that when i click on a certain file, it will rearrange itself because nautilus determines its true file type, then sorts the list by that name.  This is because I use list view mode and arrange by file type by default. 

For example, if i have a bunch of ogg files, nautilus will show them first as "Ogg multimedia" files.  However, when i just single click one to highlight it, the type will immediately change to "Ogg Vorbis audio".  This gets frustrating because when i double click a file, the first click will resort the list, then the next click will open another file.

My question:  is there anyway to force nautilus to load the correct file type information?

Thanks

---

### Post by morphodone on 2007-08-18
I guess I'm kicking a dead horse here but this really bothers me too.

So much that I might just use KDE.

---

### Post by CameO73 on 2007-08-18
I had never noticed this (somewhat weird) behaviour! (possibly because I use various other programs to manage my files, i.e. Exaile for music, gnome-terminal for most other file operations)

But I have to admit: it can be annoying. But only when you sort on Type, otherwise the 'retyping' has no effect on the list sort. I did some quick searches on the subject, but could not find anything.


You should probably file a bug at [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by oblivious on 2008-04-14
It's been some time since the original post, but I'll post this in case anyone is still having this problem.
 I searched around a bit and came up with a workaround which consists in overriding the description of the ogg mimetype in order to match the one Nautilus gives the file when you click on it, thus avoidind the obnoxious re-sorting bug...

 So, open a terminal and type:

```

gksudo gedit ~/.local/share/mime/packages/Override.xml

```

and add this line inside the mime-info tag:

[HTML]
<mime-type type="application/ogg"><comment>Ogg Vorbis audio</comment><glob pattern="*.ogg"/></mime-type>
[/HTML]

 then you 

```

update-mime-database ~/.local/share/mime

```

and 

```

killall nautilus

```

 and you're done. 

You should verify the registered mime type name by editing the file "/usr/share/mime-info/gnome-vfs.mime" and looking for the string "ogg". Same thing can be done for any "uncooperative" file types.

Hope someone finds this useful.
 Cheers

---

### Post by Jacky_J on 2008-04-16
I just wish the ubuntu gods would add this fix so i don't have to. :)

---


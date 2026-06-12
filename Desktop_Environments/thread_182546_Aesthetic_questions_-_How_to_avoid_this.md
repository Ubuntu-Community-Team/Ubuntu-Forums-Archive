---
title: "Aesthetic questions - How to avoid this?"
date: 2006-05-26
forum: Desktop Environments
---

### Post by jolinux on 2006-05-26
First of all, sorry, my english sux.

1) By default, gnome desktop use different sizes in my incons. I want the same size in all, preferably automatically. It is possible?

2) What font must be install to see all websites correctly? In some sites cant see all characters in tables (price-lists, for example). I use the <<Ctrl+->> key combination in my firefox but then, the characters are too small for read.

Thx for help.

---

### Post by bruce89 on 2006-05-26
[QUOTE=jolinux]First of all, sorry, my english sux.[/QUOTE]
It's better than my spanish!

[QUOTE=jolinux]
1) By default, gnome desktop use different sizes in my incons. I want the same size in all, preferably automatically. It is possible?[/QUOTE]
They aren't supposed to be the same size, could you post a screenshot to illustrate what you mean?  (Press "Print Screen".)
[QUOTE=jolinux]
2) What font must be install to see all websites correctly? In some sites cant see all characters in tables (price-lists, for example). I use the <<Ctrl+->> key combination in my firefox but then, the characters are too small for read.[/QUOTE]
```
sudo apt-get install msttcorefonts
```

---

### Post by jolinux on 2006-05-26
Ok, here is...

---

### Post by meng on 2006-05-26
Hey, very nice screenshot btw. I think your problem is not that the ICONS are different sizes, it's that the PREVIEWS are different sizes, as one would expect with different documents with varying paper size and/or resolution. I suspect you can fix the problem by turning off the PREVIEW option in Nautilus.

---

### Post by art on 2006-05-26
I don't know if it is possible to make this automatic, but I can tell one way to reduce the annoyance. 
1)Go to Application->SystemTools->ConfigurationEditor->apps->nautilus->icon_view and choose default_zoom_level small
If you want all the icons on your desktop to be of the same size, you can disable showing thumbnails 
2) Application->SystemTools->ConfigurationEditor->apps->nautilus->preferences and change show_image_thumbnails to never. Now they all will be the same size but no thumbnails.

---

### Post by meng on 2006-05-26
Sorry my mistake - thumbnails, not previews. Thanks art.

---

### Post by jolinux on 2006-05-26
Perfect. That was. Set show.... to never.

Thx all

---

### Post by meng on 2006-05-26
Glad it worked out for you. Personally I like the preview ... no damnit, _thumbnail_, option, but it's all about choice, eh? I do have a question (and hence a reason for posting). How come some of my documents and media files are previewed in Nautilus, and others aren't, and just appear as a generic MPG or PDF or AVI icon?

---

### Post by ifokkema on 2006-05-26
[QUOTE=meng]I do have a question (and hence a reason for posting). How come some of my documents and media files are previewed in Nautilus, and others aren't, and just appear as a generic MPG or PDF or AVI icon?[/QUOTE]

Hi again :),

You can configure the preview option to work only for a certain file size (and only for local disks). See Nautilus preview preferences for that.

Ivo

---

### Post by meng on 2006-05-26
I hadn't considered that, since I had thought that most of my MPGs were of similar size to one another, but I will check it out when I get home.

---


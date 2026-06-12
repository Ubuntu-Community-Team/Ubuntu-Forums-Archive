---
title: "Gnome shell and docky problem"
date: 2011-09-05
forum: Desktop Environments
---

### Post by sanderd17 on 2011-09-05
I like the fact that Unity has a vertical dock because it keeps your screen width and height ration the same.

However, I also like most Gnome Shell features (window management, launching apps ...). So I tried setting up a dock on GS that looks a bit like the Unity dock (but off coarse not with the lenses and unity launcher).

I tried dockbarX and AWN and they just didn't work too well with GS. So I arrived at Docky.

Docky works good if you don't put it in panel mode, but in panel mode, the docky icon and the activities button are overlapping (see attachment).

Does anyone know a solution for this? (like giving an offset to the docky icons)

---

### Post by claracc on 2011-09-06
Perhaps  you can fix this overlapping reducing the side panel of docky, this can be done as is indicated in this link: [http://do.davebsd.com/wiki/Talk:Docky#How_to_resize_Gnome_Do.27s_Docky.3F](http://do.davebsd.com/wiki/Talk:Docky#How_to_resize_Gnome_Do.27s_Docky.3F)

> How to resize Gnome Do's Docky?

I find the icons in Docky too big for my preference, but I couldn't find any settings I can change to set it smaller. Do anyone have any ideas about this? - jonkoay

Solved: It's a bit tricky, but if you hover over the top edge of Docky - try doing this on a divider for best results - you can click and drag down to shrink the bar as a whole. Likewise, if you want the bar and icons larger, do the same except click n' drag up.

---

### Post by sanderd17 on 2011-09-06
The link doesn't work, and dragging the top thing? I suppose they use Docky in horizontal mode, and that makes it resize the icons. But that's also possible with the settings dialog.

---

### Post by claracc on 2011-09-07
Well, it is odd, the link goes to a page without text now but I have copied the quoted comment from it, I don't know whats the matter.

Anycase, I have find this other link: [http://superuser.com/questions/269966/id-like-to-prevent-maximize-from-covering-one-third-of-the-screen](http://superuser.com/questions/269966/id-like-to-prevent-maximize-from-covering-one-third-of-the-screen) which explains howto use compiz to control the size of windows, perhaps in this way, you can avoid the overlapping with docky.

I have docky, and an obvious solution ( I have the panel at the bottom) is to reduce the size of icon in dock settings of docky  in order to reduce the length of panel, you can try it.

---

### Post by sanderd17 on 2011-09-07
Hmm, Gnome-shell can't work with Compiz.

And I can reduce the length of the list, but it's always aligned to the top of the screen, it should be a few pixels lower.

Anyway, thanks for the help, but I think Docky and Gnome-shell just can't do this. I'll have to look for something else.

---


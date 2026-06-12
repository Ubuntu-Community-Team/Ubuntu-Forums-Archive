---
title: "Pidgin background image"
date: 2007-09-07
forum: Desktop Effects &amp; Customization
---

### Post by isaacj87 on 2007-09-07
Hello,

I've downloaded a gtkrc2.0 file that tells pidgin to display a background image. But everytime I scroll down on my buddy list it's like the background starts to overlap on itself. I was wondering if there was a way to make the background static and non-moving.

here's the gtkrc file

```

pixmap_path "/home/isaac/Pictures/Extras"
style "my-blist" {
bg_pixmap[NORMAL] = "pidgin_bg.jpg"
text[NORMAL] = "#000000"
bg[NORMAL] = "#F5D8BC"
base[NORMAL] = "#F5D8BC"
GtkTreeView::odd_row_color = ""
GtkTreeView::even_row_color = ""
}

widget "*pidgin_blist_treeview" style "my-blist"

```

Thanks

---


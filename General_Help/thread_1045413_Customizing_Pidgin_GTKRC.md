---
title: "Customizing Pidgin GTKRC"
date: 2009-01-20
forum: General Help
---

### Post by cjohn106 on 2009-01-20
I am customizing Pidgin's backgrounds (buddy list and such) I am currently trying to modify the conversation window background. I have been able to make the conversation window a color, which I did not pick. I am trying to make it a certain image.


This is my code. I think I just need the right widget or something. The Buddylist background does work, I am just trying to get the conversation window background to be the same. With this code, the conversation window only appears as color #F5D8BC. Here is the code:



pixmap_path "~/"
style "my-blist" {
bg_pixmap[NORMAL] = "/.purple/backgrounds/Windows_Vista_Wallpaper_by_Augermage.jpg"
text[NORMAL] = "#ffffff"
#this makes the text white, if you want black, take this code:
#text[NORMAL] = "#000000"
bg[NORMAL] = "#F5D8BC"
base[NORMAL] = "#F5D8BC"
GtkTreeView::odd_row_color = ""
GtkTreeView::even_row_color = ""

}
widget "*pidgin_blist_treeview" style "my-blist"
widget "*pidgin_conv_imhtml" style "my-blist"

---

### Post by cjohn106 on 2009-01-22
Anybody else try to do this, or get it right successfully? I just need to find the right widget or something.

---

### Post by cjohn106 on 2009-01-22
is there any way in Ubuntu to view all the widgets available for a program?

---


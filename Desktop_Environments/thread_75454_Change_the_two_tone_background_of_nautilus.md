---
title: "Change the two tone background of nautilus?"
date: 2005-10-13
forum: Desktop Environments
---

### Post by vayu on 2005-10-13
On my Hoary, I changed the background color of nautilus.  I can't seem to find where or how I did that.  I would also like to do the same to the background of Evolution.

---

### Post by Wolki on 2005-10-13
[QUOTE=vayu]On my Hoary, I changed the background color of nautilus.  I can't seem to find where or how I did that.  I would also like to do the same to the background of Evolution.[/QUOTE]

This feature is hidden really, really well.

Open Nautilus. Go to Backgrounds & Emblems, and choose a color/pattern you would like to use. Now drag that color /with the middle mouse button/ to the open nautilus window. A little window pops up, offering you to choose between adding the background to this folder, or adding it to all folders. Choose the last one.

(Note: If you have set cutom backgrounds for single folders, this will not overwrite them; so you can change the standard background and keep your customizations)

I don't know if there's a way to do it in Evolution though.

---

### Post by vayu on 2005-10-14
[QUOTE=Wolki]Open Nautilus. Go to Backgrounds & Emblems, and choose a color/pattern you would like to use. Now drag that color /with the middle mouse button/ to the open nautilus window. A little window pops up, offering you to choose between adding the background to this folder, or adding it to all folders. Choose the last one.
[/QUOTE]

This will only work in Icon view for me.

On my Hoary system I found a configuration file somewhere where I entered six digit hex numbers for the colors of the odd and even rows.  I can't remember where that was.

---

### Post by Wolki on 2005-10-14
[QUOTE=vayu]This will only work in Icon view for me.

On my Hoary system I found a configuration file somewhere where I entered six digit hex numbers for the colors of the odd and even rows.  I can't remember where that was.[/QUOTE]

Yeah, sorry, i misunderstood your original question. Don't know how to change it for list view, I'm afraid.

---

### Post by vayu on 2005-10-15
In case anyone else ever want's to change the two tone color background in list view for nautilus I finally found it.

put the following in .gtkrc-2.0 in your home directory (create the file if it doesn't exist)

```

style "default"
{
  GtkTreeView::odd_row_color        = "#ffffff"
  GtkTreeView::even_row_color       = "#ffffff"
}
                                                                               
class "GtkWidget" style "default"

```

The above makes the entire background white.  Put whatever color values you want.  Whenever I want to get a number for a color, I use the GIMP color picker to help me find a color by eye and then it gives me the hex values for that color.

---

### Post by whiskytroll on 2006-11-14
"put the following in .gtkrc-2.0 in your home directory (create the file if it doesn't exist)"

Thanks for that! I'd love to make changes there... But I couldn't find that file. I did however find a .gtkrc-1.2-gnome2 that I opened whith curiosity. But it said in the first line "# Autowritten by gnome-settings-daemon. Do not edit", so I didn't dare to... Am I a coward or did I do right? And if I,m not a coward, how shall I proceed? I did try to create a .gtkrc-2.0 and put in the lines, but nothing happened, even when I relaunched the nautilus.

---

### Post by vayu on 2006-11-15
> **whiskytroll said:**
> "put the following in .gtkrc-2.0 in your home directory (create the file if it doesn't exist)"

I did try to create a .gtkrc-2.0 and put in the lines, but nothing happened, even when I relaunched the nautilus.

It was right to create the file.  I believe only very old programs use the .gtkrc-1.2-gnome2.  Do you by any chance also use KDE on the same machine?   There are settings and themes you might have set in KDE to make GTK apps look better in KDE.  When those are set then the gtkrc-2.0 file settings do not work for me.  In KDE under settings/appearance/GTK style and Fonts, are settings to use KDE settings in GTK apps. Also you might try unchecking in themes/colors, "Apply colors to non-KDE applications".

---


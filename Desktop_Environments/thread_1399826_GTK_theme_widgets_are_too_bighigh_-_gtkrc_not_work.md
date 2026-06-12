---
title: "GTK theme: widgets are too big/high - gtkrc not working correctly?"
date: 2010-02-06
forum: Desktop Environments
---

### Post by mojo2012 on 2010-02-06
Hi guys,

imho, all GTK widgets are much too big. The ratio between width and height is just a mess. All widgets are too high, especially ,tabs, buttons and comboboxes (which basically are buttons, afaik).

So, I decided to make my own little theme to end this ugliness ;-). I used the theme "eGTK" as template and created "eGTK Simple".

I managed to slim down the whole UI by decreasing all kinds of paddings and thinknesses and stuff like this, BUT: widgets of the same kind don't have the same height ... (look at the included screenshot)!

1) and 2) are both chomboboxes, but 2) is one pixel higher
(Yes, I know, it's just a pixel and 99,9% of all users won't ever notice is -- But I do. And everytime I look at the screen I hate it. 

3) and 4) are both buttons. 4) seems to adopt my gtkrc settings, 3) doesn't. 3) should normally have an icon. But I disabled all kind of icons in menus and on buttons. Somehow they seem to still be there and prevent the button from becoming less high.

Any ideas how to resolve these issues?


--------------------------------------------------
The theme can be downloaded here: [http://content.wuala.com/contents/mojo2012/Public/Simple%20eGTK.tar.gz?lang=de&dl=1](http://content.wuala.com/contents/mojo2012/Public/Simple%20eGTK.tar.gz?lang=de&dl=1)
The widget height changes are not yet included as it simply looks ugly to have different buttons heights.

Here you can see how the theme looks: [http://yfrog.com/htegtksimplep](http://yfrog.com/htegtksimplep)

---

### Post by VCoolio on 2010-02-06
Does it make a difference if you specify the size of the (non-existing) button icons?
gtk-icon-sizes = "gtk-button=20,20:gtk-dialog=48,48"

Options are: gtk-menu, gtk-button, gtk-small-toolbar, gtk-large-toolbar, gtk-dnd, gtk-dialog.

---

### Post by mojo2012 on 2010-02-06
If I set gtk-button and gtk-dialog to 0,0 all button icons are 16x16. If I set 1,1, there is an ugly pixel visible on the buttons. So obviously the icons become smaller, but the buttons have the same height as before.

While playing around with the two settings I even noticed that the Cancel and the Open button had different heights at the same time ...

I hope in Gnome 3/GTK3 all this mess will be gone for ever ... and that the stone-age Open/Save dialogs are replaced by more modern ones ;-)

---

### Post by mojo2012 on 2010-03-09
So, I played around for a few hours with a tool called gtk-parasite. It lets you look into Gtk UIs and manipulate some settings (eg borders, paddings, ...).

I finally managed to decrease the size of almost all buttons, even the big fat dialog buttons. There are only a few buttons that still keep their "fatness".

For normal buttons I use this gtkrc:
```

    GtkButtonBox   ::child_min_heigth     = 0
    GtkButtonBox   ::child_internal_pad_x = 6
    GtkButtonBox   ::child_internal_pad_y = 0

    GtkButton::default-border = {0, 0, 0, 0}
    GtkButton::default-outside-border = {0, 0, 0, 0}
    GtkButton::inner-border = {0, 0, 0, 0}

    GtkButton::child-displacement-x     = 0
    GtkButton::child-displacement-y     = 0

```But to set the bordes to 0 does not work for dialog buttons (OK, cancel, ...). To decrease their size I added this:
```

style "dialog-button" {
    xthickness = 10

    GtkButton::default_border         = {3, 3, 3, 3}
    GtkButton::default-outside-border = {3, 3, 3, 3}
    #GtkButton::inner-border = {3, 3, 3, 3}
}

widget_class "*<GtkDialog>*GtkHButtonBox*GtkButton*"               style "dialog-button"
widget_class "*<GtkPrintUnixDialog>*GtkHButtonBox*GtkButton*"          style "dialog-button"
widget_class "*<GeditPreferencesDialog>*GtkHButtonBox*GtkButton*"      style "dialog-button"

```

Strange thing is, that for dialog buttons I have to increase the border ... 

There are still buttons (eg the "print preview" button in the print dialog) that are fat. And there are problems with the focus rectangle - it sometimes looks weird!

But there is hope again ;-)

---

### Post by HyperHacker on 2010-04-25
> **mojo2012 said:**
> 
    GtkButtonBox   ::child_min_heigth     = 0
Spelling height correctly might help.

---

### Post by mojo2012 on 2010-04-25
You're right, my fault. Nonetheless It doesn't work ;-)

(look at the buttons on the screenshot)

I think, it might be that the programmers hardcoded the height of some buttons ...

EDIT: Today I checked the whole gtkrc again and found indeed a(nother) bug. I'm happy to announce that I finally managed to successfully slim down all widgets, even the fat print preview button on the screenshot.

The theme is available uner: [http://gnome-look.org/content/show.php/Simple+eGTK?content=119812](http://gnome-look.org/content/show.php/Simple+eGTK?content=119812)

---


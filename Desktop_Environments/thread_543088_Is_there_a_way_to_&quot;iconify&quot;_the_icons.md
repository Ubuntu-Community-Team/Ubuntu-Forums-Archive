---
title: "Is there a way to &quot;iconify&quot; the icons?"
date: 2007-09-04
forum: Desktop Environments
---

### Post by Majorix on 2007-09-04
If you have ever seen a Windows box (which I am sure you did) you will know what I mean.

Under Gnome, is there a way to make, for example, .py files like a python? Or, for another example, .txt files like a notebook?

The desktop could look better this way I believe. At least to me it will. So please help me.

Thanks a lot.

---

### Post by jim_p on 2007-09-04
You mean you want nautilus to display a standard icon instead of thumbnails of text files etc?

You open up a Nautilus window and go to Edit > Preferences > Preview or Thumbnails
and disable what you want to.
(I am not sure about these since my Ubuntu is in greek).

If that does not satisfy you you can always open up gconf-editor and go to the 
"/desktop/gnome/thumbnailers" submenu and disable them all together
In the subkeys below that one, you can disable thumbnails for specific filetypes

---

### Post by spupy on 2007-09-04
One way i can think of is to manually change the icons in /home/<username>/.icons/<icontheme_youre_using>/<some_size>/mimetypes/
But it's alot of work to find the icons and replace/rename them.

---

### Post by Majorix on 2007-09-04
> **jim_p said:**
> You mean you want nautilus to display a standard icon instead of thumbnails of text files etc?

You open up a Nautilus window and go to Edit > Preferences > Preview or Thumbnails
and disable what you want to.
(I am not sure about these since my Ubuntu is in greek).

If that does not satisfy you you can always open up gconf-editor and go to the 
"/desktop/gnome/thumbnailers" submenu and disable them all together
In the subkeys below that one, you can disable thumbnails for specific filetypes

Would disabling the thumbnails get me icons? Or did I misunderstand you? Thanks for clarifying.

And I tried your take with Nautilus > Edit and it didn't work :(

> **spupy said:**
> One way i can think of is to manually change the icons in /home/<username>/.icons/<icontheme_youre_using>/<some_size>/mimetypes/
But it's alot of work to find the icons and replace/rename them.

Yeah as you said thats a lot of work. And you too know how many filetypes there are. It would take ages to find icons for them all and make them useable by Gnome. Thanks for the suggestion though.

---

### Post by jim_p on 2007-09-05
Going through the gconf-editor way will disable the thumbnails for sure.
That will get you "normal" icons.

However, this happened to me when I disabled the thumbnails, but it's
only for these 2 images (see screenshot)
ALL other icons in my pc are of normal size except for these 2.

---

### Post by Majorix on 2007-09-05
I just disabled them through gconf-editor. But I forgot how to restart X without restarting the PC. Can anybody remind me?

---

### Post by spupy on 2007-09-05
Control-Alt-Backspace to restart X, but i dont think you need this. Since you are using gnome, just log out and then login back again.

---

### Post by Majorix on 2007-09-05
Ok thanks a lot for reminding. I had just logged out and logged back in anyways.

But it doesn't work. The thumbnails didn't change at all. I am stuck.

---


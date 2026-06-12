---
title: "How to set standard size of windows"
date: 2009-02-17
forum: General Help
---

### Post by DeMus on 2009-02-17
Hi,
when I open a program, in this case pypar2, the size of the window is too small to hold all the text. I would like it to open in a larger window, both width as height. How and where to set this?
Now every time the program starts, I have to do it manually.

Thanks.

---

### Post by whoop on 2009-02-17
This is probably a per-application setting. Check if you can find a dot-directory in your user directory for the program you are using. ".pypar2" for example. It could also be in the .config directory. If you can't see dot-directories you should enable you file browser to show hidden files. It could be that pypar2 does not support remembering window size/placement although allot of applications do.

---

### Post by DeMus on 2009-02-17
> **whoop said:**
> This is probably a per-application setting. Check if you can find a dot-directory in your user directory for the program you are using. ".pypar2" for example. It could also be in the .config directory. If you can't see dot-directories you should enable you file browser to show hidden files. It could be that pypar2 does not support remembering window size/placement although allot of applications do.

I hope I found the right file. I searched for all files related to pypar2 and I found one in which the windows size is described. I changed and now I want to test it.
Thanks for the advice.

---

### Post by DeMus on 2009-02-17
> **DeMus said:**
> I hope I found the right file. I searched for all files related to pypar2 and I found one in which the windows size is described. I changed and now I want to test it.
Thanks for the advice.

Yes, I did. I found the right values and changed them to what I want to have. So, this thread is solved.
In folder /usr/share/pypar2 is a file called  dlg-output.glade. It starts with:

<?xml version="1.0" standalone="no"?> <!--*- mode: xml -*-->
<!DOCTYPE glade-interface SYSTEM "http://glade.gnome.org/glade-2.0.dtd">

<glade-interface>

<widget class="GtkDialog" id="dlg-output">
  <property name="width_request">800</property>
  <property name="height_request">600</property>

As can be seen I have changed the size to 800x600. Now all the texts are visible.

---


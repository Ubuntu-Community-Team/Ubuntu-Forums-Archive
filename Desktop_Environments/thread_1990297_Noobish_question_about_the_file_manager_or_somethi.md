---
title: "Noobish question about the file manager or something..."
date: 2012-05-29
forum: Desktop Environments
---

### Post by scubscub on 2012-05-29
Hello, I was wondering, what is the actual name of the (sub?)program that saves files, for instance from firefox or LibreOffice?  It looks like Thunar but does not say anything but "save" or "save as" on the top, and does not match thunar's settings (e.g., enabling "view hidden folders" on thunar does not affect this save program).

I only ask what it is so that I can find some way to modify it -- I would like to enable hidden folders, for instance.  Also, it opens by default to a virtual folder titled "Recently Used", I would like to change this so it opens to the actual folder that was used most recently.

---

### Post by MG&amp;TL on 2012-05-29
It's a dialog from Gtk. Gtk is the framework behind Gnome, Xfce, and LXDE, among others.

Programs call gtk_file_chooser_new(), then set some parameters, and away it goes.

---

### Post by scubscub on 2012-05-29
Thanks.  Okay, so the program or dialog is called GTKFileChooser, it is modified by the commands or signals or whatever they're called, found here:

[http://developer.gnome.org/gtk/2.24/GtkFileChooser.html]("http://developer.gnome.org/gtk/2.24/GtkFileChooser.html")

But to reassert my noobishness here, how do I go about changing the file chooser's behavior?  Is there a file somewhere I modify in leafpad?

---

### Post by dniMretsaM on 2012-05-29
> **scubscub said:**
> But to reassert my noobishness here, how do I go about changing the file chooser's behavior?  Is there a file somewhere I modify in leafpad?

You'll have to do some coding. Depending on what exactly you want to do, it could be the GtkFileChooser code (which is written in C) and/or the code of the program that's invoking said dialog (languages will obviously vary here). Or possibly the GTX+ wrappers for the language that the program uses.

---

### Post by scubscub on 2012-05-29
Hmmm... but the behavior of the file chooser seems to be the same no matter what program invokes it, which is why I thought there might be a system-wide configuration file (or some such) determining how the file chooser acts when it is invoked.

And there is something here:

file:///usr/share/glib-2.0/schemas/org.gtk.Settings.FileChooser.gschema.xml

---

### Post by scubscub on 2012-05-29
Here is a page with a "patch" doing pretty much what I want, but I have no idea how to implement this:
[URL="https://bugzilla.gnome.org/show_bug.cgi?id=644426"]
https://bugzilla.gnome.org/show_bug.cgi?id=644426[/URL]

---

### Post by llua+ on 2012-05-29
That patch is for gtk3. The gtkfilechooser function thunar and firefox uses is from gtk2.

---

### Post by dniMretsaM on 2012-05-29
> **scubscub said:**
> Hmmm... but the behavior of the file chooser seems to be the same no matter what program invokes it, which is why I thought there might be a system-wide configuration file (or some such) determining how the file chooser acts when it is invoked.

And there is something here:

file:///usr/share/glib-2.0/schemas/org.gtk.Settings.FileChooser.gschema.xml

Apparently there is a settings file located at [FONT=Courier New]~/.config/gtx-2.0/gtkfilechooser.ini[/FONT] (if it doesn't exist you can create it). Example contents [here]("https://dl.dropbox.com/u/51503579/gtkfilechooser.png"). You'll want to start by changing [FONT=Courier New]ShowHidden[/FONT][FONT=Verdana] to [FONT=Courier New]True[FONT=Verdana]. Sorry about the bit of misinformation earlier. And thanks to llua in the IRC room (llua+ who posted above) for pointing out my mistake to me.[/FONT][/FONT][/FONT]

---

### Post by scubscub on 2012-05-29
I created the file with the ShowHidden changed to true, and restarted, it doesn't seem to have any effect -- hidden folders still do not appear in the chooser.

Ie, ~/.config/gtk-2.0/gtkfilechooser.ini .  I had to create the gtk-2.0 folder as well.

---

### Post by llua+ on 2012-05-29
I highly doubt that screenshot is gonna be there for long. So for archiving purposes.
syntax for the file is
```
[Filechooser Settings]
LocationMode=filename-entry
ShowHidden=false
ExpandFolders=true
ShowSizeColumn=true
GeometryX=186
GeometryY=109
GeometryWidth=908
GeometryHeight=806
SortColumn=name
SortOrder=ascending

```and like what dniMretsaM said, in your situation you want ShowHidden to read true.

EDIT: and again. that file only affects programs that uses gtk2 still. Firefox should be one. I haven't used LibreOffice before, but if it uses gtk3 (thus calls the gtk3 version of gtkfilechooser) you need to change a setting with dconf-editor(org.gtk.settings.file-chooser).

---

### Post by scubscub on 2012-05-29
Thanks to both of you.

I had an error in my original version of the file but it is now working, showing the hidden files, when called up by firefox or by libreoffice, both.

I still want to change the default folder, is there a way to use something like that gtk3 patch for gtk 2?

---


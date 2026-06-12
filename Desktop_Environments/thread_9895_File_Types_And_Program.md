---
title: "File Types And Program"
date: 2005-01-02
forum: Desktop Environments
---

### Post by redman5087 on 2005-01-02
Where can I find or change the file types and programs in Ubuntu.
 
Kind Regards
Patrick

---

### Post by crane on 2005-01-02
[QUOTE=redman5087]Where can I find or change the file types and programs in Ubuntu.
 
Kind Regards
Patrick[/QUOTE]

How do you mean change file types?

Under Computer>DesktopPreferences>Preferred Applications  You can set what to use for e-mail , webbrowser, Tect editor, and terminal. You can also rightclick on a file and select open with other application.

 Is that what you taliking about doing?

---

### Post by mal on 2005-01-02
I have the same question.  See previous thread: 

[http://www.ubuntuforums.org/showthread.php?t=9380](http://www.ubuntuforums.org/showthread.php?t=9380)

It seems that this Gnome preference tool has been left out of Ubuntu.  I have not yet seen an explanation of this or whether there is some other way to access it.

Mal

---

### Post by Darrena on 2005-01-02
Right click on a file of each type and select properties, then select the open with tab.

---

### Post by mal on 2005-01-03
[QUOTE=Darrena]Right click on a file of each type and select properties, then select the open with tab.[/QUOTE]

From the Gnome manual, it seems that the "File Types and Programs" preference tool provides more options than available through file properties.  For example, it should be possible to select the Nautilus component viewer for each file type.

I am still hoping that some guru will be able to tell us what happened to this preference tool .

Mal

---

### Post by tiiim on 2005-01-04
[QUOTE=mal]From the Gnome manual, it seems that the "File Types and Programs" preference tool provides more options than available through file properties.  For example, it should be possible to select the Nautilus component viewer for each file type.

I am still hoping that some guru will be able to tell us what happened to this preference tool .

Mal[/QUOTE]
 i dont know but if can you download this prog from the Universe source?

But yeah be nice to know why its left out but in the mean time you can still open it under right click i guess...

---

### Post by taj on 2005-10-30
It's October 2005 and Breezy now, and I am experiencing the same problem: I installed Openoffice 2.0 according to [this thread]("http://ubuntuforums.org/showthread.php?t=80392"), and removed Ooo1.9 (shown as  Openoffice2 to make our life easier, I guess ;) ). Now every time I double click e.g. a Word document in Nautilus it wants to open with Openoffice2 (Ooo1.9), unless I rightclick the document and choose Openoffice2.0 (the real 2.0).
So, how can I install the "File Types and Programs" preference tool that I need, or where can I find its function? I strongly suggest to include it into the next release.

---

### Post by dryden on 2008-01-26
Three years ago, people were wondering how to edit the "Open with" context menu of Nautilus. They were directed to the properties window f the file. But guess what: "open with" programs you add yourself do not get the same status as existing options, and you cannot remove or modify existing options, and if you want to add the same program twice, you will not be able to distinguish between the two because it only shows the name of the program.

Three years later, there still is no GUI way of doing this.

Grrrrr. Time to find out for myself.

The [Gnome Admin Guide](http://www.gnome.org/learn/admin-guide/latest/mimetypes-registering.html) tells me how:

In order to add a file handler, you create a .desktop file with the right mime-type(s) in ~/.local/share/applications, or edit those in /usr/share/applications. An easy way is to add one using the Nautilus Properties/Open With tab, and then modify it as it appears in ~/.local/share/applications. After modification, run sudo update-desktop-database to renew the mimeinfo.cache file. 

To change the default handler for a certain type, first find out the mime type of the file you want to assign:
```
gnomevfs-info <filename>
```

Then edit your ~/.local/share/applications/defaults.list to add a new line like:
```
audio/x-mpegurl=audacious.desktop
```

Then run the update tool again:
```
sudo update-desktop-database
```

It seems as if this is not enough for Nautilus to incorporate the new settings, so change anything using the Nautilus "Open with" settings, and it will then display your other changes as well.

To display or hide your new .desktop entry in the main menu, use the System/Preferences/Main Menu program.

---


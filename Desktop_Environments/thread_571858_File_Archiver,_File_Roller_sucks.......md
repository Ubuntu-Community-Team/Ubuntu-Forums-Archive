---
title: "File Archiver, File Roller sucks......"
date: 2007-10-09
forum: Desktop Environments
---

### Post by Hideaki on 2007-10-09
I'm looking for a new File Archiver, I hate file roller. I'm looking for something closer to the features WinRAR has.  The main thing that annoys me about file roller is the inability to just drag a folder from the File Roller window and dump it straight into an open folder in Nautilus. The next thing is not being able to know the % of the extraction, and which file it is extracting from(on multiple file archives). 

Also, support for all the formats I've got installed(unrar, 7z, etc).

Anyone know of a file archiver that will allow me to do those things? Or how to make File Roller act more like that?

---

### Post by kerry_s on 2007-10-09
yes they do. i switched to using "unp" for unpacking and i use the standard commands for packing.

**sudo apt-get install unp**

unp the-compressed-file

**man unp**

in thunar i have it set as a custom command

xterm -e unp %f

---

### Post by Hideaki on 2007-10-09
Hmm, I was looking for a GUI program.

---

### Post by wildkarde on 2007-10-09
You might want to try peazip.

[http://gnomefiles.org/app.php/PeaZip](http://gnomefiles.org/app.php/PeaZip)

Post your thoughts about the app if you can.  Other people might be curious.

---- edit

Hmm, i might have spoken too soon there.

Maybe Xarchiver?

---

### Post by Hideaki on 2007-10-09
Both Peazip and Xarchiver are the same or worst than File Roller. Still not allowing drag and drop or displaying how the extraction is going.

---

### Post by xat_ on 2007-10-09
This inability to drag and drop is a fault of Nautilus if I remember correctly. Very annoying indeed.

---

### Post by mexlinux on 2007-10-09
ark can do exactly what you want, even in GNOME (have just tested).

---

### Post by Hideaki on 2007-10-09
> **mexlinux said:**
> ark can do exactly what you want, even in GNOME (have just tested).

Thanks, I was gonna try that next, but wanted to avoid installing KDE.

I just tested it, it works very nicely. It's kind of sad that I have to use a KDE app to do something to simple. I might switch to KDE with the release of 7.10

Thanks for all the help :)

---

### Post by mexlinux on 2007-10-09
> **Hideaki said:**
> 
... It's kind of sad that I have to use a KDE app to do something to simple. I might switch to KDE with the release of 7.10...

You might like to also install 
kcontrol
kde-style-klearlook

Use them to trick the theme your kde apps, and belive me, you can barely know it's a KDE app running in GNOME
 
At the end, they are all linux apps running in the desktop you have chosen,

just consider them as written with a different toolkit.

Take this screenshot as a sample:
KDE app: kmail
QT app: qcad
GNOME app: evolution
GTK+ app: firefox
OpenOffice, it's own toolkit
They are all living in peace together.

And I bet you can barely see the difference.

---

### Post by 3rdalbum on 2007-10-10
> **Hideaki said:**
> I just tested it, it works very nicely. It's kind of sad that I have to use a KDE app to do something to simple. I might switch to KDE with the release of 7.10

No point - there is a patch for Nautilus that makes the drag 'n' drop from File Roller work as it should, and I believe it was accepted into the version of Gnome that will ship with 7.10. :-)

But there's no shame in installing parts of KDE, almost everybody does it as some KDE programs are better (and some Gnome programs are better).

---

### Post by wild_oscar on 2007-10-21
> **3rdalbum said:**
> No point - there is a patch for Nautilus that makes the drag 'n' drop from File Roller work as it should, and I believe it was accepted into the version of Gnome that will ship with 7.10. :-)

But there's no shame in installing parts of KDE, almost everybody does it as some KDE programs are better (and some Gnome programs are better).

I do not think Nautilus was fixed on 7.10  - I still cannot drag and drop to a nautilus opened window.

---

### Post by mriya3 on 2007-10-27
Drag and drop works for the icon view. Unfortunately the patch to make it work also in the tree view didn't make it in the final release.

(see [http://bugzilla.gnome.org/show_bug.cgi?id=171655](http://bugzilla.gnome.org/show_bug.cgi?id=171655))

---

### Post by wild_oscar on 2007-10-27
Is there a way to patch it so it can work with the list view?

---


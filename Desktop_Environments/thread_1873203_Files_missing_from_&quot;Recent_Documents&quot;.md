---
title: "Files missing from &quot;Recent Documents&quot;"
date: 2011-11-01
forum: Desktop Environments
---

### Post by Graeme.N on 2011-11-01
After much searching and reading, I am posting this query ...

Is there a setting somewhere that limits what file types appear in "Recent Documents" under "Places"?  My OpenOffice.org documents are not appearing there.

I have checked the ~/.recently-used and ~/.recently-used.xbel and the OO.o files appear in the ~/.recently-used file but not the ~/.recently-used.xbel file.

TIA for any help.

---

### Post by Graeme.N on 2011-11-07
Any ideas?

---

### Post by BobMarleyy on 2011-11-07
> **Graeme.N said:**
> After much searching and reading, I am posting this query ...

Is there a setting somewhere that limits what file types appear in "Recent Documents" under "Places"?  My OpenOffice.org documents are not appearing there.

I have checked the ~/.recently-used and ~/.recently-used.xbel and the OO.o files appear in the ~/.recently-used file but not the ~/.recently-used.xbel file.

TIA for any help.

I have the same problem. However, I am using LibreOffice and my .recently-used.xbel is in ~/.local/share.

Media files opened with VLC are also not appearing in Recent Documents. In contrast, when I open the same file with Totem, it is shown in Recent Documents. Files opened with VLC do not appear in any of the two .recently-used logs. This indicates that not certain files, but certain applications do not appear in the Recent Documents.
It happens with other applications as well, e.g. Leafpad.

Please someone help!

Cheers,
Bob

---

### Post by pavi_elex on 2011-11-08
Try this in terminal
```
touch ~/.gtkrc-2.0
gedit ~/.gtkrc-2.0
``` now type this line in file and save it.
gtk-recent-files-limit=100

---

### Post by BobMarleyy on 2011-11-08
> **pavi_elex said:**
> Try this in terminal
```
touch ~/.gtkrc-2.0
gedit ~/.gtkrc-2.0
``` now type this line in file and save it.
gtk-recent-files-limit=100

Thank you for the suggestion. I created the file and inserted the line but it does not solve the problem. Note that I already had set the limit to 25 documents (right click on places - properties - number to display). I do not think that the maximum number of documents shown in recent documents affects what is shown (just how much).

Somehow, some applications still do not appear in the Recent Documents list. If you have another suggestion I would like to hear it.

Cheers,
Bob

PS also note that in Xubuntu 11.10 gedit is replaced by leafpad

---

### Post by BobMarleyy on 2011-11-16
As Graeme already asked:
> **Graeme.N said:**
> Any ideas?
Or are we the only ones with this problem?

---

### Post by Graeme.N on 2011-11-18
Decided to "upgrade" to LibreOffice, and as I was doing so I noticed the libreoffice-gtk ("office productivity suite -- GTK+ integration") module ... installed that and the OOo/LO docs are now appearing in the "Recent Documents" list.:)=D>\\:D/

So I am now very happy!:lol:

---

### Post by BobMarleyy on 2011-11-19
Thank you for the suggestion, libreoffice is appearing in the recent documents list now. Probably, this package is installed when you install the whole libreoffice suite. I just installed the writer, so adding the libreoffice-gtk manually solves this recent documents problem.

However, files opened with vlc or leafpad do still not appear in the recent documents list. Do you mind if I hijack this thread? Because I still could use some help:
How can I get files opened with vlc or leafpad in the recent documents list?

I have looked for more *-gtk packages but none were there for vlc or leafpad. I have this problem since the clean install of Xubuntu 11.10. However, I changed the theme to a gtk3 compatible theme, so notifications (like from gwibber) would appear normally...

TIA,
Bob

---

### Post by Graeme.N on 2011-11-20
I installed the "full" LibreOffice package, but then had to install the GTK integration separately.

Feel free to hi-jack this thread for directly related purposes ... as is your stated intent.  I, too, would be keen for vlc related files to appear in "Recent Documents".  I use MousePad rather than LeafPad, and its files *_**do**_* appear in "Recent Documents".

---

### Post by BobMarleyy on 2011-11-29
Bump

---

### Post by BobMarleyy on 2011-12-18
Bump the bump

---


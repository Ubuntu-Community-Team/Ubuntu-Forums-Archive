---
title: "File Associations"
date: 2007-03-22
forum: Desktop Environments
---

### Post by Mark Erbaugh on 2007-03-22
How are files associated with applications in Gnome (Ubuntu Dapper)?

I am aware of the 'Open With' tab on the 'Properties' context (right click) menu for icons.  However, it seems that some file associations are 'permanent' in that they can't be removed on the 'Open With' tab.

I have two specific annoyances.

I installed the Screem HTML editor and now it wants to be the default editor for all plain text files.  I would like to disassociate Screem from some files, but I can't remove it in the 'Open With' tab - the remove button is grayed out.

For some reason, Gnome thinks that all my files with the extension .dat are MPEG videos and the icon that shows up is of a reel of film. When I click on an icon, it turns to the document icon (this is a plain text file), but when I refresh or reload the directory, it turns back to MPEG.

---

### Post by Mark Erbaugh on 2007-04-13
I finally figured out the answer to my own question. I'm posting it here in case others need the same information.

Programs that show up in the Nautilus Properties popup menu under Open With that can't be removed appear to come from associations in the file /usr/share/mimeinfo.cache. If you delete the association from here, it goes away from the Open With page.

Built in File type assignements (in my case associating .dat files with video/mpeg) are in /usr/share/mime/packages/freedesktop.org.xml.

These are also in /usr/share/mime/globs, but globs is generated automatically.

Once you have made changes to freedesktop.org.xml run:

sudo update-mime-database /usr/share/mime

I hope this helps,
Mark

---

### Post by ComplexNumber on 2007-04-13
or one could read [this]("http://ubuntuforums.org/showthread.php?t=408274").

---

### Post by Unconscious on 2007-04-13
Thank you, ComplexNumber, this was really helpful. :D 

The file I had to edit, though, was /usr/share/applications/mimeinfo.cache. That did the trick, and I was able to fix some other odd associations while I was in there.

I still think it doesn't need to be this difficult.

---

### Post by ComplexNumber on 2007-04-13
> **Unconscious said:**
> Thank you, ComplexNumber, this was really helpful. :D 

The file I had to edit, though, was /usr/share/applications/mimeinfo.cache. That did the trick, and I was able to fix some other odd associations while I was in there.

I still think it doesn't need to be this difficult.
glad to help. i knew all the information necessary to achieve what you wanted to do was in there(ie /usr/share/applications) because it worked for me and all the 'open here' data is in there.. i didn't have to edit the mime.info file, though.

---

### Post by Ateo on 2007-04-19
> **Unconscious said:**
> Thank you, ComplexNumber, this was really helpful. :D 

The file I had to edit, though, was /usr/share/applications/mimeinfo.cache. That did the trick, and I was able to fix some other odd associations while I was in there.

I still think it doesn't need to be this difficult.

Exactly. File associations under KDE is as easy as Windows. Why can't this simplicity be implemented with Gnome? Grrr.

---


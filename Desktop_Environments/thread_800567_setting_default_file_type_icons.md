---
title: "setting default file type icons"
date: 2008-05-19
forum: Desktop Environments
---

### Post by gnivler on 2008-05-19
Looking for a way to set the default icon for a file type in GNOME.  I am not talking about a per-file/folder setting which is accessed through properties in nautilus.  I want to configure "all files of this mime type have this icon".

It doesn't seem like it's currently possible outside of manually inserting graphics files into your file system at specific locations relating to your current theme (I didn't try this method, seems like a kludge to me and gets wiped out on certain updates).  I did hours of reading on the subject and came up with nothing which worked and certainly nothing as simple as the goal.

I discovered that in previous versions of GNOME there was a package called Control Center Plus which included a section 'Advanced' and in there was a capplet for File Types and Programs which apparently included a GUI method for assigning an icon to a particular type of file.  I can't find any current version of this package, even the source I found looks very deprecated and I didn't risk trying to install it.

There was one promising method which hasn't yet worked for me, maybe I'm doing it wrong or maybe it doesn't work with GNOME 2.22.  Basically you just copy a png or svg file into ~/.icons/ with the naming convention gnome-mime-*mimetype*.png (eg gnome-mime-application-x-bitorrent.png).  This is the first file type I've been trying to make work.  Nautilus reports the mime type so I'm assuming (maybe incorrectly?) that the mime type is properly configured in the system; it would have to be by default because I haven't changed any mime type settings in my system.

Simple question, but nobody has the answer?  Here's hoping it's not in a FAQ somewhere (which I missed)! :confused:

Thanks!

---

### Post by johnconnor on 2008-05-23
[http://www.kdau.com/projects/assogiate/](http://www.kdau.com/projects/assogiate/)

I never used it so I don't know if it works well

---

### Post by gnivler on 2008-05-23
> **johnconnor said:**
> [http://www.kdau.com/projects/assogiate/](http://www.kdau.com/projects/assogiate/)

I never used it so I don't know if it works well

Very nice find, that's exactly what I was thinking, an application to implement what is lacking in the gnome interface.  Unfortunately it doesn't seem to work with this version of gnome/Ubuntu, it claims to be changing things and even runs gtk-update-icon-cache but it has no effect in my testing, which may be flawed.  The author's site doesn't seem to have any current updates or information on which versions of gnome would be supported, might send him an email to see.  Thank you for the reply/info.

---


---
title: "Mime types in Gnome/Ubuntu"
date: 2005-02-12
forum: Desktop Environments
---

### Post by stoffe on 2005-02-12
Hello, got a few files from a friend in a package, one of which was a file with the extension .url - he's a windows user, so this is some kind of shortcut from windows I think. Anyhow, when I click on it I get this:

> **Cannot open Filename.url**
The filename "Filename.url" indicates that this file is of type "resource location". The contents of the file indicate that the file is of type "application/x-mswinurl". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "application/x-mswinurl", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

And it contains something like this:
> [InternetShortcut]
URL=http://www.some.url.com/


So, I thought I'd try to fix this somehow, more out of curiosity than because of any real needs. I wanted to know where I could set these associations and decide what mime-types goes where, if I could. Or at the very least, find or set the correct extension for "application/x-mswinurl".

Now, I can't find any docs or info on this anywhere. I've been through google and some forums, and going through the menus of my system, not finding anything. I know it could be done in KDE, but here I find nothing. Any pointers appreciated. Running hoary btw.

---

### Post by gazum on 2005-02-12
I believe if you will right click on the file and use "Open with", nautilus will associate program you used to open your file with this mime type.

Regarding adding new MIME types, apparently previous version of Gnome included "File Types and Programs" utility that did not make up into Gnome 2.8. New approach explained here
[http://www.gnome.org/~jrb/files/mime/](http://www.gnome.org/~jrb/files/mime/)

For now on you can add new MIME types manually as described here
[http://www.fedoraforum.org/forum/showthread.php?t=26875](http://www.fedoraforum.org/forum/showthread.php?t=26875)
[http://www.au.freebsd.org/gnome/docs/faq2.html#q22](http://www.au.freebsd.org/gnome/docs/faq2.html#q22)
[http://www.freedesktop.org/wiki/Standards_2fAddingMIMETutor](http://www.freedesktop.org/wiki/Standards_2fAddingMIMETutor)

There is a graphical MIME editor that is related to ROX file manager (It is not included into rox-filer package, so you need to install it yourself)
[http://rox.sourceforge.net/phpwiki/index.php/MIME-Editor](http://rox.sourceforge.net/phpwiki/index.php/MIME-Editor)

---

### Post by stoffe on 2005-02-13
Ah thanks, so it is a part of the system temporarily missing, that makes more sense then. :) A good set of links too.

I also just now found this link which may be useful if anyone else have the same problem, I have yet to actually try it but it seems to be easy enough to adapt to an Ubuntu system: [http://www.colleeseum.com/index.cgi/main/freebsd/mini_how_to?id=Internet%20Shortcut](http://www.colleeseum.com/index.cgi/main/freebsd/mini_how_to?id=Internet%20Shortcut). I think the part about checking for running Firefox instances and so on can be ignored, just run Firefox and set how to handle this in your Firefox settings instead.

Seems the practice of including links this way is pretty common, maybe it should be handled something like this by default in a system that wants to play nicely with others?

---

### Post by gazum on 2005-02-13
Frankly, I believe it is much easier to put  a link directly into text of email message than send .url file as an attachment. I think windows creates .url file automatically if you copy link and paste address line into Outlook though.

Anyway, generally speaking about MIME types and Gnome/Nautilus. If you want to associate a custom icon with a newly created MIME type. Create a 48x48 pixels .png image and put it into /usr/share/icons/gnome/48x48/mimetypes/ folder.  The file should be called like gnome-mime-application-newmimetype.png. For x-mswinurl the name of the file should be gnome-mime-application-x-mswinurl.png.

---

### Post by stoffe on 2005-02-13
[QUOTE=gazum]Frankly, I believe it is much easier to put  a link directly into text of email message than send .url file as an attachment. I think windows creates .url file automatically if you copy link and paste address line into Outlook though.[/QUOTE]

Hehe, I have no idea. The way I usually get these is when getting something via FTP from friends, I suppose they are including a simple internet shortcut for more info about whatever may be in the directory or archive. I don't think I know anyone who uses Outlook, and even then I think the link is shown correctly inline in the message body in most mail programs.

Also, like I said, it is no biggie for this particular issue, however it might be a bigger issue next time somethings not right with the mimetypes, and that's what really got me to ask in the first place. :)

---


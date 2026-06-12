---
title: "Text Editor"
date: 2005-08-10
forum: Desktop Environments
---

### Post by pailhead on 2005-08-10
Does anyone know if there are any text editors for GNOME that are similar in features (with a GUI) to UltraEdit in windows?  One of the features I would like is the ability to have built in FTP, I haven't found one yet so I thought I'd ask. 

Anyone?

---

### Post by mctavish on 2005-08-10
My crystal ball tells me you will waste many frustrating hours trying and discarding editors, and end up with a hollow disappointed feeling.

Here are some you could look at. None are specifically gnome or gtk2.

scite - i use this
nedit - ugly. Not sure if tabs have made it to the release version yet. I was using the development version for a while which has them.
jedit - java based, featureful - might be a good option.
kate - kde though, so you will need kde libraries I guess.

Don't know about the ftp though. In unix land the mentality is usually to stick to one function - ie text editing, rather than swiss army knife style.

---

### Post by C38a7r1zvl on 2005-08-10
Well, when using kate under KDE you can use kioslaves of all kind to directly access remote files. ftp:// for ftp, smb:// for samba, fish:// for scp and so on. But as mctavish pointed out this would most likely lead to loads of dependencies.

---

### Post by Lux Perpetua on 2005-08-10
[QUOTE=pailhead]Does anyone know if there are any text editors for GNOME that are similar in features (with a GUI) to UltraEdit in windows?  One of the features I would like is the ability to have built in FTP, I haven't found one yet so I thought I'd ask. 

Anyone?[/QUOTE]
 There's always Emacs...I don't know if it has FTP specifically, but it has loads of available extensions and is scriptable (Emacs-lisp). It does sort of have a learning curve, but I've found it fun to work with. One more thing to look into.

---

### Post by void_false on 2005-08-11
I could never understand WHY THE HELL you need FTP in text editor???

---

### Post by Cyberkef on 2005-08-11
[QUOTE=pailhead]Does anyone know if there are any text editors for GNOME that are similar in features (with a GUI) to UltraEdit in windows?  One of the features I would like is the ability to have built in FTP, I haven't found one yet so I thought I'd ask. 

Anyone?[/QUOTE]
[http://www.screem.org/features.php](http://www.screem.org/features.php)

But I still prefer Gedit+gFTP

---

### Post by Stormy Eyes on 2005-08-11
[QUOTE=void_false]I could never understand WHY THE HELL you need FTP in text editor???[/QUOTE]

Nor do I. Just fetch the file, edit it, and send it back. I recommend Gvim, by the way (apt-get vim-gnome), because I grew up using vi as my $EDITOR. There's a bit of a learning curve to it, though.

---

### Post by pailhead on 2005-08-11
[QUOTE=void_false]I could never understand WHY THE HELL you need FTP in text editor???[/QUOTE]
 Because you can open the file via ftp remotely in the text editor.. edit it and when you save it's automatically updated on the server.  That way I don't have to have gFtp open grab the file open gedit, then edit it save it, then switch back to gFtp and upload it.  It's all done in one easy step, which for me keeps productivity up.

I used to do it the old way.. now I use uedit when I'm in windows...

---

### Post by varunus on 2005-08-11
Just a quick tip.  If you go to Places->Connect to server, choose FTP with password or Public FTP or whatever, and connect to the FTP server that way, gedit will be able to directly edit files from it.  (This is called Gnome-VFS.)

---

### Post by pailhead on 2005-08-11
Ahh sweet.. Then that is what I'm looking for.. much appreciated of the tip Varunus!

---


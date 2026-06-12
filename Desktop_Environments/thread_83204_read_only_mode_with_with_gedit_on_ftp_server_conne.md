---
title: "read only mode with with gedit on ftp server connection"
date: 2005-10-28
forum: Desktop Environments
---

### Post by noskule on 2005-10-28
hi all

If I connect to a ftp server via Places/conntect to Server and open a file with gedit the files are allways "read only" . Is there a way to change that, so that I can edit the files? Bevor i had a kubuntu installation and this was working fine with konqueror/kate, so the problem cant be the ftp server.
Does someone has a suggestion?
thanx nos

---

### Post by frenkel on 2005-10-28
Gedit (or gnomevfs) doesn't support this yet. I couldn't get this to work either on Gentoo. :(
However KDE's kioslaves does support this, so that's why it works in KDE.

---

### Post by noskule on 2005-10-28
oh, very bad. :(  I wanted to change to gnome cause of its not so overfilled like kde.

Now I did install kate, and it works without problems. But it seams that this is restricted to applications with kioslave support. Is this correct? Or is there a solution to install "somthing" this works with all applications, or at least with a texteditor, Inkscape and gimp?

Does gnome support a similar feature in near future?

---

### Post by frenkel on 2005-10-28
Yes, that's correct, only applications wich support kioslaves can use this function. I don't know when Gnome is going to implement/support it, but it's been this way for more than a year already IIRC. So I don't think is is important to them.
You might contact a developer or ask in their IRC channel. If you do, please post their answer here :)

---

### Post by scubasteve657 on 2008-02-29
This can be fixed quite easily:
   1. Run gconf-editor
   2. Open the tree to /apps/gedit-2/preferences/editor/save
   3. Edit writable_vfs_schemes
   4. Add ftp to the list

---


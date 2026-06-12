---
title: "vim with Nautilus and smb://"
date: 2007-10-03
forum: Desktop Environments
---

### Post by jsilve1 on 2007-10-03
Has anyone gotten Vim (specifically gVim) to work transparently with network URLs?  For example, using gedit, I can do this:

1) Browse in Nautilus to a SMB network share, "smb://server-name/sharename"
2) Right-click a text file and choose "Open with Text Editor" (which opens the file in Gedit)
3) make changes in gedit, and SAVE. That's the important bit -- Gedit has built-in Gnome network transparency and will save to SFTP:// URLs, SMB://, [FTP://,](FTP://,) etc.

But if you substitute "Gvim" for "Gedit" in the above steps, IT DOES NOT WORK. In fact, Gvim will not even open the file, and says something similar to:

"smb://vmware@vmware-server/www/TextFile.txt" [New DIRECTORY] 0,0-1         All

It thinks the file name is a "New DIRECTORY". WTF?

A few years ago there was a gnome-vfs plugin or component being built for Gvim but that appears to have died. ([http://www.opensky.ca/~jdhildeb/software/gnome-vim/](http://www.opensky.ca/~jdhildeb/software/gnome-vim/))

Heeeeellllp!!

Thanks!

---

### Post by rudysanford on 2008-06-10
Did you ever find a way to work around this?

---


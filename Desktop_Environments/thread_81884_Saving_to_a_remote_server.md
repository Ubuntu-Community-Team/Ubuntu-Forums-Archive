---
title: "Saving to a remote server"
date: 2005-10-25
forum: Desktop Environments
---

### Post by dizzy1234 on 2005-10-25
Hi,

I'm trying to edit some stuff on a remote server without much luck. I'm logging onto the server using SSH and can upload and download without a problem. However, if I open and edit a file, the editor (I've tried Screem and SciTE) is having trouble saving to the server and giving me this error message:

"Could not save file '/home/nick/sftp:/nick@SERVER/home/nick/public_html/DIR/FILE.php'. Save under a different a name?" Yes/No

Obviously I've change some names and stuff, no offence.

Any idea what to do?

Cheers
Nick

---

### Post by flower on 2005-10-25
if the case is you can install stuff on the remote machine better use nfs.
this way you'll avoid editor's problems - the editor will not make difference between the local and remote files ;)

---

### Post by David A Knight on 2005-10-25
With screem you can work via ssh in a number of ways.

1) Places->Connect To Server  from the gnome panel.  Screem will show these in the open file dialog
2) Have a nautilus window open at an sftp location and drop the file onto the main Screem window (not the editor part or the url will be inserted)
3) File->Open Location from in Screem.  sftp://user@host/path/to/file
4) start Screem from the command line as     [FONT="Lucida Console"]screem sftp://user@host/path/to/file[/FONT]

same for working with a site in screem, which would then give access to all the files in the top level project folder in the file pane.

---


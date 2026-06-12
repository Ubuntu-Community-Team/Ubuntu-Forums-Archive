---
title: "OpenOffice-GVFS opening documents from smb/sftp/... mounts"
date: 2009-08-03
forum: Desktop Environments
---

### Post by bkortleven on 2009-08-03
We have been experiencing a problem when opening OOo files through samba shares on Ubunut 9.04

What happens is as follows:

1. Opening an smb located file when OOo is opened:
a. Open OOo
b. Go to File-Open
c. the selection list and Places bar are as it should be, displaying the same content as in Nautilus
d. opening a gvfs-mounted share (both smb and sftp tested), content and files displayed correctly
e. when opening a file, the Open-dialogue closes, and the OOo screen stays empty, file doesn't open.

I did the same with soffice started through console, and I got this message when clicking the Open button after selecting a file:

```
(soffice:31259): GLib-CRITICAL **: g_filename_to_uri: assertion `filename != NULL' failed
```


2. Opening a document from Nautilus
a. open nautilus
b. browse to a smb/sftp based folder
c. doubleclick on a document to be opened
d. the OpenOffice 3.0 splash screen is displayed
e. nothing else happens... the splash screen disappears again, nothing else...


When doing all these locally, all works.
I tried copying the files to my Home folder, no problems.

Is there an update on this?
Any way to get this working again?

Thanks for sharing ;)

---

### Post by rhy7s on 2009-12-15
I get a similar error on Ubuntu 9.10. Opening a bookmarked share in Nautilus which I assume is mounted via GVFS works fine. Opening images in EOG or text files in gedit works fine. Trying to open .doc, .docx or *.odt files in OO.o 3.1 just results in a new empty untitled file. In a similar vein, SMPlayer and VLC won't open files from smb links either. Any clues beyond having to mount directories manually would be appreciated. Edit: installing gvfs-bin and a restart, now both vlc and OO.o are working as expected.

---

### Post by natxoo on 2010-02-26
I've solved it installing gvfs-fuse package. This make openoffice use fuse an automagically 'copy' in /home/user/.gvfs

---

### Post by maxxer on 2010-02-28
I'm having similar problem, but I *do* have fuse-gvfs installed.

any other infos?
thanks

---


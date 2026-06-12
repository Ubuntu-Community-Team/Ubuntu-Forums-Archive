---
title: "Error &quot;I/O error&quot; while deleting&quot;"
date: 2006-03-21
forum: Desktop Environments
---

### Post by rdking on 2006-03-21
trying to dump some junk off my drive.  Have a folder that has 3 unknown file type and size files in the directory, which show up when I open the folder in nautilus then dissapear (ls in console shows that it is looking for the files but says the don't exist).  Can't dump the file to trash through nautilus  or "sudo rm -R folder".  Even a rm -f fails to do anything.  Can anyone help my try and dump this folder.

Nautilus message is:

Error "I/O error" while deleting "/{path to folder}

ls in console:

ryan@ubuntu:{path to folder} ls
ls: Samp: No such file or directory
ls: txt: No such file or directory
ls: Disccom.: No such file or directory

these are the three files which show up temporarily in nautilus

rm -R /{directory}:

rm: cannot remove `{directory}': No such file or directory

---


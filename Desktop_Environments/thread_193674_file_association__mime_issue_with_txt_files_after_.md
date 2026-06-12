---
title: "file association / mime issue with txt files after dapper upgrade"
date: 2006-06-10
forum: Desktop Environments
---

### Post by dcymbal on 2006-06-10
After a recent upgrade to dapper, I am noticing this issue:

Double-clicking any plain text file with an extension of .txt results in the following popup dialog:

"The filename "foo.txt" indicates that this file is of type "txt document". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. "

If I rename these files to any other extension and dbl-click they open in gedit as expected (and as was happening in warty and breezy).   These are all plain text files.  Any ideas?

---

### Post by meng on 2006-06-10
I've seen this problem described with .txt, .exe, .mp3 and .htm, so far as I'm aware it's only with upgrades not clean installs. You may find that deleting ~/.local will solve the problem, although you then have to reconfigure your preferred apps and menu changes. Also, I am still having a problem with some (not all) .htm files. I don't know if a better fix is planned.

---

### Post by dcymbal on 2006-06-10
[QUOTE=meng]I've seen this problem described with .txt, .exe, .mp3 and .htm, so far as I'm aware it's only with upgrades not clean installs. You may find that deleting ~/.local will solve the problem, although you then have to reconfigure your preferred apps and menu changes. Also, I am still having a problem with some (not all) .htm files. I don't know if a better fix is planned.[/QUOTE]

Thanks for the tip about deleting .local.  That resolved the issue for me.  I have not seen the problem with any other extensions, for me it was exclusively the .txt

---

### Post by JohnST on 2006-11-15
> **dcymbal said:**
> Thanks for the tip about deleting .local. That resolved the issue for me.  I have not seen the problem with any other extensions, for me it was exclusively the .txt

Yes, Thank you very much. I also had the problem with .txt files only. Looking closer at the content of the ~/.local folder, I found a more narrow solution:

Delete the line
"application/x-extension-txt:*.txt"
in the file
~/.local/share/mime/globs
Then restart nautilus and the problem is gone.

My experience is that that a bad shutdown can cause this issue.

---


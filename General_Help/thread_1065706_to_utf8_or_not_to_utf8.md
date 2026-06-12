---
title: "to utf8 or not to utf8"
date: 2009-02-10
forum: General Help
---

### Post by SteveHillier on 2009-02-10
Apologies if I am showing great ignorance.
Following an issue I was trying to resolve yesterday I posted an thread on how to permanently mount shared NTFS folders.
Many kind people had shown me the light and now I have a folder mounted on start up.
The program I am trying to use is installed on a Vista box and a Ubuntu box with data being on the shared Win 2003 folder.
I created the files on Ubuntu.  I successfully copied them to the Win 2003 folder and accessed them from my Vista box.  I can add new records and close and restart without issue from Vista.
Having now set up Ubuntu to mount the drive and set up the path correctly I can now start to access these shared files from Linux.
However the program reports an error and corrupts the database - remember this is a database that was created by Ubuntu.
I am simply wondering if I was right to add 'iocharset=utf8' in my mount command?  That seems the most likely cause of the corruption but if anyone can help.....
Thanks
Steve
ps.  I have also contacted the program developer just in case it is somewhere in their code.

---


---
title: "bit defender"
date: 2009-06-21
forum: General Help
---

### Post by philcamlin on 2009-06-21
ok i know this is probably a stupid question but i use bit defender to cleanup any viruses my grandma runs in wine 

aparently any av in ubuntu is a windows only thing 

can i repair the i/o errors or will it beatup my grandmas machine i dont want to screw it up:popcorn:

or is a virus checker thing totally useless

sorry ive never used windows and never plan to, too meny viruses

[[IMG]http://img36.imageshack.us/img36/7897/screenshotwux.th.png[/IMG]](http://img36.imageshack.us/i/screenshotwux.png/)

---

### Post by mike555 on 2009-06-21
I believe those errors are because the scanner couldn't open certain files to scan them, a permission thing .........

---

### Post by jimv on 2009-06-22
A) Why does she have WINE?

B) Why not use a native AV like ClamAV or Avast?

[http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

---

### Post by Wiebelhaus on 2009-06-22
> **jimv said:**
> A) Why does she have WINE?

B) Why not use a native AV like ClamAV or Avast?

[http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

Bit Defender does support linux ya know..



From support:

> The BitDefender scanning engine includes the number of I/O errors in the Statistics section of the scan report. An I/O error is counted everytime the scanning engine is denied access to a file. The files for which an I/O error is returned include the operating system files, the files in use, and the user-protected files.

    * Operating system files: The files are in use by the Windows operating system and the scanning engine is permanently denied access to them. For example, the paging file used for storing the system virtual memory is inaccessible to the antivirus.
    * Files in use: The files are in use by other software and the scanning engine is temporarily denied access to them. For example, using an editing software during a scan will deny the access to the files opened in the editing software. Closing the editing software before starting the scan will allow the scanning engine to access these files.
    * User-protected files: The user initiating the scan is denied the access to the files. For example, although a user is allowed to scan the files contained in her home folder on a file server, she will not be able to scan the files from the other users' home folders stored on the same file server.



Basically I/O error is computer terminology for "unable to read/write"

---

### Post by munky99999 on 2009-06-22
[http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html](http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html)

---

### Post by jimv on 2009-06-22
> **Wiebelhaus said:**
> Bit Defender does support linux ya know..



From support:



Basically I/O error is computer terminology for "unable to read/write"

Ah, I thought he was trying to run it in WINE :P

---

### Post by philcamlin on 2009-06-22
no its all good it was permission things thank god :) 699 viruses or whatever :popcorn: id crap myself

i dont like wine because it doesnt work for most things 

thanks to all who helped

---


---
title: "Filenames on CD-ROM"
date: 2006-01-17
forum: General Help
---

### Post by pbb on 2006-01-17
I've got a few files on a CD-ROM (burned under Windows) that I cannot read or copy to harddisk, appearantly because of unsupported characters in their filenames.

Using "sudo mount -o utf8 /media/cdrom0" I was able to get most of them copied, but now I am still left with one file that cannot be copied.

How can I get to this file???

---

### Post by pbb on 2006-01-17
No ideas?

---

### Post by pbb on 2006-01-19
Please, anybody? Is this such a weird problem?

---

### Post by z_diver on 2006-01-19
Are you sure it's the filename that is causing the issue?  Are you able to make a copy of the entire CD?  Try that and then try to copy the file from the new CD to HD.

Usually Linux/Unix is able to use all the characters that Windows uses and then some, so I've only seen the oposite problem.  Was the original CD created using an English only installation of Windows or was there another language involved.

---

### Post by taurus on 2006-01-19
What is the exact name of the file that you can't copy over???

---

### Post by pbb on 2006-01-20
Okay, feeling stupid again... It was actually a problem caused by Nero on the Windows-machine where I burned the CD. My mistake was that I didn't check the CD under Windows, I just checked the original files that were still on the Windows harddisk.
The filename contains a 'character' of which the hex-code is 0F. Guess not many filesystems will support that. The funny thing is that under Windows, it just shows as a square box, and you can do anything with the file you want. On the CD it shows as a question mark, and the file is unreadable.

Wise lesson #1: Don't blame Linux too fast :-)

---

### Post by z_diver on 2006-01-20
That is interesting.  I've seen Winders 2000 servers that were hacked by Unix/Linux guys and they'll name the files in a way that nothing you do from the native OS will remove them.  Years later and they are still right there.

---

### Post by pbb on 2006-01-21
No, this was the other way around. It was a very invalid filename, but XP didn't have any problems with it. XP could open, copy, delete, anything. But Linux didn't know what to do with it!

---


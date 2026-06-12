---
title: "how to securely delete email"
date: 2005-11-29
forum: Desktop Environments
---

### Post by seatea on 2005-11-29
I  have  just recently stated using Linux and the email program Evolution. I would prefer to securely delete my email  as I go along rather  than just emptying the  Trash and worrying that I need to "scrub" my hard drive at some point in the  future so no one  will be  able  to recover any of my professional information. Is there  a way to do this? Also, can the Trash in GNOME be securely deleted rather than  just emptied?

---

### Post by dcstar on 2005-11-29
[QUOTE=seatea]I  have  just recently stated using Linux and the email program Evolution. I would prefer to securely delete my email  as I go along rather  than just emptying the  Trash and worrying that I need to "scrub" my hard drive at some point in the  future so no one  will be  able  to recover any of my professional information. Is there  a way to do this? Also, can the Trash in GNOME be securely deleted rather than  just emptied?[/QUOTE]
In Evolution, "deleting" email just tags it, you have to "Expunge" a folder to permantly delete the data.

---

### Post by seatea on 2005-11-30
How can I Expunge the  Trash folder for Evolution?

---

### Post by nocturn on 2005-11-30
Are you talking about wiping files?

You cannot do this from evolution (or any other app).  
You can use shred, wipe or bcwipe from the command line, but they do not function fully on journalling filesystems like Reiserfs and Ext3...

---

### Post by seatea on 2005-11-30
Yes, I am talking about  wiping files. If shred, wipe and bcwipe don't work fully on Linux, then I guess that  the only alternative  is to use something like  "Darik's Boot and  Nuke" when it comes  time  to sell/dispose of my computer?

---

### Post by nocturn on 2005-11-30
[QUOTE=seatea]Yes, I am talking about  wiping files. If shred, wipe and bcwipe don't work fully on Linux, then I guess that  the only alternative  is to use something like  "Darik's Boot and  Nuke" when it comes  time  to sell/dispose of my computer?[/QUOTE]

Oh, they do work on Linux.  If you use a FAT or EXT2 filesystem.
Wiping is just not fully effective on journaling filesystems, because of the journal itself.  So, this would apply to NTFS too.

When you want to wipe your entire drive, it is a different matter.  All of the above will be very successfull at that (because they wipe the entire disk, the journal is wiped safely too).

---

### Post by dcstar on 2005-11-30
[QUOTE=seatea]How can I Expunge the  Trash folder for Evolution?[/QUOTE]
Either "File-Empty Trash", or select a folder and "Folder-Expunge" (CTRL-E) from the menus.

---

### Post by seatea on 2005-12-01
How does Expunge differ from Empty-Trash?

---

### Post by dcstar on 2005-12-01
[QUOTE=seatea]How does Expunge differ from Empty-Trash?[/QUOTE]
Don't think there is a difference when used on the Trash folder.

---

### Post by HermanAB on 2005-12-01
Hmmm, I think you are approaching the privacy issue wrong.  What you need to do instead is encrypt your /home, /var and /swap partitions.

---

### Post by nocturn on 2005-12-01
[QUOTE=dcstar]Don't think there is a difference when used on the Trash folder.[/QUOTE]

The Trash folder is not a real folder.
Deleted messages are marked as deleted in their own  folders, Trash is just a filter to list them.

expunge folder removes all deleted messages in that folder, while empty-trash removes all deleted messages in all folders.

---

### Post by arnieboy on 2005-12-01
[QUOTE=nocturn]The Trash folder is not a real folder.
Deleted messages are marked as deleted in their own  folders, Trash is just a filter to list them.

expunge folder removes all deleted messages in that folder, while empty-trash removes all deleted messages in all folders.[/QUOTE]
never mind.. didnt read the whole thread..

---

### Post by anthro398 on 2005-12-01
I posted some thoughts on this topic on the Suse forum that you might find interesting.  See [http://forums.suselinuxsupport.de/index.php?showtopic=17430&hl=]("http://forums.suselinuxsupport.de/index.php?showtopic=17430&hl=").
I also use the dm_crypt module as described in the wiki to encrypt the /zzz partition.  Of course, erasing email on your end does nothing to protect your privacy in the entire rest of the lifecycle of an email so unless you're only concerned about a local attack you'd better start thinking about gpg or similar solutions.

---


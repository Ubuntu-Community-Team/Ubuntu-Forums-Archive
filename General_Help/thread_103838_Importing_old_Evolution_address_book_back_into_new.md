---
title: "Importing old Evolution address book back into new install of Evolution"
date: 2005-12-14
forum: General Help
---

### Post by lillian27 on 2005-12-14
Hello,

As the subject line says, I'm trying to import an old(er) Evolution address book into the current version of Evolution.  The old install is on a separate physical drive, so I have access to all the files in my old .evolution dir.

I've tried using File/Import, then browsing to the addressbook.db file, but the "Next" button in the Import Wizard is never enabled.

Am I going about this the wrong way?  Is there another way to import data from previous installs of Evolution?:confused: 

Thanks!

lillian

---

### Post by cstudent on 2005-12-19
If by chance you still have Evolution running on the old drive and can still open it. A slick way to save and import your contacts (address book) is to select all the addresses (ctrl+a) and under the file menu select save as vcard. This will save all the addresses to a single vcard file. Copy the vcard file over to the new drive and open Evolution and chose import as a vcard. 

If on the otherhand all you have is the old files. Try renaming the .evolution/addressbook directory (just to keep it as a backup) and try pasting the old address directory in it's place.

---

### Post by lbarcala on 2007-12-12
I have the same problem. I don't have the old system and to rename and copy the old addressbook directory did not work for me.

Any other solution?

The old addressbook worked with Dapper Drake (updated from Breezy) and now I have a clear new Gutsy Gibbon.

---

### Post by Krydahl on 2007-12-12
I sorted this just the other day - and can't quite remember what I did.

There are evolution directories all over the place.

There's your .evolution directory in home - this includes a sub-directory for you addressbooks. Start by copying the old files back into there.

There's also one in gnome2_private, but for me the one that came with my new install seemed to be the same as the old one. All that's in there is a txt file.

Then there's another directory under /home/.gconf/apps/evolution.

I think what I did was replace those files with the old versions from my previous install. If I recall it also needed a reboot to get evolution to take any notice, though there's probably a better way of getting it to refresh.

---

### Post by vanadium on 2007-12-12
Indeed, that would be the idea. See details here:

[http://ubuntu.wordpress.com/2005/12/03/how-to-backup-evolution/](http://ubuntu.wordpress.com/2005/12/03/how-to-backup-evolution/)

---

### Post by rbmorse on 2007-12-12
I just did this for my Hardy (Ubuntu 8.10 installation). 

There are two files:

/home/username/.evolution/addressbook/local/system/addressbook.db 
/home/username/.evolution/addressbooks/local/system/addressbook.db.summary

I just copied the files from the old install (7.10) to the new (8.04).   You have to restart the session...maybe even the machine (reboot) before evo will "see" the new database files. 

BTW...this will wipe out anything that's currently in the new database, so if you have stuff there you want to keep, use the save as vcard/import single file method described above.  The only problem I had with that is that some fields were not carried over.

---

### Post by lbarcala on 2007-12-13
I had imported mails and tasks yet, so I did not want to begin the configuration. I only want to import the contacts. Finally I did the following:

1) Create one contact list in the new Evolution for each contact list I had into the old version (we can name them as test1, test2, etc.)
2) Create one contact for each of these lists (again, test1, test2, etc.). It will create one directory in .evolution/addressbook/local per list.
3) Exit from evolution.
4) Overwrite each addressbook.db and addressbook.db.summary of .evolution/addressbook/numbers@machine with the ones of the old version. Each file from old version overwrites one differentent file (in different directory) in the new evolution.
5) Restart de computer

This have worked for me.

Thanks

---


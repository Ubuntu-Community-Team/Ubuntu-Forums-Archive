---
title: "Unable to write to disk, Firefox bookmarks and Home folders not working, etc."
date: 2009-03-25
forum: General Help
---

### Post by The_Montgomery on 2009-03-25
Good afternoon,

Just last night, I started experiencing problems with my Ubuntu installation.  I've got 8.10, with the 2.6.27-14 generic kernel installed.

The core of the problem seems to be that nothing is able to write to disk; it's not full, but nevertheless, when trying to copy files from one directory to another, I receive the "Error while copying - There is not enough space on the destination."

Possibly because of this, or because of an unrelated issue, my Firefox bookmarks aren't displayed, the back and forward buttons are greyed-out, my Home subfolders aren't displayed in the "Places" tab on the Main menu, and Pidgin immediately crashes upon login (though running it from the Terminal with automatic login disabled and debug mode allows it to run, at least until I attempt to log in; evidently because it cannot write to disk).  Additionally, I can't save anything.

I haven't yet tried doing a complete uninstallation of Firefox; I can't save my bookmark backups (as I cannot copy files), and I'm not even sure if this is the root cause.

The aforementioned issues started appearing, if I recall, sometime after I uninstalled the default Gnome games.  Reinstalling them evidently didn't help, so I'm not sure if it's a dependency issue or not.

Any suggestions?  Thanks in advance.

---

### Post by evilaim on 2009-03-25
Oh yes, I think I remember this issue, it had something to do with a hidden garbage on the drive.  Look for a .trash in your home folder.  I think that's the issue, I'll search google for a few minutes and post back if you say that isn't the issue.

---

### Post by The_Montgomery on 2009-03-25
There doesn't appear to be any such .trash file or directory.  But thanks, my Google abilities have so far not availed me, hope you can find something.

---

### Post by The_Montgomery on 2009-03-25
Also, I'm unable to uninstall anything via the command line; I'd tried it to see if the disk WAS actually full.

---

### Post by The_Montgomery on 2009-03-25
Ah, okay... maybe the disk WAS full.

Running "df -l" in the Terminal revealed that I indeed had no free diskspace.

I could've sworn I'd done an autoclean and autoremove recently, but evidently not.  Running "sudo apt-get clean" and later "autoclean" and "autoremove" freed up enough disk space that I seem to be back to normal.

But I'll get back to you.

---


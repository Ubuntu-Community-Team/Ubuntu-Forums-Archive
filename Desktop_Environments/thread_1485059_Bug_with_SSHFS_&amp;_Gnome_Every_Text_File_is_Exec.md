---
title: "Bug with SSHFS &amp; Gnome? Every Text File is Executable"
date: 2010-05-16
forum: Desktop Environments
---

### Post by Lucky. on 2010-05-16
EDIT:  Included server and client type.

I'm thinking of filing a bug report, but I'm not sure if I should or not (Never done this before).  Thought I'd try here first.

I recently used SSHFS/Fuse on Desktop Lucid to connect to my Karmic file server like so:

> 
sshfs username@servername:/srv/www /mnt/www


This works great!  I can read/write just fine.  However I get some strange behavior when accessing files over the share.

When I double click on most files (.PDF .ODT .BMP .MP3 etc), the appropriate associated program loads up and opens the file.  However with files containing text (.txt .php .html etc.), Gnome gives me a message saying "Do you want to run blah.txt or display its contents?  blah.txt is an executable text file."

This is consistent for every text-based file, even though the permissions are -rw-rw-r-- (no executable bit at all).

I tested Kubuntu and openSUSE as well:

64 bit Ubuntu(Gnome) = Problem exists
64 bit Kubuntu(KDE) = No problem
64 bit openSUSE(Gnome) = Problem exists

It looks like this may be a Gnome issue.  Anybody else able to duplicate this problem?  Is it actually a bug or a feature?  Should I file the bug with Canonical or file it on Gnome's site?

Thanks!

---

### Post by AlphaLexman on 2010-05-16
What type of file system is formatted? Fat16/Fat32/NTFS? 

I notice on my dual boot system, NTFS (WinXP) and USB sticks (Fat32) that text files are executable.

---

### Post by Lucky. on 2010-05-16
Whoops, I forgot to mention that.

Client is Lucid with ext4, and server is Karmic with ext4.  Both are full systems, no dual booting.

---

### Post by AlphaLexman on 2010-05-16
Note I am still using Jaunty, but I found this: 

System,  Preferences, File Management, Behavior (tab), Executable Text Files:


[LIST]
[*]Run executable text files
[*]View executable text files
[*]Ask each time
[/LIST]

 Note that I have Gnome, KDE and XFCE all installed so you might not have all my options.
Just trying to help.

---

### Post by Lucky. on 2010-05-16
Thanks a bunch!  As you suspected, I couldn't find it exactly the same way with my current configuration.  I found the settings by clicking "Edit->Preferences" while having a file browsing window open.

Again, thanks a ton!  This is a lifesaver of a workaround.  It was driving me batty to edit html files and keep getting prompted each time.

I will try submitting this small bug to Gnome and seeing what they say.

---

### Post by chiwi on 2010-05-17
just to be curious, why haven't you used NFS?

---

### Post by Lucky. on 2010-05-17
That's a great question!  NFS is my ultimate goal, but for now I'm taking baby steps and documenting them.

I tried NFS almost a year ago, but from what I could tell, security was a [pretty big problem](http://ubuntuforums.org/showthread.php?t=1203246) unless I had Kerberos running (If you know of another way, I'd be very interested!)

I started by using Samba, then moved to SSHFS, and after I get this hammered out I think I'll try NFS again with Kerberos for authentication.  With each implementation I learn a little more and become more confident in administration.

---


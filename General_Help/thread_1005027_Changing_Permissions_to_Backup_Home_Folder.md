---
title: "Changing Permissions to Backup Home Folder"
date: 2008-12-07
forum: General Help
---

### Post by sandman3838 on 2008-12-07
Hello All!  ):P

Can anyone help with this one?
I'm trying to recover my UBUNTU 804 HOME folder to UBUNTU 810.

I have my original Ubuntu 804 HOME folder (including it's hidden folders) saved over on my WINXP HD!

1.  I just did a re-install of Ubuntu 810.
2.  I configured/installed drivers for sound, video, and network.
3.  I let the system do an upgrade.
4.  I made two text files using TEXT EDITOR and saved them in my new HOME folder.

	File name=notepad test   	Group=john  Owner=john - John Smith  Permissions= -rw-r--r--
	File name=notepad test2.txt   	Group=john  Owner=john - John Smith  Permissions= -rw-r--r--

These open with no issue.

5.  Next, I went over to C:\SAVED UBUNTU HOME FOLDER  or  (/media/WIN_XP/SAVED UBUNTU HOME FOLDER)
The TXT files here are as follows:

	File name=code notes.txt	Group=root  Owner=root   Permissions= -rwxrwxrwx

These files open up asking for:
	Do you want to run "code notes.txt" or display its content?
	<Run Terminal>  <Display>  <Cancel>  <Run>

Also, I just did some more looking around in my HOME backup folder (/media/WIN_XP/SAVED UBUNTU HOME FOLDER)
even my wallpaper is messed up.  It probably all is?

	File name=Lights.jpg	Group=root  Owner=root   Permissions= -rwxrwxrwx

Is it possible to change or correct everything in my HOME backup folder (/media/WIN_XP/SAVED UBUNTU HOME FOLDER)
ONLY!  Just targetting my Backup Home Folder on the XP HD and still leave my new current HOME folder or everything on my UBUNTU HD alone.

As for anything hidden that's over in that backup folder?  All I can think of getting is .ICONS, .THEMES, and my EVOLUTION EMail folders?  

As usual I can just bet that the real headache here is going to get that Email folders back over?

Anyway, .......  Any suggestions!  :)

---

### Post by Slim Odds on 2008-12-07
How did you "backup" these files?

Simply copying files from linux to windows will **NOT** preserve the file attributes.

---

### Post by sandman3838 on 2008-12-07
Who knew?
I guess I didn't!
Nuts!

I thought if I just un hid the HOME folder and copied them over to another HD that all would be OK.  Keep in mind that I'm moving over from Winxp and it's something that I have done with that OS.

Any suggestions?

Am I   :lolflag:

---

### Post by samuraix51 on 2008-12-08
Yea, copying to Windows won't save the file permissions.
Just an idea, if you have the space:
Make a temp dir on your ubuntu box.
Copy all your files that you backed up on the XP drive to the temp dir you just made.
Then change all the permissions there, then move them to your new home dir.

---

### Post by Slim Odds on 2008-12-08
> **sandman3838 said:**
> 
Any suggestions?

Only for the future....

use a backup utility that preserves the attributes.

tar.gz or zip

---

### Post by Slim Odds on 2008-12-08
> **samuraix51 said:**
> Yea, copying to Windows won't save the file permissions.
Just an idea, if you have the space:
Make a temp dir on your ubuntu box.
Copy all your files that you backed up on the XP drive to the temp dir you just made.
Then change all the permissions there, then move them to your new home dir.

How the heck is he going to know what all of the attributes should be?

---


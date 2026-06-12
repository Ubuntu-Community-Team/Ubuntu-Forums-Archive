---
title: "Prevent accidently deleting folder"
date: 2009-04-23
forum: General Help
---

### Post by GXice on 2009-04-23
I have a folder on the Desktop called "Work" and this folder is important. So much so that my entire computer is dedicated to storing the files written to this folder.

Its on my desktop for ease of access, but I want to prevent the folder from ever being placed in the Rubbish Bin or being deleted by accident. 

Is there a way to set permission to write and read and edit and delete the files inside the folder, but to prevent from actually deleting this "Work" folder itself?

Cheers :)

---

### Post by yeats on 2009-04-23
So... are there others who use this computer?  What makes you think it might accidentally be deleted?  Linux generally assumes that you know what you're doing as far as deleting/moving/managing files, and warnings are minimal by design (on the command line, no news is good news - if it returns to the prompt that means success).  If I were you, I would limit access from other users to your computer...

---

### Post by GXice on 2009-04-23
I'm the only user who uses this computer. However, accidents happen and have happened in the past on Windows. There is no warning message when dragging into the Rubbish Bin on Ubuntu.

I would think this would be pretty easy to accomplish?

---

### Post by chriskin on 2009-04-23
> **GXice said:**
> I'm the only user who uses this computer. However, accidents happen and have happened in the past on Windows. There is no warning message when dragging into the Rubbish Bin on Ubuntu.

I would think this would be pretty easy to accomplish?

draggin into the rubbish bin doesn't erase it , you have to empty the bin as well. this will definitely mean that you want it deleted

as for the original subject, most probably , if you want to be able to write at this folder, i can't think of a way just deleting can be avoided - last time i checked, write and delete was give at the same time with the "write" permission


idea that might or might not work : set permissions inside the folder to read/write but on the folder outside it as read-only and don't click to apply this read-only permission to the subfolders.

---

### Post by yeats on 2009-04-23
Have you considered moving the folder somewhere "safer", then creating a link to the folder from the desktop?  Seems like that would solve your problem...

---

### Post by aloshbennett on 2009-04-23
Instead of putting the folder directly in the Desktop, you can have the directory somewhere else where there is less chance of you going and deleting it.

Create a soft link to the work directory from your Desktop. In this way, you would delete only the link and not the actual directory if you mess around on your desktop.

But be warned that if you go <i>inside</i> the directory soft link and delete a file, then the file is deleted.

PS: oops! Dint see your post, chrissharp123.

---

### Post by GXice on 2009-04-23
> **chriskin said:**
> draggin into the rubbish bin doesn't erase it , you have to empty the bin as well. this will definitely mean that you want it deleted

The folder contains something like 400 GB of information and various projects. I certainly dont want it moving to the recycle bin and back again, accidental or otherwise.

I'll try the idea with permissions, as you've said.

---

### Post by chriskin on 2009-04-23
> **GXice said:**
> The folder contains something like 400 GB of information and various projects. I certainly dont want it moving to the recycle bin and back again, accidental or otherwise.

I'll try the idea with permissions, as you've said.

please try it on another folder first, i do not know if it works they is it meant to work

---

### Post by GXice on 2009-04-23
> **aloshbennett said:**
> Instead of putting the folder directly in the Desktop, you can have the directory somewhere else where there is less chance of you going and deleting it.

Create a soft link to the work directory from your Desktop. In this way, you would delete only the link and not the actual directory if you mess around on your desktop.

But be warned that if you go <i>inside</i> the directory soft link and delete a file, then the file is deleted.

PS: oops! Dint see your post, chrissharp123.

Sorry I didn't notice you guys post after Chris, but this is also a safer bet. I was hoping for some fancy CLI code which I could 'freeze' the folder on the desktop but not the files inside. Guess I'm getting a bit ahead of myself :)

---

### Post by aloshbennett on 2009-04-23
Here's some CLI tips that could help:
If you have a directory structure like

parent-> work -> a.txt, b.xt

parent doesn't have write perms, work has write perms. Then you cannot delete the work directory, but can add/delete contents inside work(flip side, you cannot add contents to parent dir)

---

### Post by callan79 on 2009-04-23
> **GXice said:**
> The folder contains something like 400 GB of information and various projects. I certainly dont want it moving to the recycle bin and back again, accidental or otherwise.


I guess my thoughts here are there's not really any foolproof way to prevent user error (I mean, how can you drag a folder to the garbage bin, accidently??).

My solution is to leave everything as is, but just keep good backups.

Tools such as Grsync or SimpleBackups should help you keep a daily copy of your files. Be it on the same physical disk or different physical disk doesn't matter, you just need to keep a copy.

Personally this is what I have:

HARD DRIVE 1 IN MY COMPUTER - ubuntu and my home directory

NETWORK HARD DRIVE (NAS - 400GB) - all my data
  (note, the NAS is in a separate room, to protect against theft)

HARD DRIVE 2 (500GB) IN MY COMPUTER - every day, Ubuntu takes the data on the NAS, works out what has changed, and puts a copy on this drive.


So, if I were to delete a file on the NAS, or if a file got corrupted, I could restore at any time.

Good luck!
Callan

---

### Post by GXice on 2009-05-21
> **callan79 said:**
> I guess my thoughts here are there's not really any foolproof way to prevent user error (I mean, how can you drag a folder to the garbage bin, accidently??).

User error on my part mostly. I slide the mouse around quite fast and click all over the place. It's sort of like... asking for trouble. Having been a Windows user for so long, it strikes me as bizarre that the Rubbish Bin doesn't have a dialogue box asking "Are you sure you'd like to send this to the Rubbish Bin?" Yes/No.

Anyway, sorry to bump such an old thread, but I played around with permissions a bit and it's all good now. The Parent -> Work -> file.txt idea worked well. Thanks :)

---

### Post by Yellow Pasque on 2009-05-21
Why not just put the actual folder someplace safer and make a link to it on your desktop?

---

### Post by DemonBob on 2009-05-21
For the command line, add an Alias to bash to make rm mean move to trash, like so. 

[http://ubuntuforums.org/showthread.php?t=623656](http://ubuntuforums.org/showthread.php?t=623656)

---


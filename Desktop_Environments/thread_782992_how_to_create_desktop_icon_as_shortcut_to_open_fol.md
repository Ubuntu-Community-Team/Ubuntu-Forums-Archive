---
title: "how to create desktop icon as shortcut to open folder?"
date: 2008-05-05
forum: Desktop Environments
---

### Post by al_mckin on 2008-05-05
Hi everyone,

I think this is probably a stupid question, but I had a look around and couldnt find an answer.

I'm using gnome on hardy and I want to create a desktop shortcut to a directory.  I tried using "create launcher" -> "location" but that seemed to only want to create a shortcut to an executable.

Specifically, I just got my dad to try ubuntu and set up a new hard drive so his computer now dual boots XP and ubuntu.  I want to create a shortcut to his "My Documents" folder on his XP drive.

When I click on the 40.0Gb media icon in the places menu it mounts the drive and sticks a shortcut on the desktop to its root directory.  How do I create a shortcut to an arbitrary folder on the drive, or any other folder on my ubuntu drive for that matter?

I haven't set the drive to automount yet but I here ntfs-config makes life easy for this?  Does that sound right?


Cheers everyone!

Alastair

---

### Post by TheMemphisExperience on 2008-05-05
Yes, NTFS config is a wonder. On my laptop, I have a large Vista partition that handles most of the data and the smaller Ubuntu partition that reads and writes to the Vista partition. So long as Vista is not hibernating, the partition housing all my movies, docs, and music will automount to /media. I've got nifty shortcuts for all my items on the desktop as well.

To create a shortcut to a specific folder, simply navigate to your target folder. Select it and hold CTRL+SHIFT and drag and drop it to the desktop. 

You can drag and drop it to some other folder on your Ubuntu partition if you want(like documents) or just throw it on the desktop for ease of access.

---

### Post by al_mckin on 2008-05-05
Thanks Memphis!

I thought it was something simple like that!  
So I'll try ntfs-config out later on my dads computer.  I take it from your post that you shouldn't mount the ntfs drive if windows is hibernating?

Alastair

---


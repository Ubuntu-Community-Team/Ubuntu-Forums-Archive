---
title: "Unable to chown networked drive"
date: 2005-12-11
forum: Desktop Environments
---

### Post by abyss6 on 2005-12-11
WARNING - Extreme newbie alert!

With that out of the way, I am trying to change the ownership of a networked drive.  Somehow (don't ask, b/c I doubt I could recreate it), I was able to access my music folder on my windows computer.  I am able to view it, but I can't play any files directly.  To play them, I have to open 'File Browser (Root)'.  I would like to be able to play them without having to do that, so I thought that changing the ownership would do it.  In FB(R), when I try to change the permissions, it doesn't let me.  Likewise from a terminal window.  What can I do?  Thanks.

EDIT: I don't know if it matters or not, but I meant to post this in the Gnome forum.  Sorry.

---

### Post by Zelut on 2005-12-11
Ok lets see if we can figure this out with a little more information...

You're connecting to a seperate computer on the network using _______?  (ie; how did you set this up?)

You say you can view the files but not play them?  Can you edit/rename them?

You may want to check out [GNUmp3d]("www.gnump3d.org") as a home streaming music player (for both windows & linux).  This is what I use to share my collection between my three home computers.

---

### Post by abyss6 on 2005-12-11
The two computers are connected on my LAN.  

I went into Places and then Connect to Server.  The type of server is "Windows Share" and typed in the pertinent information.

Now either before or after this (I can't remember), I used Samba to link the two computers.  All of the files in my music directory are in "/mnt/win".  This is how I view the files in FB(R).

I also tried to mount the networked drive automatically ([http://ubuntuguide.org/#automountnetworkfoldersall](http://ubuntuguide.org/#automountnetworkfoldersall)) - I think this is how the files are showing up in "/mnt/win".

I know this isn't chronologically correct, but I wanted to get down everything I did.

EDIT: I can rename files and I can open .txt files, but not .mp3 files.

---

### Post by abyss6 on 2005-12-11
I was able to fix my problem by remounting it in a different place with full permissions.

I know just enough about this to screw something up or do something right and have no idea how I did it.  Guess I'll just have to play with it some more.  Thanks for the help.

---


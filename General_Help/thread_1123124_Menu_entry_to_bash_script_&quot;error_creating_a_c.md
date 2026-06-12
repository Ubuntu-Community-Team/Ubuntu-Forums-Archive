---
title: "Menu entry to bash script: &quot;error creating a child prcess for this terminal&quot;"
date: 2009-04-11
forum: General Help
---

### Post by Nathanael Culver on 2009-04-11
[Not sure if this is the right forum]

I've been playing around with EncFS, and following a tutorial from [Life in X]("http://xlife.zuavra.net/") [here]("http://xlife.zuavra.net/index.php/66/"). The author has written a shell script called [enc]("http://xlife.zuavra.net/files/posts/0066/enc") which simplifies mounting and unmounting encrypted folders using the EncFS utils. The general syntax for enc is:

enc /path/to/encrypted/folder/ /mount/point/

it then prompts for a password and mounts the folder.

Everything works from the command line, however, I'm trying to simplify things further by creating a Gnome menu entry I can click on to run enc, and just enter the password. If I type an enc mount command in a terminal, such as:

~/enc /media/sdcard1/encrypted/ ~/decrypted/

then enter my password, the folder is mounted. However, if I copy and paste the same command line into the Command line of a menu entry, I get a "There was an error creating the child process for this terminal" error when I try to run it (I've set the entry to Application in Terminal; otherwise I never see anything).

What am I not understanding? Or is there another way of accomplishing the same thing?

--Nathanael Culver

---

### Post by Nathanael Culver on 2009-04-12
bump

---

### Post by Linteg on 2009-04-12
Try using the full path, e.g.: /home/user/enc ... instead of just ~/enc

---

### Post by Nathanael Culver on 2009-04-12
Thanks for the suggestion. Already tried that. Also tried selecting/deselecting the "Application in Terminal" option, and enclosing the whole command line in quotes. No go. I'm also copying and pasting the command from a terminal, so there's no chance of a typo.

--Nathanael Culver

---

### Post by Nathanael Culver on 2009-05-23
[Can't figure out how to mark the original post SOLVED]

Problem solved (or rather superceded) by Tom Morton's excellent [Cryptkeeper]("http://tom.noflag.org.uk/cryptkeeper.html") (currently at version 0.9.3) which does all I was looking for and more. It puts a little icon in Gnome's system tray. Left click it, select the (pre-configured) encrypted folder, supply password, and it's mounted. Slick.

Nathanael Culver

---


---
title: "cant rename files."
date: 2005-07-13
forum: Desktop Environments
---

### Post by DarkManX4lf on 2005-07-13
i cant rename files for some reason, i am logged in as root, when i try to rename a file, i right click on the file and then click rename and after like 3 seconds it just wotn let me rename....normally when you rename a file, you right click t hen click rename and then you rename it and then click somewhere or press enter and its renamed....well for me when i right click and then click rename, 3 seconds later its like it  automatically pressed enter......how do i fix this?

---

### Post by rmjokers on 2005-07-13
One thing to remember is modification of a file name requires write permission for the directory containing the file.  This is the inode where the filename is actually stored.

A few things you might want to check on are:

[list=1]
[*]Make sure the file you are modifying is not on a network drive.  If it is, some of the permissions you see might be masked off at the fileserver.
[*]Look as the permissions of the directory containing the file.  Does root have write permissions on this directory?
[*]Try renaming the file from the command line.
[/list]

---

### Post by poptones on 2005-07-13
Are you using hoary? There was some sort of bug in it initially that would cause this but I have not noticed it lately. Have you applied all the available updates?

---

### Post by DarkManX4lf on 2005-07-13
yea im  using hoary, the permissions were already set, but the problem still occurs.

---

### Post by alastair on 2005-07-13
Get a shell, and try and "sudo mv <old> <new>".

If this works, there's a GUI bug somewhere. But the GUI's for wimps, right? :-)

---

### Post by DarkManX4lf on 2005-07-13
the terminal way is good but, the problem is im renaming mp3 files, i name my mp3s a certain way

(Artist Name) - Song Name.mp3

so renaming 20files in terminal kinda sucks

---

### Post by varunus on 2005-07-13
This is apparently a glitch in nautilus, the workaround:
Highlight the file and press F11, this will let you rename it.  Some people have complained of nautilus not letting them click to rename.  What mouse do you have?

---

### Post by alastair on 2005-07-13
Perfect opportunity to learn shell scripting, or Perl, or Python etc. Or even "man rename". You won't regret it - much more fun (and future-proof) than "learning" how to use "F11" :-)

---

### Post by dewey on 2005-07-13
If you want to rename mp3s like that, there's a *gasp* windows tool to do it for you, called The Godfather.  It should automatically rename all your mp3s, ogg, mpc, ape, flac, aac, apl, wv, mp4, ofr, or spx  to the artist - song format, with extremely little input from you, and it's very accurate.
I'm not sure if there's a program similar to it for linux, or if you could run it under wine, but download it here:
[http://users.otenet.gr/~jtcliper/tgf/](http://users.otenet.gr/~jtcliper/tgf/)

---

### Post by poptones on 2005-07-13
If you will install mp3info and spend about an hour learning to use it you won't regret it. You could rename all 20 of those files from the tag info using mp3info with one failry simple command line. Spend an hour now, rock into eternity :)

---


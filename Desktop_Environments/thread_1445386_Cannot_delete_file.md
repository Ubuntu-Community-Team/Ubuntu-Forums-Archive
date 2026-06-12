---
title: "Cannot delete file"
date: 2010-04-02
forum: Desktop Environments
---

### Post by pac-man on 2010-04-02
Hi guys, I have a folder that is hard (impossible) to delete, it's not about permissions, what happens is that the system tells me this file does not exist at all, but I see the icon there.

Something curious is that this file has a little black square with a "?" inside, I have another file (in the trash can) with this questionmark and guess what.. I cannot delete it either.

I tried logging in directly to the terminal and tried to rm -R and same thing happens, it says file does not exist.

I am using kubuntu 9.10, this is a screenshot of the problem, hope you got a solution for this.

Thanks!

[IMG]http://o.imm.io/fJ0.jpg[/IMG]

---

### Post by 3Miro on 2010-04-02
I had this happen to me once, but I don't remember what exactly fixed the problem. If terminal doesn't help, you can try:

- switching off the graphics (Ctr + Alt + F1, but save everything that you are doing). Try deleting this in pule console mode.

- install Nautilus and/or Thunar, those are the default file managers for XFCE and Gnome and they may do what Dolphin cannot. You can also try Krusader and other such options.

- You can try booting from a live CD and use KDE or Gnome directly from the disk. This should do the trick.

I hope one of those works for you.

---

### Post by ajgreeny on 2010-04-02
Is this a mount folder of an iso file, or something similar?

If it might be, try right clicking and unmounting.  I may be quite wrong, but it is a possibility, and something that I had happen to me as long time ago.

You could also just reboot, and if it's a mounted file or folder it should disappear.

---

### Post by 2hot6ft2 on 2010-04-02
Looks like it may be an invalid name. Might try renaming it first then try deleting it.

---

### Post by nem75 on 2010-04-02
The problem seems to be the unknown character in the filename (encoding problem). You can remove the file by its inode number. Here's a nice howto:

[http://www.cyberciti.biz/tips/delete-remove-files-with-inode-number.html](http://www.cyberciti.biz/tips/delete-remove-files-with-inode-number.html)

---

### Post by 2hot6ft2 on 2010-04-02
> **nem75 said:**
> The problem seems to be the unknown character in the filename (encoding problem). You can remove the file by its inode number. Here's a nice howto:

[http://www.cyberciti.biz/tips/delete-remove-files-with-inode-number.html](http://www.cyberciti.biz/tips/delete-remove-files-with-inode-number.html)
Nice find. Bookmarked for future reference.

---

### Post by pac-man on 2010-04-13
I tried to remove it using the inode number, but it replies that it cannot be deleted because it is a folder and not a file.

Note: renaming, replacing, copying, moving, changing permissions, properties or whatever I want to do with this folder is impossible.

---

### Post by Monsieur Gonzalez on 2010-04-13
Hi!
This has happened to me too. I guess something is wrong with the original file encoding. Anyway, what I do when this happens is go to the folder (Descargas in this case) and press f4. That'll bring the terminal window.
In the terminal window : 

1 - write "rm -rf" - but don't press enter yet!!!! Now write "Adam" and press Tab button for auto-completion of the folder name. 

2 - Double check that's the folder you want to delete. Once you press Enter there's no (easy) going back. Press Enter and (hopefully) the folder is gone. 

As to where the problem lies, I cannot really tell, it's only happened to me with some downloaded files.

---

### Post by deconstrained on 2010-04-14
What is the type of filesystem that the files you can't delete are on? I've run into this exact same problem before on a JFS volume. You may need to specify to use UTF-8 character encoding in the mount options. Once you do, the problem will be gone.

Open up kterm and enter "man mount". Then press / and type in the name of the filesystem type to search the man page for mount options specific to it. Look for something like "utf8" or "iocharset=utf8". Then, put that in the "mount options" column of your /etc/fstab entry that corresponds to the volume that the files you can't delete are on.

---

### Post by ali_etoom on 2010-04-14
Change the name ur using special character that mean something to the shell or use root privileges by issuing nautilus.

---

### Post by pac-man on 2010-04-24
@Monsieur Gonzalez: Tried that, but when I type the first letters of the folder Adam..bla bla and tap the tab key, nothing comes up, because for the system that folder does not exist at all (even though it is there). However, I didn't know that F4 popped out a terminal inside the nautilus windows, very useful thanks for the tip :)

@Deconstrained: it is EXT4

---

### Post by Monsieur Gonzalez on 2010-04-24
Ok, so, very carefully, and checking that you're in the right directory (the one called Descargas), fire up the terminal (f4) and type "rm -rf Adam*" (*do not type the " *).

By the way, the file manager is not called Nautilus (Gnome) but Dolphin (KDE SC).

Good luck.

---

### Post by rich1842 on 2012-07-31
This really does work! 

'gksudo nautilus /home/carl/Desktop/' --- example - takes you to where your file/folder is.

[http://ubuntuforums.org/showthread.php?t=1123479](http://ubuntuforums.org/showthread.php?t=1123479)

That's where I got it.

---

### Post by wildmanne39 on 2012-07-31
Hi, this is an old thread so it has been closed, thanks for sharing.

---


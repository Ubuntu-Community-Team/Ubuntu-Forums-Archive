---
title: "How do I remove a link made in Gnome?"
date: 2006-03-05
forum: Desktop Environments
---

### Post by MetalMusicAddict on 2006-03-05
I found out that I could make a link to a file/folder in Gnome by middle-clicking and dragging it to where I want. Cool, it worked. But... um... how do I remove the link?

I made the link from a networked folder to my desktop and now it says something like "Error:"Not on the same filesystem". What is that?

---

### Post by incubus on 2006-03-05
Not sure if that's a symbolic link, but if it is:
$ rm -f <filename>

should do.

The link should be in your ~/Desktop directory, I'd guess.

incubus

---

### Post by MetalMusicAddict on 2006-03-05
The icon is a folder with a arrow on it. Looks like a symlink. In properties under "Type:" it says "link to folder' Im kinda scared that it will delete the real folder from the other PC now.

---

### Post by Sutekh on 2006-03-05
It looks like it, but this is how I would check, use the terminal

This is what a symbolic link looks like
```
user@ubuntu:~/Desktop$ ls -l
...
**l**rwxrwxrwx 1 user user 22 2006-02-12 16:12 **[COLOR="Cyan"]My Music[/COLOR] -> [COLOR="RoyalBlue"]/mnt/multimedia/Music/[/COLOR]**
...
user@ubuntu:~/Desktop$
```

The **l** and **->** are the giveaway

---

### Post by MetalMusicAddict on 2006-03-05
Yea, the 2 links in the screen have a **->** in the output.

So **sudo rm -f ~/Desktop/Audio** worked. Thanx all. ;)

---

### Post by AirIntake on 2006-08-17
This is probably obvious to non newbs, but just a note. If you have spaces in the folder, you have to add ' to either side of the folder name. Example:```
sudo rm -f 'Windows Drive'
``` instead of:```
sudo rm -f Windows Drive
```

This is if you are in the folder where the undeletable links are already.

---


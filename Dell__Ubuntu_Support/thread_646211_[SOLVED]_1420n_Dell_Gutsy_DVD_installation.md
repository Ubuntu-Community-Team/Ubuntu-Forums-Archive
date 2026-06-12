---
title: "[SOLVED] 1420n Dell Gutsy DVD installation"
date: 2007-12-20
forum: Dell  Ubuntu Support
---

### Post by natehall on 2007-12-20
I still have the factory installed Fiesty on my machine. So Ive decided to take the plunge. I've downloaded and created a DVD (4.2Gigs!). I I've backed up my data (Just in case) and I'm ready for the fresh install. What do I do next?

---

### Post by natehall on 2007-12-20
I 'd post the DVD's directory if I could but it is called "Dell Ubuntu Reinstallation Media" and the Bash terminal does not like spaces in the filenames! (Couldn't they have made it a little easier by calling it "Dell_Ubuntu_Reinstallation_Media" !

---

### Post by desheffer on 2007-12-21
The intended usage is to reboot it like a Live CD. When it boots it should have an icon to install it onto your hard drive. This will erase everything on your hard drive, so be careful and make sure you've backed it all up.

FYI, to change to a directory called "Dell Ubuntu Reinstallation Media" using bash, you will need to place a backslash in front of each space. For example: ```
cd Dell\ Ubuntu\ Reinstallation\ Media
```

---

### Post by natehall on 2007-12-21
Funny you should post that, I remember reading about using the \ and I tried it just before reading your post. Thanks anyways. There was an eariler post, [http://ubuntuforums.org/showthread.php?t=640828](http://ubuntuforums.org/showthread.php?t=640828) about making a new factory partion like for Gutsy.  I would like to follow his guide but My Linux version is different than what the post showed.

---

### Post by gbrainin on 2007-12-21
You can also deal with spaces (or other reserved characters) in file or directory names by enclosing the name in single quotes, e.g.:
```
cd 'Dell Ubuntu Reinstallation Media'
```

---

### Post by timseal on 2007-12-21
What if you just add the dvd as an apt source, comment out all the other sources, and do a dist-upgrade?  Wouldn't that do the trick?

---

### Post by adrianmak on 2007-12-21
work with 1420 model (without a  n )??

---

### Post by natehall on 2007-12-21
There was another tread that had the link I needed. The solution was to simply hit f12 real fast when the Dell logo came up . It walks you through from there.  ( I saved my data on USB sticks, Since my files were all messy anyways I figured  a reinstall is a good time to organize them neatly on the reload)

---

### Post by natehall on 2007-12-21
> **adrianmak said:**
> work with 1420 model (without a  n )?? It should. The N only means it never had Windows loaded.  You might have a different wireless card  Intel has better support for Linux , so that is what drives the Wireless and the Video If you are concerned about that type in ( without the quotes) "sudo lshw" in your terminal to find out.

---

### Post by adrianmak on 2007-12-21
does dell ubuntu 7.10 version solve the compiz fusion issue ??

And my 1420 is installed official ubuntu 7.10 for few months. how do I do an update patached packages from the Dell version without a fresh installation ?

---


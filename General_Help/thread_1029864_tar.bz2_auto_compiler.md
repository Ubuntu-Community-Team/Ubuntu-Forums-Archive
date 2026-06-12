---
title: "tar.bz2 auto compiler"
date: 2009-01-03
forum: General Help
---

### Post by jtb74129 on 2009-01-03
Hi All.  I am probably going to get torched for this but I am going to ask this question anyway.  I am new to linux and have chosen Ubuntu after trying more distros than I thought possible.  I have done my research all across the net looking for a simple answer to compiling and installing .tar files.  I have seen more comments about it being difficult for noobs to compile and all the instructions that tell you how are lengthy.  So my question is this (humbly asked, since I know nothing about linux):

Why does everyone like to reinvent the wheel?  I would think that with all the experts that are out in Linux universe (which I have seen the work, and it is incredible) why no one has come up with an auto compiler that simply takes a .tar.bz file and compiles it into a .deb file? 

If there is one out there, please point me to it, because it is not showing up in any of the forums or google searches I have done.  Only how to compile it yourself the long way.

Ok...I have now put on my fire proof suit...the torching my commence...:)

Thanks for your help in advance...I have plenty of marshmallows to share..

---

### Post by Frak on 2009-01-03
Well, we sort of do have something like that. It's called [checkinstall]("apt:checkinstall").

---

### Post by tech0007 on 2009-01-03
One reason I could think of is not everyone likes a particular program the same way.  Compiling from a tar ball gives you the chance to customize it. It's a linux thingy, I guess but I could be wrong. :)

---

### Post by kevdog on 2009-01-03
depending on architectures, you need to usually run a configure script that you can customize with certain switches.  Additionally some programs simply have only a make file with no configure file.  I wish it were that easy as you wanted.  And finally checkinstall is a sad way to make a .deb.  I really am aware of any real way to make a distributable .deb file although I know there is a way -- its very difficult.  Pacman would be a much better way to create a compiled/distributable executable.

---

### Post by jtb74129 on 2009-01-03
> **kevdog said:**
> depending on architectures, you need to usually run a configure script that you can customize with certain switches.  Additionally some programs simply have only a make file with no configure file.  I wish it were that easy as you wanted.  And finally checkinstall is a sad way to make a .deb.  I really am aware of any real way to make a distributable .deb file although I know there is a way -- its very difficult.  Pacman would be a much better way to create a compiled/distributable executable.

Can you send me a link to Pacman.  When i search for it in synaptics I get the game.

---


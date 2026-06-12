---
title: "Best place to install game?"
date: 2009-04-28
forum: General Help
---

### Post by ManyBeers on 2009-04-28
I downloaded a chess engine from here [http://jose-chess.sourceforge.net/index_download.html]("http://jose-chess.sourceforge.net/index_download.html")
and would like to know when I install it what would be the correct folder to be in when doing so. The .tar.gz currently sits on my desktop.

---

### Post by 3Miro on 2009-04-28
Doesn't it come with instructions?

Programs that run for everyone are usually installed in /usr/local/something

If you will be the only one to play the game, try:
/home/your_username/something

Depending on the game, the second may not work, but it is the more secure way of doing it.

---

### Post by soro2005 on 2009-04-28
Either /opt or keep it in your /home directory. It probably doesn't matter where you put it. You just shouldn't clutter the filesystem. /opt is a good place for that sort of manually added programs.

---

### Post by mb_webguy on 2009-04-28
If it came in a tarball, it's probably source code.  If you use [checkinstall]("https://help.ubuntu.com/community/CheckInstall") when you compile and install it, a package will be created and the program will be installed to /usr/local, along with all other manually-installed programs.   Plus, you'll be able to manage the software using the package managers.

---

### Post by soro2005 on 2009-04-28
It's in java. He doesn't need to compile it, just to leave it somewhere where it doesn't get in the way. /opt is the right place, or inside his home directory.

---


---
title: "HOWTO: Beep Media Player 2 (BMPx) for Ubuntu"
date: 2006-06-24
forum: Desktop Environments
---

### Post by Nexu on 2006-06-24
BMP started out as a project to port XMMS to a GTK+2 interface.
The development on BMP came to a halt after 0.9.7 release. The
reason lies within the XMMS codebase which was troublesome
to work with.

The main authors of BMP decided to start out fresh. Which allows
them to implement the same functionality and more without being
held back by old merits inherited from XMMS codebase.

This new codebase is called "BMPx" as a project name. This will
be eventually change to [COLOR="RoyalBlue"]Beep Media Player 2[/COLOR] when time comes.

For a list of current features see [here]("http://bmpx.beep-media-player.org/site/About").

**You can find .DEB files here until it get imported in Ubuntu:**

[http://thehoneymustardbandits.org/nexu/linux/beepmediaplayer/]("http://thehoneymustardbandits.org/nexu/linux/beepmediaplayer/")
(There were some other posts about BMPx debs/repository before.
But those are outdated by now)

**For a compiling from SVN HOWTO. Go to this link:**

[http://forum.beep-media-player.org/viewthread.php?tid=182]("http://forum.beep-media-player.org/viewthread.php?tid=182")


[IMG]http://bmpx.beep-media-player.org/beepmediaplayer-small.png[/IMG]

---

### Post by alingatong on 2006-06-25
I love bmpx but I am just afraid of its many dependencies. Its just a media player but those dependencies are killing me. 

I tried sudo dpkg -i one of your .debs

and I get this error:

dpkg: dependency problems prevent configuration of bmpx:
 bmpx depends on libglademm-2.4-1c2a; however:
  Package libglademm-2.4-1c2a is not installed.
 bmpx depends on libboost-filesystem1.33.1 (>= 1.33.1); however:
  Package libboost-filesystem1.33.1 is not installed.
dpkg: error processing bmpx (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bmpx


When i apt-get install libglademm or something, it cannot be installed because of depends on libgtkmm..

What do you suggest for me to do just run this app?

---

### Post by Nexu on 2006-06-26
Check the page out again. There is now a repository :D

---

### Post by IcemanV9 on 2006-07-11
BMPx's [website]("http://bmpx.beep-media-player.org/site/Downloads#Ubuntu") do have a package for Ubuntu to download/install via aptitude (or apt-get).

It works nicely on my box.

---

### Post by Nexu on 2006-07-11
I know :)

I builded those :)

---

### Post by Panic.fo on 2006-07-13
I get the same errors as alingatong..

Any ideas?

---

### Post by Nexu on 2006-07-14
Which .deb did you used?

(answer: you shouldn't use any downloaded deb but use the repository on bmpx site)

---

### Post by loftx on 2006-07-29
I get the same errors, using the instructions straight from [http://beep-media-player.org/site/Downloads](http://beep-media-player.org/site/Downloads)

The problem seems to be no libboost-filesystem1.33.1 package.

**Edit:** The problem went away after I fixed my sources.list. It was missing some repos

---

### Post by bhoughton on 2006-08-12
Just a NOOB here 

What do I do with the KEY... I saved bmp-packages.pubkey to the desktop and executed the sudo apt-key add bmp-packages.pubkey and received the following:

"gpg: can't open bmp-packages.pubkey no such file or directory"

Any tips are greatly appreciated...

Regards,

---

### Post by Dubbayoo on 2006-08-13
> **bhoughton said:**
> Just a NOOB here 

What do I do with the KEY... I saved bmp-packages.pubkey to the desktop and executed the sudo apt-key add bmp-packages.pubkey and received the following:

"gpg: can't open bmp-packages.pubkey no such file or directory"

Any tips are greatly appreciated...

Regards,


you either saved it with a different name or it isn't in the dir you're running the command in.

---

### Post by maniacmusician on 2006-08-13
I tried using the repositories, but it didn't work; it said it couldn't find the package bmpx.

---

### Post by ruffneck on 2006-10-04
I noticted the repos are for dapper. Will it work with Edgy as well?

---


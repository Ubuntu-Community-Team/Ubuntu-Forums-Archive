---
title: "Environment variables (Oh, not again!)"
date: 2009-04-03
forum: General Help
---

### Post by nmccrina on 2009-04-03
Hello all,

I know there is a ton of info about environment variables all over, but perhaps that is the problem. I can't seem to wade through it all to get the "one single definitive answer" on where to set the damn things. One place says .bashrc, another says .bash_profile, then there's /etc/profile, /etc/environment, etc. etc. etc. So my question is this: is there a single file somewhere that I can set environment variables in so that they will be read by everything (console, GNOME, anywhere)?

The specific situation is as follows. I've installed Java and Eclipse from source (and before everybody says "well, it's in the repositories", let me just say that I like installing from source). It wasn't a big deal, I just unpacked the respective .bin and tar.bz2 files in ~/src, then put symlinks to the binaries in ~/bin. My path is supposedly set (in .bashrc and /etc/environment) so that ~/bin is in my PATH. Currently, the eclipse, jar, java, javac, javaws, javadoc, and appletviewer programs are all symlinked to in ~/bin. And, in the terminal, I can run Java and it is found, and I can even run Eclipse and it finds Java. But, when I tried to make a launcher for Eclipse with the command /home/nmccrina/bin/eclipse, it says that it can't find Java. Is this because the PATH variable that I set twice only applies to the shell, and GNOME needs the PATH set elsewhere? If so, where do I need to set the path?

This is one of the few areas where it seems to me that Windows makes more sense. There is ONE place to set the path, and you are done.

Thanks for the replies.

---

### Post by nmccrina on 2009-04-04
Well, it is fixed. I made a jre symlink in the Eclipse folder that pointed to the jre folder in my jdk directory. Why or how this fixed anything, or indeed why it would run in the terminal but not by launcher before, is beyond me. Oh well, a lot of things are. 

Anyway, now I'm not sure the problem had to do with my PATH at all. 

):P

---


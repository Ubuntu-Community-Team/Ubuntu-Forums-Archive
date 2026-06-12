---
title: "Kubunto sources.list ?"
date: 2006-02-18
forum: Desktop Environments
---

### Post by jenkins_t on 2006-02-18
I am a Linux newbie. I do however have a dual boot laptop with XP and Mepis installed. I left some free space on hda to play with other distros. My question is this:

With Ubunto, can I use Debian pools or do I use Ubunto pools?

Here's my Mepis sources.list, can I use the Debian pools from that in Ubunto?

```

# See sources.list(5) for more information, especially
# This file should be edited through synaptic
# New sources should be added only in the section at the end of this file!

# Primary
deb ftp://ftp.debian.org/debian etch main contrib non-free
# deb ftp://ftp.debian.org/debian sid main contrib non-free

# Sources
# deb-src ftp://ftp.debian.org/debian etch main contrib non-free
# deb-src ftp://ftp.debian.org/debian sid main contrib non-free

# MEPIS apt pool - specific packages available on-line
deb http://apt.mepis.org/3.4 etch main
# deb http://apt.mepis.org/3.4 sid main

# mplayer
deb ftp://ftp.nerim.net/debian-marillat/ etch main
# deb ftp://ftp.nerim.net/debian-marillat/ sid main

# Security upgrades for Etch
deb http://security.debian.org/ testing/updates main contrib non-free


```

I realize that Mepis wont do any good. Or does Ubunto sources give all of software that is avail thru above sources?

---

### Post by GeneralZod on 2006-02-18
Ubunt**u** :)

You are strongly advised *not* to use any Debian repositories.  Here is a fairly complete Ubuntu sources.list, courtesy of aysiu:

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by jenkins_t on 2006-02-18
Thanks for the reply. So will ubuntu sources have normal stuff like Apache, Webmin, MySQL, gkrellm. Well that may not be so normal, but what I could think of.

Does it use Synaptic manager?

---


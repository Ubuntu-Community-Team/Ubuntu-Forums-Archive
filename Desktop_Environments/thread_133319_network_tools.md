---
title: "network tools"
date: 2006-02-20
forum: Desktop Environments
---

### Post by meagert on 2006-02-20
new linux user...retired novell/ms sys admin...
installed ubuntu 4 ...nice...one problem so far (a million to come), network tools.
I try to run it, the screen appears for 2 seconds at most...disappears.  I need access to these tools, as I have a home network, and need to experience networking from a linux box. I have not an effin clue about linux, except that I like it so far. I intend on an immersion for the next few weeks, but if anyone can help with this first problem, much appreciation will be bestowed upon you.....

---

### Post by heimo on 2006-02-20
Open a terminal window and run gnome-nettool. You probably get some errors if the application doesn't run. Post the errors / warnings.

---

### Post by linuxusr50 on 2006-02-20
open a terminal and type

man [*toolname*]

Replace [*toolname*] with any of the following:

ifconfig
ping
tracepath
dhclient
ip
ifup
ifdown
netstat
.....many more.....

you can get an idea by typing    **man -k network**     at the command line in a terminal window.

Luck,
Dan

---

### Post by meagert on 2006-02-20
*** glibc detected *** free(): invalid pointer: 0x08271f00 ***
Aborted
thanx heimo

and Dan for the tip

---

### Post by heimo on 2006-02-20
[quote=meagert]*** glibc detected *** free(): invalid pointer: 0x08271f00 ***[/quote]

Huh. :shock: I'd probably check that I have updated my Ubuntu. Might be a bug in some older version of that application, but I haven't encountered that one. Command line versions, as Dan posted, are a very nice way to do the same thing - I consider it more flexible, but that's of course question of preferences.

updates your system:
```
sudo apt-get update
sudo apt-get upgrade

```

---


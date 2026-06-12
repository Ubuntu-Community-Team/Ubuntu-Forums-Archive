---
title: "Programs close themselves"
date: 2009-01-18
forum: General Help
---

### Post by mrkane27 on 2009-01-18
It goes like this. I'm surfing the web and for instance I'm trying to type an address in the address bar. At some point, I press a letter key, and the Firefox window disappears.
Or. I'm grabbing some lunch with a Linux DC++ window open and when I come back it's gone. (Also happened with Pidgin.)

I'm thinking, it's only happened with GTK applications, but I haven't a clue as to what's causing it.
Any help would be greatly appreciated.

Thank you,
Vlad

---

### Post by x33a on 2009-01-18
open these programs from the terminal. keep an eye on all that is verbosed on the terminal. when a program crashes, you might find something useful there.

---

### Post by mrkane27 on 2009-01-18
vlad@vldku:~$ linuxdcpp
Loading: Hash database
Loading: Shared Files
Loading: Download Queue
Segmentation fault             (some time later)

Well... So much for that. :))

---

### Post by HavocXphere on 2009-01-18
Run a memtest on the box for a few hours and see if that turns up anything. (Boot from CD and select it from the menu).

Weird that it only happens with gtk apps though... You can try changing the gtk theme to Raleigh and see if that makes a difference.

---

### Post by joereith on 2009-06-15
I had that problem for quite some time. what I found it to be is that there was a slight fluctuation in my power supply that would cause a memory address to not be accessible and therefore close that application with a segmentation fault so I would also look at that along with the mem test from the cd. Good luck, hope you get it resolved.

---


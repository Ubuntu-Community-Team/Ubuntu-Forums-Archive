---
title: "Modifying Keymaps in Hoary Hedgehog"
date: 2006-01-23
forum: Desktop Environments
---

### Post by schnarff on 2006-01-23
Hello All,

I apologize if this is a redundant question, but I've spent the last several hours trying to figure this out via man pages, conf files, this forum, and Google, without much success.

Basically, I'd like to modify the US-International w/dead keys layout and then load the modified layout. The goal is to do things like changing:

```
    key <TLDE> {        [dead_grave,    dead_tilde      ],
                        [     grave,    asciitilde      ]       };

```

to

```
    key <TLDE> {        [     grave,    asciitilde      ],
                        [dead_grave,    dead_tilde      ]       };

```

This way, since I spend most of my time typing regular US-English characters (i.e. "~" as Shift+Tilde to get to my home dir), I'll only have to hit extra keys on the rare occasion that I'm writing in French. 

I'm running an essentially stock version of Hoary Hedgehog. I've found files like /etc/X11/xkb/symbols/us (which is where I pulled the above from), /usr/share/xmodmap/xmodmap.us, etc., but I have no idea which one is actually controlling my setup, and how to reload it once I've modified it.

Thanks in advance for any help you can give.

Alex Kirk

---

### Post by yanik on 2006-01-23
Is there a reason you post your Hoary question in the Breezy forum?

---

### Post by schnarff on 2006-01-24
::Sigh:: Because when I originally opened a window to post in, I had forgot I wasn't running Breezy (I am at home, just not at work), and I made a dumb mistake. Definitely a long day yesterday. Any way this can be moved over to the Hoary forum, or should I just create a fresh post over there?

Thanks,
Alex Kirk

---


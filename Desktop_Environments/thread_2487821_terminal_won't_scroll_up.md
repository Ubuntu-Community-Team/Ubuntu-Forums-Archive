---
title: "terminal won't scroll up"
date: 2023-06-15
forum: Desktop Environments
---

### Post by bitrat2 on 2023-06-15
Hi,

on Ubuntu 18.04.6 LTS, the terminal scrolling behaviour sometimes changes, usually after some kind of impolite interaction with 'less' (eg killing less or a process piped into less).

When this happens, there doesn't seem to be any way to scroll up.  The scroll bar is there, but there's no handle.  Also the mouse wheel changes behaviour from scrolling the terminal buffer to scrolling the command history (which is usually hooked to up/down arrows on my system).  

The shift+up/down/home/end keys just write capital letters to the terminal.

Is there some corruption of the current terminal configuration?  Can I read/write that to correct it an open terminal?  I've tried messing with the preferences dialog, but it is spartan and has no effect.

Can I reset the terminal to its original config without losing the current buffer contents?

Note: this happens in a newly opened terminal, so not related to buffer size.

Cheers.

---

### Post by TheFu on 2023-06-16
**Which terminal?**  There are like 20 different choices.
If you don't know, check the process table for the actual name of the program being run.

I really hope you've signed up for ESM support with 18.04.  Regular support for that release ended.

---

### Post by bitrat2 on 2023-06-16
Hi, thanks, yes I'll be updating my system v soon!  

```
$ pstree -aps $$
systemd,1
  &#9492;&#9472;systemd,2680 --user
      &#9492;&#9472;gnome-terminal-,3567
          &#9492;&#9472;bash,490
              &#9492;&#9472;pstree,10628 -aps 490

```

---

### Post by TheFu on 2023-06-16
I don't use gnome-terminal, so I can't help.  I'm an xterm user.

Soon, updating from 18.04 will be very difficult without a fresh install. Best hurry or plan on a fresh install. I think you have days, not weeks, before the difficulties start. There are many things that changed since 18.04, so a fresh install is really the only way to remove all the old cruft.  If you moved from 16.04 via upgrade to 18.04, it is time for a fresh install anyway.

---

### Post by bitrat2 on 2023-06-16
Yes, definitely a complete rebuild.  I'm contemplating a shift to Debian 12 with IceWM or similar.

---


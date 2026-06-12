---
title: "Gnome icons disappear &amp; desktop freezes"
date: 2007-09-15
forum: Desktop Environments
---

### Post by jlee on 2007-09-15
A number of posts reference problems w/the desktop freezing and
the loss of desktop icons.  My experience followed the addition of
an icon from Firefox by dragging from its address bar to the desktop.

A week prior, I had tried to back up my desktop folder to another
machine on my network. Some of the Firefox "shortcuts" could not
be read or transfered.

By moving the most recent icon/link to trash and rebooting via
CNTL ALT DELETE the problem disappeared.

I conclude that a corrupted icon/link file prevented Gnome from
rendering the desktop when required.

Questions:
  What type of file is associated w/an icon?
  Is it editable?
  What function in Gnome refreshs the desktop?

---

### Post by Wolki on 2007-09-15
Which version of Ubuntu are you running? I've seen links with special characters crashing gnome some versions back, but it doesn't seem to happen anymore.

> **jlee said:**
> 
  What type of file is associated w/an icon?
  Is it editable?
  What function in Gnome refreshs the desktop?

Icons are usually .desktop files. More information on them here:[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)
They're editable, but GNOME for some reason doesn't offer to edit them. Just dragging them to a text  editor should be fine; some things can also be changed from their properties window.
I'm not exactly sure what you mean with your last question. The program responsible for drawing the desktop is nautilus, you can force a refresh with ctrl-r or F5.

---

### Post by jlee on 2007-09-17
Thank you for the very useful link. I'll need to spend some
time digesting the info therein.

I'm running v7.04 that has been upgraded several times 
beginning w/Warty  ... no beryl.

So, something about the icon/link file disagrees with Gnome
when it "renders" the desktop.  Whether its a problem with
the file or charactors within is yet to be determined.

---

### Post by krelverehan on 2007-12-15
I know this is a little late for a response, but I run into similar problems where the desktop freezes, but the rest of the computer seems to run fine. It seems to be a case for me where nautilus is actually freezing.

I just enter in the terminal:
[FONT="Courier New"][INDENT]
user@computer:~$ killall nautilus[/INDENT][/FONT]

---


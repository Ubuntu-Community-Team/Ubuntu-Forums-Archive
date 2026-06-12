---
title: "Startup Applications"
date: 2009-12-06
forum: Desktop Environments
---

### Post by b00n on 2009-12-06
I've browsed the forums a bit and still have questions about startup applictions.

I'm running 9.10 and x86-32 if that matters.

(a) I tried System > Preferences > Startup Applications {Options} [Remember Running Applications], with Firefox, an xterm, and Emacs running.  When I log in again I get Firefox and Emacs.  I originally started Emacs with "-rv" but it comes up without that.  After groveling around under $HOME for a while I found .config/gnome-session/saved-session has a file <long name>.desktop and if I edit the command line by adding "-rv" I get Emacs the way I want.  Is the file location and format documented someplace? Web searching on ".desktop" just gets hits for "desktop".  Also, I notice it has things like "--smid=..." and AFAIK Emacs does not take that as a flag.

(b) The xterm I had running was apparently not recognized, because I do not get one when I log in again.  Is this a bug?  A known limitation?

(c) It would be really great if "remember running applications" provided a way to browse and edit what got saved.  Should I submit a ticket somewhere?

---

### Post by akashiraffee on 2009-12-06
> **b00n said:**
>   Is the file location and format documented someplace? 

Yep.  Look in the "Gnome Desktop Administration Guide" -- I think you can search for .desktop in the help browser there.

For a quick orientation see post #20 on this page:
[http://ubuntuforums.org/showthread.php?t=1346796&page=2](http://ubuntuforums.org/showthread.php?t=1346796&page=2)
However, that may not be the only purpose of a .desktop file, it's just the only one I know of ;)

You can also find stuff in "man desktop-file-install".

---

### Post by b00n on 2009-12-06
Thanks!  For anybody "watching" that also led to this guide describing the file format

[http://standards.freedesktop.org/desktop-entry-spec/latest/index.html](http://standards.freedesktop.org/desktop-entry-spec/latest/index.html)

I still do not understand how "--smid" is used, any suggestions where to look for that?  It appears it is accepted by Emacs but there's no documentation for it that I see.  A web search on '--smid' turns up lots of results for 'smid'.

> [http://ubuntuforums.org/showthread.php?t=1346796&page=2](http://ubuntuforums.org/showthread.php?t=1346796&page=2)

That suggests to me I might be able to "Remember Running Applications" including xterm if I had an xterm.desktop file, but I'm not sure how to do that.  If I try to create one in ~/.local/share:[INDENT]~/.local/share$ desktop-file-install xterm.desktop
Error on file "xterm.desktop": Failed to create file '/usr/share/applications/xterm.desktop.1E7D4U': Permission denied
[/INDENT]I could put one manually in ~/.config/gnome-session/saved-session/ but I don't understand how to tie it in to the saved session framework, and at any rate if I have to put it there it seems like I already missed doing it the right way.

---


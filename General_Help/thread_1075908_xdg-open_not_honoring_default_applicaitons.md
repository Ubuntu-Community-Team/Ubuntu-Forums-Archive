---
title: "xdg-open not honoring default applicaitons?"
date: 2009-02-20
forum: General Help
---

### Post by mb_webguy on 2009-02-20
The commands "gvfs-open" and "gnome-open" open files using the expected default applications.  The "xdg-open" command, however, doesn't, and it's causing some frustration for me with applications that use this command to open files and directories.

What's even more strange is that "xdg-mime" shows the correct default applications!  Take a look:```
matt@the-tardis:~$ xdg-mime query filetype test.avi 
video/x-msvideo
matt@the-tardis:~$ xdg-mime query default video/x-msvideo
vlc.desktop
matt@the-tardis:~$ xdg-open test.avi 
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
[...]

matt@the-tardis:~$ gnome-open test.avi 
VLC media player 0.9.8a Grishenko
[...]

matt@the-tardis:~$ gvfs-open test.avi 
VLC media player 0.9.8a Grishenko
[...]

```
Even stranger, "gnome-open" and "gvfs-open" open text files with Gedit (which is the associated application), but "xdg-mime" doesn't show any associated applications, and "xdg-open" opens text files with vim.

So... is this a bug, or does "xdg-open" keep it's file associations somewhere other than the standard mime defaults files used by pretty much every other application?  If it's the former, is there a fix or workaround?  And if it's the latter, where are these associations kept, and why would it not agree with "xdg-mime", which is supposed to be used to show and set the defaults for "xdg-open"?

---

### Post by mb_webguy on 2009-02-22
*bump*

If it means anything, I first noticed this when trying to open files from within Deluge while using an Openbox session.  In Gnome, Deluge opens files using my Gnome defaults, but in Openbox it doesn't.  A bit of Googling revealed that Deluge uses xdg-open, which led me to discover this issue.

---

### Post by jeffus_il on 2009-03-29
We are dealing with the same problem here:
> [http://ubuntuforums.org/showthread.php?t=1108776](http://ubuntuforums.org/showthread.php?t=1108776)
I am playing a bit in the hope of some success...

---

### Post by unless-cam on 2009-04-11
For me I think the problem occurs because I'm using dwm rather than gnome kde etc.

xdg-mime appears to report the file associations used by gnome, however xdg-open appears to use the file associations used by /etc/mailcap

As a workaround editing /etc/mailcap seems to do the trick.

---


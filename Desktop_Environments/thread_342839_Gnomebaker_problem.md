---
title: "Gnomebaker problem"
date: 2007-01-20
forum: Desktop Environments
---

### Post by vims1 on 2007-01-20
I can't burn audio CDs direct from mp3 with gnomebaker.  When I try to add a file to the "tracklist" gnomebaker just shut down.  Here is the what is written in the terminal while running:

$ gnomebaker
/bin/sh: /usr/bin/esd: not found

** ERROR **: file media.c: line 271 (media_info_get_mediafile_info): assertion failed: (decodebin)
aborting...
Aborted (core dumped)

I use xubuntu, edgy, and the version of gnomebaker is 0.6.0.

Does anybody have a solution to the problem??

---

### Post by Cobikegeek on 2007-01-21
Do you have the codecs below installed?  This is from the ubuntu restricted formats page.

"To add mp3 support to GnomeBaker, install gstreamer0.8-mad and gstreamer0.8-misc."

You might also try using the K3B app as your burner.  It's more full-featured than gnomebaker.

---


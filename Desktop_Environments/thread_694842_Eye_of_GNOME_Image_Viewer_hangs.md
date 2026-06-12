---
title: "Eye of GNOME Image Viewer hangs"
date: 2008-02-12
forum: Desktop Environments
---

### Post by mathenge on 2008-02-12
Eye of GNOME Image Viewer no longer works on my system. Each and every image file (I've tried .JPG, .PNG and .BMP) cause the application to freeze. The main window turns grey and I have to FORCE QUIT it.

Strange thing is that I can run it under a debugger. If I start Eye of GNOME (/usr/bin/eog) under my curses debugger (cgdb) is successfully opens image files and quits normally when I close it.

Since there's no output from Eye of GNOME, it logs nothing to the system, even when started at the command line there's no information, when killed it dies without a sound it's impossible to send out any messages that might help anyone debug this problem other than the scenario I've described.

When it hangs, the message in the status bar is normally something like: Loading /home/user/a.jpg...

I've currently changed my default handler for images to gThumb so my life continues though I'd like to find a solution for this.

---

### Post by fakeollie on 2008-03-05
The same thing is happening to me lately. EoG gets stuck reading random files. When it hangs, I kill it, and just open the same file again and it works. 

I couldn't reproduce it from the command line to watch for any error messages, since once I kill it, it then starts working again. It hangs while the status line reads "loading image filename.jpg"

It's really annoying.

---


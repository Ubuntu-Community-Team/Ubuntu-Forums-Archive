---
title: "segmentation fault launching lots of programs."
date: 2013-03-15
forum: Desktop Environments
---

### Post by jimbo99 on 2013-03-15
We might mark this as solved.  I'm posting it for posterity.  It took some time to trace this down.  I solved my problem so now I want to at least document it.  Maybe someone else will benefit.

_Back-story (short)._

I filled my hard drive up.

Just after this happened I received a long cryptic (and I mean long and cryptic -- excessively long cryptic almost unusable by the average person) message telling me that there was a problem with some file.  Once I noticed that I'd had the issue I cleared some space figuring that's all I needed.  However, issues started cropping up.

Attempts to load "terminator" or "google chrome" (and many others) resulted in a failed attempt.  Launching them in a terminal window resulted in a message indicating that there was a segmentation fault.  This issue also happened during updates.

Upon reviewing some of the log files indicated an issue with something about a library file with libgio-2.0.so.0.3* in the name.

That's the back-story.

_Path to Discovery:_

I created a new account and logged in.  Everything worked.  So...

I created a folder to hold **all** the hidden files that were located in my home folder.

I then logged out and back trying to launch terminator (loads fast so it's a good test since it was 100% segementation faulting).

This worked.  So I began moving hidden folders back into place in small groups, logging out, and then back in.  Each time I launched terminator I would then copy another group of folders until it failed to work.

When this happened I moved all the hidden **files** back into my home folder.

I then began moving folders from the home folder back into the folder for holding the hidden files until terminator worked again.

It turns out it was the .local folder that was causing me the grief.

I looked into that folder and found a bunch of additional folders and files.

Rather than move folders around I chose to just move the files first.

This resulted in terminator failing to launch.

In the end the file causing the problem was called "mime-cache".

I put everything back, and though the desktop is a bit messed up everything works again.  I have no idea what the mime-cache file is nor how to rebuild it. 

I didn't have to reinstall the OS and in the end it would not have mattered as the problem was with a local file in my home folder.

---

### Post by jimbo99 on 2013-03-16
One point of this story is that a single file (a data file at that) in your home folder can cause hundreds of applications to crash upon launch.  This is a single point of failure that should not exist.

---


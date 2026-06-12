---
title: "Acroread Plugin Under Limited User"
date: 2012-05-29
forum: Desktop Environments
---

### Post by RylosFan on 2012-05-29
I'm experiencing an odd problem using a PDF plugin within Firefox 11 on Ubuntu 10.10.  The problem is that I have a few users that need to print paystubs from our HR site; the server is supposed to display a pdf within a new dialogue window, unfortunately, it does not (just shows a blank page).  

There is no problem on the admin account and, unless by some fluke it worked a handful of times, I even created a temporary, limited user account that the PDF plugin seems to work just fine.  

I've done my best to make sure that both the current limited and the temporary limited account are identical in configuration, **/bin/false**, not allowed to perform admin functions on the computer to no avail.  Since I had setup the browser to always run in private mode, I thought this had something to do with the plugin issue, however, running the browser in normal mode has no affect.  Looking at Firefox's about:plugins, Adobe Reader's plugin is displayed on all accounts.

I've gone so far as to delete all configuration files relative to Firefox and Adobe Reader for the user and even wiping out the limited user's home directory (kinda nuking an ant hill, but I ran out of ideas).

The software in question is: **Adobe Reader 9.5.1 (plugin**), **Firefox 11**, and **Ubuntu 10.10 x86**.

I hope someone can think of something else.

---

### Post by RylosFan on 2012-05-29
**UPDATE**

Ok, so I installed mozplugger and that seem to make the difference for the limited user.  However, it doesn't work on the first click of the "print" button, it has to be clicked again for the window to spit out the PDF.  I did notice the a debug log in the user's directory, which I've attached.

My best guess at this log is either a permissions issue with the /tmp directory or some sort of bug with the reader plugin?

Thoughts anyone?

---


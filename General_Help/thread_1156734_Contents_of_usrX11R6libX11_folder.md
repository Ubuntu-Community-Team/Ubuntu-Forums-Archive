---
title: "Contents of /usr/X11R6/lib/X11 folder"
date: 2009-05-12
forum: General Help
---

### Post by ramb4ldi on 2009-05-12
Hello, thanks for any help you guys offer (or redirection if I should be trying a different area of these forums).

Hopefully it is pretty simple to sort out, I was trying to move a file around but missed the last / on the destination, basically:
sudo mv ~/Desktop/rgb.txt /usr/X11R6/lib/X11
instead of 
sudo mv ~/Desktop/rgb.txt /usr/X11R6/lib/X11/
Wasn't really paying attention, I was just copying the code instructions from a site.

Everything still seems to start up properly but I am pretty sure there were important files in that folder (I know for instance that the program I was setting up runs in black and white rather than colour but then that might be a different issue) so basically my question is:

[B]What packages do I need to reinstall to ensure that the folder contains all of the default stuff that it is meant to?
[/B]
I had looked in the package manager and found X11-common and reinstalled that but that made no changes, should the folder be empty on a standard default install possibly and I am worrying about nothing?

---

### Post by Brandon Williams on 2009-05-12
What happened when you did this? If the directory already existed, then the two commands are equivalent. If the directory did not exist, then the command you ran would have created a new file call /usr/X11R6/lib/X11, while the command you intended to run would have failed.

On my Jaunty system, there is no directory called /usr/X11R6/lib, so both of those commands would have failed. On my Hardy system, /usr/X11R6/lib exists, so the command you ran would have created a file called X11 in that directory. If this is also the case for you (a file was created), then just delete the file. There is nothing to reinstall.

---

### Post by ramb4ldi on 2009-05-12
It created a file called X11 so I assume it is the same as your Hardy system, most probably because I didn't do a clean install for jaunty. It seems as if everything is fine then. Thank you for your response.

---


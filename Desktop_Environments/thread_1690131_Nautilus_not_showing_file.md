---
title: "Nautilus not showing file?"
date: 2011-02-17
forum: Desktop Environments
---

### Post by jclose on 2011-02-17
Hey all, I am having an odd issue I am hoping you can help me with.

I created a spreadsheet (OpenOffice) and then saved it to the harddrive, but Nautilus doesn't show the file(s) (I created an XLS version of the file, too).  It became an issue when I wanted to attach that file to an email and I couldn't find it to click on it in the browse window.

*  File shows up in terminal window ('ls' command).
*  File is not hidden; show hidden files is on.
*  Saved location is a symlink to an NTFS partition.
*  I saved a copy to a native partition and that showed up OK.
*  Many many other files in that same folder show up without problems.  
*  I have done this process before (creating new documents - with OpenOffice even, saving them to this partition) without similar problems.
*  File opens fine from OO's 'Recent docs' list.
*  Nautilus v 2.32 (Ubuntu 10.10)

Anyone have any ideas?

Thanks,
J

---

### Post by Krytarik on 2011-02-18
May it be the filename, does it contain any special or localized characters?

---

### Post by Semox78 on 2012-05-08
Hello everybody

No. This is not the problem. I have the same issue with Nautilus. 

This is the 2nd time (after 3 month or so), when a folder won't show its files in Nautilus. I am using U11.10. Within both folders are some 20-50 files. They're of mixed content like images, PDFs and so on. In the terminal they can be found and listed. Even when I open a PDF from evince or I don't know what the Reader is called, the PDFs will show up and can be opened.

What is it, that Nautilus does not show the files properly? How can Nautilus be configured to fix that issue? This seems to be a sporadic bug, but how can I repair the view of the folder?

I repeated the steps from my previous speaker:
*  Files show up in terminal window ('ls' command).
*  Files are not hidden; show hidden files is on.
* Files open up properly in Applications

Even a restart would not 'fix the folder'.

Best rergards,
Semox78

---

### Post by xtaylord on 2012-05-29
I had the same issue
Typing sync  on the command line fixed it

---

### Post by VanillaMozilla on 2012-05-29
Yep, same here.

I'm not at a Linux system at the moment.  What does sync do?

Seems like you shouldn't have to kick Nautilus to get it to display a file.  A bug, surely.


EDIT:  Not a bug, just a minor nuisance.

---


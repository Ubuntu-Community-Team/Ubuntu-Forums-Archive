---
title: "Progress bar Useless (zip, rar etc)"
date: 2008-12-04
forum: Desktop Environments
---

### Post by 09buntu on 2008-12-04
Hello!

Whenever I extract zip, rar etc in Ubuntu 8.10 the progress bar goes to 50% and then stayes there until it's complete 100%.

This is not how a progress bar should work IMHO. 
It makes the whole idea with a progress bar useless!

So, is there a solution?

---

### Post by SamNSane on 2008-12-05
I've never seen this in Ubuntu. I'm guessing there's something special about your configuration that's involved somehow in making this happen.

Maybe if you post some information about your hardware, particularly memory and disk configuration, one of the brighter folks around here will be able to help you.

And then, of course, there'll be some folks like me involved, too. We won't be helpful, but we'll try (your patience, probably).

That is a pretty funny issue. I didn't think I'd ever hear about a progress bar more useless than the type I used to see in older versions of Windows.

---

### Post by 09buntu on 2008-12-05
[quote=SamNSane]I've never seen this in Ubuntu. I'm guessing there's something special about your configuration that's involved somehow in making this happen.[/quote]

That's what I thought too. But it seems to be a [_known bug_]("https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/289655").

> Binary package hint: file-roller

When extracting multi-archive rars containing a single entry, file roller stays at 50% during the extraction.

File roller appears to be keying off the number of entries in the archive to populate the progress bar, rather than the number of archives in the set. This is somewhat disorienting because the progress stays at 50%.

In this case, either the number of rar files in the archive set should be used, or the progress bar should be put in indeterminate mode.

> Michael R. Head wrote on 2008-10-28: (permalink)

* Screenshot-Extracting files from archive.png (13.6 KiB, image/png)

This is new in intrepid. I believe before intrepid, the progress bar would be set in indeterminate mode. Here is how to reproduce:

1) find a large file, such as the ISO for intrepid
2) rar it into a multi-volume archive:
 rar a -v10240k intrepid.rar intrepid.iso
3) right click/Extract Here...
Note that the progress bar stays at 50% during the duraction of the extraction (see attached screenshot).

It's an annoying bug if you extract these type of files on a regular basis, never knowing when it's going to complete.
And for new Ubuntu users, this makes the OS seem a bit more unpolished.
I'm sure it will be fixed though. Marking this solved.

---

### Post by SamNSane on 2008-12-06
I'm glad you posted what you were able to turn up by doing research. I used Intrepid briefly but found that I had too many issues with it to allow it to be used on my admin boxes, so went back to Hardy.

I might not have seen the bug anyway, since I don't usually use archives that meet those specific criteria, though I'd be interested to see if there are nuances in the behavior with archives that have a few large components and many small ones.

Thank you again for posting the information. Some of the more useful data posted on the forum comes from folks who ask a question, and then answer it for themselves.

---

### Post by 09buntu on 2008-12-06
Thank you for your kind response.

I'm also having things not working properly in Intrepid that worked fine in Hardy (webcam for example, and graphics driver for an older laptop).

Trying to figure things out though.

---


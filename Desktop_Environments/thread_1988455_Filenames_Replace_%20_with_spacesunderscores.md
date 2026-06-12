---
title: "Filenames: Replace %20 with spaces/underscores?"
date: 2012-05-27
forum: Desktop Environments
---

### Post by cognaq on 2012-05-27
Is there any way to batch replace the "%20", which at some point of transfering files over the Internet, appeared on Ubuntu. On Win7, downloading the files preserves spaces. Also, it seems to be the case with only some files.

E.g."A.1.%20QEII%20Mean.ppt" is to become "A.1. QEII Mean.ppt" or "A.1._QEII_Mean.ppt" or "A.1.QEIIMean.ppt" even.

---

### Post by t.rei on 2012-05-27
I'm having that very same issue when downloading using firefox. It works "properly" when using chromium-browser. 

Interested in a solution that preferably fixes firefox behavior. It used to work just fine.

---

### Post by irv on 2012-05-27
I found this answer by doing a web search.
> Since spaces are not allowed in a URL, the %20 represents a space. If you right click on a link to the file, you should be able to save the file with spaces instead of the %20's. But if you load the file in your browser and then try to save it, it ends up with the %20's.
I check some of my files on my server in Firefox and Chrom and they both have the %20 in them.

---

### Post by cognaq on 2012-05-28
> **irv said:**
> I found this answer by doing a web search.

I check some of my files on my server in Firefox and Chrom and they both have the %20 in them.

After some experiments, I can confirm this behaviour. On both Firefox and Chromium.
Furthermore, I downloaded a large amount of files using Firefox on Windows 7, then I archived them and uncompressed them on Ubuntu, they also had the %20 instead of spaces. On Win7 they hadn't.

So, is there any way to solve this without manually changing filenames (300+ files)?

---

### Post by Lars Noodén on 2012-05-28
You might be able to use [rename](http://manpages.ubuntu.com/manpages/precise/en/man1/prename.1.html) if you can figure out the right regular expression.  Test on small batches first.  I would guess that something like this might do it:

```

rename 's/%20/ /' *

```

---

### Post by nothingspecial on 2012-05-28
> **Lars Noodén said:**
> You might be able to use [rename](http://manpages.ubuntu.com/manpages/precise/en/man1/prename.1.html) if you can figure out the right regular expression.  Test on small batches first.  I would guess that something like this might do it:

```

rename 's/%20/ /' *

```

The -n option of rename will show you what it would do without actually doing it, which is useful for testing

```

rename -n 's/%20/ /' *

```

---


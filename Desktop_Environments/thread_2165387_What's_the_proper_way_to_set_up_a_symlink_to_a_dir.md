---
title: "What's the proper way to set up a symlink to a directory on a different drive?"
date: 2013-08-04
forum: Desktop Environments
---

### Post by Baasha on 2013-08-04
Hi,
I am running vs.13.04 on a 64 bit machine with an SSD and two HDDs (with Raid 1).

I want to save my SSD from wear and tear so I have all my data files on the HDD.  I want to have a symlink in the home directory called Data which will point to the Data directory on the HDD.  I used the following to set it up:
```
ln -s "$(/media/bob/Data)" ./Data
```
I get an error that says there is no such file or directory as Data.  From what I have read, if you try to link to a directory that already exists, the link will end up in that same directory, but that didn't happen either. So now I am confused.

What is the proper way to do this?

---

### Post by steeldriver on 2013-08-04
The problem is with the 1st part of your command not the second 

[FONT=courier new]$(/media/bob/Data)[/FONT] tries to *execute */media/bob/Data and return the result, try it with the plain filename

```
ln -s /media/bob/Data ./Data
```

You may need to remove a broken link if your previous try created one, or use -s**f** to force the new link

---

### Post by Baasha on 2013-08-04
Thx Steeldriver, that worked perfectly.  Now that I am thinking about it, there are a lot of configuration files in home (presently on the SSD) that will be written to a lot (like email profiles). I don't mind waiting a second or two if these could be located on my HDD also, but I found that I was not allowed to erase the home directory so I could replace it with a link.  Is this possible?

---


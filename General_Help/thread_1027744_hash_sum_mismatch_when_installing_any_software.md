---
title: "hash sum mismatch when installing any software"
date: 2009-01-01
forum: General Help
---

### Post by IronFox on 2009-01-01
I get hash sum mismatch when ever I try to download any piece of software after I added the Medibuntu repo.  Can i fix this without removing the repo?

EDIT: I unchecked the repos and I still get the error

---

### Post by ajgreeny on 2009-01-01
Try using a different server for the downloads by going to *System > Administration > Software Sources* and either choose one nearest to you or "other" and let the system find the fastest.

---

### Post by IronFox on 2009-01-01
been there, done that, still no go.  it dosent seem to matter which server i use i keep getting the same error.

I cant even download the files with http and install them, says corrupted file system

---

### Post by ajgreeny on 2009-01-02
Are you certain you enabled the correct medibuntu repos for your ubuntu version?  It is quite easy to use the wrong line in the instructions on the medibuntu page, and install the hardy repos for intrepid, for example.  I would have expected that the problem would have corrected itself when you disabled these repos, but I can't think of anything else to suggest, other than making sure you have updated your sources with ```
sudo apt-get update
```

---


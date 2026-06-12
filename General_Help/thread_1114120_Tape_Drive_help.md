---
title: "Tape Drive help"
date: 2009-04-02
forum: General Help
---

### Post by Trinimuse on 2009-04-02
Guys, I have an 8mm tape drive attached to my UbuntuStudio pc.  I want to just get a list of the files on the tape.  That is, I want to read the tape and just get a list of the filenames that I can paste into a text file.  Any ideas?  Any additional info that might be helpful just let me know.  Thanks in advance.

---

### Post by dcstar on 2009-04-02
> **Trinimuse said:**
> Guys, I have an 8mm tape drive attached to my UbuntuStudio pc.  I want to just get a list of the files on the tape.  That is, I want to read the tape and just get a list of the filenames that I can paste into a text file.  Any ideas?  Any additional info that might be helpful just let me know.  Thanks in advance.

If the tape was created by cpio, then this will help, otherwise **you** have to know what created the tape.

```
man cpio
```

---

### Post by HermanAB on 2009-04-02
Install 'mt' the magnetic tape utilities.  Then, well, uhmmm, have fun...

Tapes are rather last century and on the whole best avoided.

---


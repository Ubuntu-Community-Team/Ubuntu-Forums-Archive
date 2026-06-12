---
title: "how to copy files with non-English characters in filename"
date: 2012-01-21
forum: Desktop Environments
---

### Post by Qmanisambushed on 2012-01-21
Hi everyone.
I am trying to copy some files which they have non-English characters in their filenames. but I get an error "invalid encoding" while copying them. how can I copy them?
note: non-English characters doesn't display correctly. there is '&#65533;' instead of every non-English character.

---

### Post by Viman on 2012-01-21
Are you using the command line?
I think that file managers can handle it pretty easily through good ol Ctrl+C Ctrl+V.

May I ask what kind of characters are these?

---

### Post by Qmanisambushed on 2012-01-21
> **Viman said:**
> Are you using the command line?
I think that file managers can handle it pretty easily through good ol Ctrl+C Ctrl+V.

May I ask what kind of characters are these?
I used command line and Ctrl+C Ctrl+V. both of them get same error.
these are Turkish characters.

---

### Post by sudodus on 2012-01-21
What if you quote them for example
```
cp 'üx.txt' uex.txt
``` or
```
cp "üx.txt" uex.txt
```

When cutting & pasting I guess it depends on the encoding/decoding of the two programs. If that differs, you will get different characters.

---

### Post by Qmanisambushed on 2012-01-21
well when I am trying to copy them into Desktop or similar places there is no problem but when I want to copy them to my hard or my phone I get error.

---

### Post by Viman on 2012-01-21
Strange. I've moved files written in Japanese both through Nautilus and CLI flawlessly.

Perhaps installing/updating the Locales and Language support for Turkish should help?

As a workaround, you could rename the files temporarily just for the act of transferring.

---

### Post by sudodus on 2012-01-21
> **Qmanisambushed said:**
> well when I am trying to copy them into Desktop or similar places there is no problem but when I want to copy them to my hard or my phone I get error.
The phone probably has a different encoding of the characters. What do you mean by 'my hard'? Is it an external hard disk drive? In that case, what tool do you use to read it?

Unfortunately ascii characters 128-255 are encoded differently in linux, windows and apple systems. Unicode and UTF-8 are ways to get around that problem, but it is not always applied, for example in cut and paste operations or in simple text files. But in word processor texts it usually works.

---

### Post by Qmanisambushed on 2012-01-21
I think my problem is solved. I wrote a script and delete every '&#65533;' from filenames.
Thank you every one for your attention:)

---


---
title: "problem unraring files"
date: 2009-01-24
forum: General Help
---

### Post by omegaserpent on 2009-01-24
first off, greetings to all as this is my first post.

i have unrar installed and functioning fine.
trying to extract files from a 51-part rar file with password. file viability and password are known to be correct and working for others. problem is that while extracting (it reaches to around 4.5 of 7.1 GB)it will re-ask me for the password, and starts the process from the beginning without giving me any error messages.

anyone have a clue as to what's going on?

---

### Post by dcstar on 2009-01-24
> **omegaserpent said:**
> first off, greetings to all as this is my first post.

i have unrar installed and functioning fine.
trying to extract files from a 51-part rar file with password. file viability and password are known to be correct and working for others. problem is that while extracting (it reaches to around 4.5 of 7.1 GB)it will re-ask me for the password, and starts the process from the beginning without giving me any error messages.

anyone have a clue as to what's going on?

Firstly, is there sufficient disk space on your / partition and also where you are extracting to?

Secondly, which of the unrar packages do you have installed?

---

### Post by howefield on 2009-01-24
Any time that's happened to me, it is the password that is wrong, or at least being typed wrong, have you tried copy/pasting the password to make sure you are getting it right ?

---

### Post by mb_webguy on 2009-01-24
Are you using unrar from the command line, or as a plugin to Archive Manager (File Roller)?  Also, if you're doing it in Archive Manager, are you extracting the first file in the multipart rar?

---

### Post by omegaserpent on 2009-01-24
i've tried archive manager, extract here, and terminal.
im thinking one of the files may have been corrupted during download- problem is i cant see which one it is, as it wont give me an error message.
i'll keep you posted

---

### Post by taurus on 2009-01-24
Or hopefully you don't try to unpack (or unrar) it in a vfat filesystem.

---

### Post by Mud.Knee.Havoc on 2009-01-24
> **omegaserpent said:**
> i've tried archive manager, extract here, and terminal.
im thinking one of the files may have been corrupted during download- problem is i cant see which one it is, as it wont give me an error message.
i'll keep you posted

One other possibility:

Windows doesn't tell the difference between upper and lower case.  Linux does.  So even though Windows will unrar these properly:

file.rar
file.001
FILE.002
file.003

linux won't.  

* Please note that I haven't really used Vista, so maybe Windows is case-sensitive now.  No idea (and no desire to find out). :)

---


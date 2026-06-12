---
title: "Encrypting to zip fails when p7zip-rar is installed"
date: 2009-02-23
forum: General Help
---

### Post by Ctulhu on 2009-02-23
Hi all

I am using Ubuntu 8.10 x64 and have a problem with creating encrypted zip files: I want to create an encrypted zip file so I

- highlight the files;
- right-click, and choose "Create Archive...";
- choose ZIP;
- enter a password, and click "OK" ...

The result is pasted below:

###############
7-Zip  4.58 beta  Copyright (c) 1999-2008 Igor Pavlov  2008-05-05
p7zip Version 4.58 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,3 CPUs)
Scanning

Creating archive /home/XXX/Desktop/XXX.pdf.zip

System error:
E_INVALIDARG                
###############

Now comes the interesting part: this ONLY happens after I installed p7zip-rar (so that I can open .rar files) -- before doing that, when I only had p7zip and p7zip-full installed, the encryption worked fine. So,

question 1: is there a way to be able to open .rar files (preferably, but not necessarily a GUI) but still be able to create encrypted zip file?
question 2: is this a bug or a feature (whose benefits elude me)?

Thx,
C

---

### Post by mb_webguy on 2009-02-23
You could use unrar instead of p7zip-rar.  Since p7zip-rar is independent of p7zip-full, you shouldn't lose any functionality.

---

### Post by dolman25 on 2009-02-23
I think this is a bug with archive manager, when iv got p7zip installed I cant extract a bunch of rar files. I guess the archive manager cant tell the difference between p7zip and rar files

---

### Post by Ctulhu on 2009-02-27
Ok, unrar it is then, thx a lot.
C

---


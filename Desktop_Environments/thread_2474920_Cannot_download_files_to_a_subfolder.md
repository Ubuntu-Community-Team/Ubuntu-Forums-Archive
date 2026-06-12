---
title: "Cannot download files to a subfolder?"
date: 2022-05-11
forum: Desktop Environments
---

### Post by allardp on 2022-05-11
Hello all,

I'm encountering a annoying bug in Ubuntu 22.04. For some reason I cannot download en save files to a subfolder with multiple browsers.
If I want to download a file I can save it in my Documents or Downloads folder or whatsoever, but when I want to save the file inside a subfolder which is in that folder the download fails.
I tested it with Firefox, Chrome and Chromium. All three browsers does the same on multiple installs.

More people who encountered this bug?

---

### Post by GhX6GZMB on 2022-05-11
Check your subfolders' ownership/permissions. Like this:
```
macro@macro-pc:~/Documents$ ls -la
total 1148
drwxr-x---  8 macro macro   4096 May 10 01:36  .
drwxr-x--x 21 macro macro   4096 May 11 20:37  ..
-rw-r-----  1 macro macro    177 Feb 23 00:45  4526.bck
-rw-r-----  1 macro macro     48 Feb 23 00:45  4526.dcm
-rw-r-----  1 macro macro     60 Feb 23 00:45  4526.lib
drwxr-x---  2 macro macro   4096 May 10 01:30  6910p_customising
drwxr-x---  4 macro macro   4096 Nov 27 23:43  Backup_Docs
drwxr-x--- 11 macro macro   4096 Apr  3 23:25  Electronics
drwxr-x---  2 macro macro   4096 Apr 21 21:44  Internet
-rw-r-----  1 macro macro 962616 Feb 21 01:03  Lubuntu.png
drwxr-x---  2 macro macro   4096 Mar 27 23:08 'MOC3023M (PSPICE MODEL)'
-rw-r-----  1 macro macro  87064 Mar  7 22:25  pe.png
-rw-r-----  1 macro macro  70723 Apr 11 00:20  SoftstartR1.pdf
drwxr-x---  2 macro macro   4096 Jan  1  1970  standard_snubberless_triacs_pspice
macro@macro-pc:~/Documents$
```

---

### Post by ajgreeny on 2022-05-11
Both Firefox and chromium are snap versions now and in the oast you could not download to any other folder than Downloads as the snap system forbade it.
I don't know if snaps still work like that as I removed all the snap infrastructure from my systems and now use either PPAs for chromium or the direct .tar.gz download from Mozilla for Firefox.
I can't help with chrome as I use that only on Android, never on my Linux distris.

---

### Post by GhX6GZMB on 2022-05-11
> **ajgreeny said:**
> you could not download to any other folder than Downloads as the snap system forbade it.

Really? My banning of snap makes me happier every day. :)

---

### Post by ajgreeny on 2022-05-12
As I said, things may have changed now, but it was really frustrating for me and as a consequence of the very slow first startup, along with these other annoyances of the whole snaps system, I just stopped using them to begin with, then once I realised there were alternative ways of getting the applications, got rid of the complete snap system.

So far, so good!
If things change I may have to accept snaps as one of the many ways forward but if I'm able to find alternatives that work and do not cause other problems, I shall remain snapless.

---


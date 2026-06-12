---
title: "Maintenance on Ubuntu?"
date: 2006-05-11
forum: Desktop Environments
---

### Post by here_be_mike on 2006-05-11
Hi all. Just about to move onto ubuntu from windows and want to know if theres any regular maintenance i could easily do on ubuntu like i would on windows.

Things on windows like:

Defrag
Registry clean up 
Junk file clean up
History clean up (Web history, cookies etc)


And what programs would you recomend to replace:
Nero
Winamp
Anti Virus
Firewall
Spyware clean up


Thanks all

---

### Post by Ramses de Norre on 2006-05-11
Defrag: no need for, ext3 (the linux file system) handles fragmentation way better as ntfs.

Registry clean up: no such thing I'm aware of (no need for).

Junk file clean up: what exactely do you mean by this?

History clean up (Web history, cookies etc): depends on your browser, in firefox (the default) you can do this in the preferences.


Replacements:

Nero: k3b

Winamp: xmms looks much like winamp but I prefer amarok for my music (looks and feels a bit like itunes)

Antivirus: no real need for, but if you want to protect windows computers in your network I'd advice avg (how to on the forums)

Firewall: firestarter

Spyware: no such thing on linux (yet?)

---

### Post by here_be_mike on 2006-05-11
By junk files i mean things like, zero length files, temporary files and log files that arnt needed (like install logs).

---

### Post by Ramses de Norre on 2006-05-11
Uhm temporary files are stored under /tmp/ which is cleared on shutdown.

Zero length files? How would they be created? You could make a simple script for it to search and remove them.

And logs are stored in /var/log/ but I think normally logs are overwritten each session, and many programs let you set the log policy yourself. You can watch the amount of space used by /var/log/ and delete some files if you want to.

---

### Post by here_be_mike on 2006-05-11
Thanks again Rameses. Ive no idea how zero lenght files are created but im basicly trying to find (if needed) a replacement for Iolo system mechanic junk file remover, seems to find a lot of crud on my brothers pcs when i havnt used it for a while :P

---

### Post by linuxcity on 2006-05-11
All of the above could be done with Linux or not needed for it yet. However, there is time that you want to use a Windows program, but it is not available in Linux.  You may have to learn the equivalent  program that available for Linux.
for example. I use Adobe PageMaker in Windows, which Scribus equivalent in Linux, but I do not know how to use it yet. I can use Gimp or Gimpshop for Photoshop replacement. I have to use MemoriesOnTv on Windows.
I like to learn to type Vietnamese on Linux, which SCIM is a solution, but I do not know how to set it yet. 
Instead of Dual boot I use VNC to connect to a desktop to solve something quick. When neither the solution works, I boot back to my Windows, but only when there is no other way. I have a 300GB external hdd, and it is under NTFS, so I have to plug it to Windows to transfer file for Linux do not support writable NTFS.

This forum has been very helpful to me. I was mostly searching and asking questions, but I now have enough knowledge to answer some. I'm very happy to what I have learned so far.

I started using Linux for almost 10 years now (since Red Har 4.x), but I'm a slow learner, so I only have the courage to leave the MS world behind for the last 8 months.

It was a challenge for me when I first started using Ubuntu in my daily work, but I'm slowly getting used to it.  I wish I could have as much knowledge in Linux as I do in Windows, but it takes time and practice to get there.

---


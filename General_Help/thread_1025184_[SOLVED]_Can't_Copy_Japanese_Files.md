---
title: "[SOLVED] Can't Copy Japanese Files"
date: 2008-12-29
forum: General Help
---

### Post by Kissell on 2008-12-29
I have a Ubuntu 8.04 box that has files named with Japanese characters...  I can use them and read/write them just fine on that box.  These files are stored on an EXT3 partition (if that matters).

An example is like this (if you can read this)
> 14 - X’mas&#12398;&#28310;&#20633;.mp3

I'm trying to copy those files to another Ubuntu server.  That server is also a Ubuntu 8.04 box, but it uses the XFS file system.  No matter what program I use to copy or which box I initiate the transfer on, the copy complains and will copy everything but these files with "weird" characters of kanji and hiragana in them.  

Obviously these characters are outside the correct English way of doing things and don't normally exist in the alphabet...  So the transfer complains with an error like "14 - X’mas ?.mp3 can't be copied" so its like it can't even read those characters.  

How do I fix that?  I need to be able to copy these files off this server (I can copy them just fine inside the original server).  I need to somehow make the new server understand those characters, or get some sort of massive recursive file renaming utility that will leave all files in their original path and automatically strip their filenames of any invalid characters that can't be read.  I'm interested in knowing how to do both, as I'm sure I'll run into this problem again.

---

### Post by Kissell on 2008-12-30
Okay, I could just not see the japanese characters or read those file names because I had mounted an SMB share with "smbfs", and they don't work when I was doing that...  

But, I noticed that if I browse the network via normal SMB shares, like smb://servername then the files show up just fine that way, and I can copy them...  

I think this is because when I mount a drive with smbfs I need to give it some sort of parameters like utf-8 or something like that, but nothing I tried worked.  oh well, i'll just not use smbfs for this transfer.

---


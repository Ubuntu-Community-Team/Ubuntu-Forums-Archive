---
title: "Windows 7 style libraries?"
date: 2014-10-23
forum: Desktop Environments
---

### Post by munkifisht on 2014-10-23
I have been looking for a solution to this but have yet to find anything useful. One thing that I find incredibly good with Windows 7 was the introduction of libraries. Windows libraries, in case you done know sort of work like symlinks. They amalgamate the contents of different folders into a virtual folder.


Why would this be useful? Well, in my example, I have 10 HDDs, all of them with a variety of media organised into different catagories. Frankly it's a pain to have to sift through drive after drive to get what I want. Libraries remove this trouble, so for example all the folders that have pictures in them are lumped into one virtual folder and this is where I go when I need to find something.

---

### Post by TheFu on 2014-10-23
Libraries only work in the GUI - never from cmd.exe.  Libraries are NOT part of the file system which makes it really hard for non-GUI programs or scripts to access them. That doesn't seem smart to me, but on Windows, I'm like a penguin in the desert and expecting things to work the UNIX way is extremely frustrating to me.

So there are multiple ways to achieve similar outcomes with non-standard Linux file systems.  I don't use these, but many people do - web search for **unionfs vs** to get some ideas. I think there are at least 5 options.  The media center guys will know them all.  If you use these things, please, please, please, have excellent backups - especially if you decide on LVM and spanning volumes.  Don't be the guy who comes back next month when 1 drive in the 9 drive LVM volume dies and all the data across all of those drives is gone (and not have at ;east 1 backup copy).

BTW, if you know the file name - you can use **locate** to find them almost instantly on disk and if you want to search inside files or metadata **recoll** is amazing.  Personally, I have a script that can be run from anywhere on the network that searches data partitions across all the machines to locate files. It also searches a DB with off-line storage too.

Trying to do things the Windows way isn't always the best idea on a different OS.  Regardless, I hope the flexibility in Linux serves what you need.

---


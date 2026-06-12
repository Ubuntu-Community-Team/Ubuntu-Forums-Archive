---
title: "User permissions and an external hard drive"
date: 2009-05-29
forum: General Help
---

### Post by tabor on 2009-05-29
I'm running the latest version of Ubuntu and I currently have an external HDD connected to it.  It is a desktop and here in about a month I will move in with a few roommates.  I am considering placing my desktop in the living room area instead of my room, because I have a lap top I can use in my bedroom.

I would like to have the external HDD hooked up to the desktop because that is where all my music/video files are at.  I also have some personal files on this HDD that I do not wish for anyone to view, however I would like to keep them on the HDD.

My question...is there a way to set it up to where only my account and the root account have read/write permissions to all files, and other users only have read permissions to certain folders, but not all?  Is this something that can be as simple as using chmod?

---

### Post by pytheas22 on 2009-05-29
Sure, it's very easy to do this using simply chmod.  Just make sure that your private files are owned by root and that their permissions are set to 700, which will give the owner read/write/execute permissions, but make the files invisible to all other users on the system (except root, of course).

Also, I'm assuming that you're not mounting the hard disk over the network, since you don't mention that.  If you were doing something like that, it might make things a bit more complicated; I'm not sure.  But if it's just a local device, a command like 'chmod -R 700 /private/directory' should work fine.

---


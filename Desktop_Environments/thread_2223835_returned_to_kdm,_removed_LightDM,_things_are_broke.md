---
title: "returned to kdm, removed LightDM, things are broken"
date: 2014-05-13
forum: Desktop Environments
---

### Post by linbu2 on 2014-05-13
Kubuntu 14.04, I changed back to KDM after upgrading to 14.04 (from 12.04) and having LightDM thrust upon my machine.  My home/me/ Documents and Downloads and other sub-directories are gone.  Firefox, though installed, has no launcher icon (I have fixed that).  Thunderbird seems to think I just installed it, all of my accounts, add-ons, mail messages are gone.  All of my Documents are missing.

What the....???  How do I get all of that back?  There's a script in my home directory now: "Access your private data desktop".  Now (possibly as a result of clicking it), there are many encrypted directories under my home.  How do I convert those back to my familiar directories and files?

Why did this happen without any permission from me?  I don't get it- we are forbidden from logging into a GUI as root for our own protection, and that makes sense- but when I follow the rules and innocently make a change, a garbage typhoon ransacks my machine without permission or even warning.

I just want to get something done in a friendly computing environment.

Thanks for your help.  I sure do need it!

---

### Post by steeldriver on 2014-05-13
You apparently chose to encrypt your home directory when you installed, and it looks like the switch from kdm to lightdm has broken the *automatic* decryption on login

I've never bothered to encrypt my home dir so I'm not familiar with the hooks for the automatic decrypt (it's possibly just a keyring thing) but I'm sure if you wait a while someone will be able to help you sort it out

It's nothing to do with being "forbidden" from logging in to the GUI as root

---

### Post by linbu2 on 2014-05-13
Many thanks, I sense now that I panicked too soon and too much!

---


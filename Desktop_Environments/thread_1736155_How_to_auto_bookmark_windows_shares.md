---
title: "How to auto bookmark windows shares?"
date: 2011-04-22
forum: Desktop Environments
---

### Post by Linux ubunu on 2011-04-22
Hi
Sorry if this question is silly to you. I am really new guy into Linux only few days experience. 
 
_**I will explain what I have:**_
ubuntu 10.10 => joined into Active Directory Domain (test.net)
I can login using AD users using Likewise-Open
I have in my Windows environement Home Folders (Shared by AD) for every user and it apears as Z: Drive automatically when I loged in using windows machines.
 
**I need same setup using ubuntu desktop to show these Home Folders for every users automatically when he logs in.**
 
Thak you in advance.

---

### Post by cipherboy_loc on 2011-04-22
Try gvfs. You can set up each user's mounts (username + password), and then on login you can run the gvfs-mount command and have it mount the selected shares. Login credentials are stored in the keyring.

Edit:
BTW, I don't know the exact commands and steps necessary, but I remember reading about it online. Try google.
And welcome to the forums!

Cipherboy

---


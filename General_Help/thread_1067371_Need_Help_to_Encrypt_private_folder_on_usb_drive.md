---
title: "Need Help to Encrypt private folder on usb drive"
date: 2009-02-11
forum: General Help
---

### Post by xwisdom on 2009-02-11
Hello,

I'm trying to encrypt a folder on a usb drive but getting the following error:

Attempting to mount with the following options:
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=[*clipped: sig was here*]
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? n
Aborting mount.
Error processing sig; rc = [-22]
Error mounting eCryptfs; rc = [-22]; strerr = [Invalid argument]. Check your system logs; visit <http://ecryptfs.sourceforge.net/ecryptfs-faq.html>.

I followed the instructions on this site:
[http://www.ubuntugeek.com/how-to-create-a-private-encrypted-folder-on-ubuntu-810-intrepid.html](http://www.ubuntugeek.com/how-to-create-a-private-encrypted-folder-on-ubuntu-810-intrepid.html) 

and replaced the ~/Personal with /media/disk/personal

Any ideas? Can't we create more than one private folders?

PS. I'm using xubuntu 8.10

---

### Post by bodhi.zazen on 2009-02-11
since this is the first time you have attempted to mount the encrypted directory, did you try answering the question y (yes) rather then n (no) ?

---

### Post by xwisdom on 2009-02-11
Hi,

Thanks for the reply.

I did try entering "y" but it still failed with same "Error mounting eCryptfs; rc = [-22]; strerr = [Invalid argument]. "

---

### Post by xwisdom on 2009-02-19
Can anyone help me with this issue pleaseE?

---


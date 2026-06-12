---
title: "Trying to recovery home - Lost passphrase"
date: 2016-04-03
forum: Desktop Environments
---

### Post by beppe_rm on 2016-04-03
Hi all,

I'm trying to recovery the home of 14.04 on laptop with live USB 15.10. I followed this:

[http://ubuntuforums.org/showthread.php?t=2215496](http://ubuntuforums.org/showthread.php?t=2215496)


I tryed:

```

ubuntu-gnome@ubuntu-gnome:~$ sudo ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...
find: File system loop detected; `/sys/kernel/debug/pinctrl' is part of the same file system loop as `/sys/kernel/debug'.
ubuntu-gnome@ubuntu-gnome:~$ 

```


I don't know what it really means.

Furthermore, I don't have the passphrase, but only the login pw; I saw this:


"Recovering Your Mount Passphrase

In the event that you did not write down your mount passphrase, you may be able to recover it by decrypting the file  /home/username/.ecryptfs/wrapped-passphrase  **using your login passphrase.**

     ecryptfs-unwrap-passphrase /home/username/.ecryptfs/wrapped-passphrase
    Type your login passphrase to reveal the mount passphrase 

If your login passphrase matches the passphrase used to encrypt the wrapped-passphrase file, your mount passphrase will be written to screen. Record and protect this data accordingly.

If you have lost your wrapped-passphrase file, and you did not record your mount passphrase, it is impossible to access your encrypted data."

So I insert the login pw:

```

ubuntu-gnome@ubuntu-gnome:~$ ecryptfs-unwrap-passphrase /home/username/.ecryptfs/wrapped-passphrase
Passphrase: 
Error: Unwrapping passphrase failed [-2]
Info: Check the system log for more information from libecryptfs
ubuntu-gnome@ubuntu-gnome:~$ 

```

Where is the error?

Many thanks

---

### Post by BadBBilly on 2016-04-09
> **beppe_rm said:**
> 


Hey man,
                I am in the exact same boat, am attempting to use Ubuntu Live USB to access my encrypted data, i have not found any articles on google except your couple of posts.
If i find anything out i will notify here ASAP.

cheers,

---


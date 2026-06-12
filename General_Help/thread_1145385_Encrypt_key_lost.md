---
title: "Encrypt key lost"
date: 2009-05-01
forum: General Help
---

### Post by Xun on 2009-05-01
Hi,

Today, I made a big mistake: I erased my / but I forgot my drive was encrypted since the Jaunty's Alpha 3.
(the key was in the /var/lib/ecryptfs/user)

I didn't write the key down because I didn't see it. That's why I forget my drive was encrypted.

I re-installed Ubuntu 9.04 with on 
- ext4; sda5 /
- ext3; sda3 /home

I can't access to my folders, because of I haven't got the key, so the access.
I created a new user "alex2" with the same password to be able to use my computer. The encrypted folder's user's name is "alex".

I use photorec (I'm not sure of the manner I did), trying to rescue some deleted files, and maybe the key.
Now I have 1486 folders, each with 500files inside. All with crazies names; for examples "f94139568.txt".

How can I do to find my Key, and rescue my last 300photos (trip in Wien)  which are not saved on my second drive ?

Thanks for your help,
Still, excuse my English :s

Xun

---

### Post by Xun on 2009-05-02
up :( ...

Xun

---

### Post by danwood76 on 2009-05-02
I havent ever encrypted a volume before but I would have thought that if you have lost the key you are pretty much stuffed.
The encryption is there to protect your data so I wouldnt have thought there would be an easy way round it.

If the key was stored within a file and you possibly have that file in those recovered documents you could grep through them and search for your username and hope you get lucky.

---

### Post by Xun on 2009-05-02
How can I be sure I correctly use photorec ?

I have 1483 folders ( recup_dir1 etc...), research "keyring", "login" or "alex" has no anwser ...

I believed photorec was able to rescue my deleted files ...

Xun

---

### Post by danwood76 on 2009-05-02
Doing a plain file search wont give as good results as the program grep will.
Grep will search the files contents for it as well as filenames.

I would seriously doubt you will find the key though.

Normally before I install (or reinstall) an OS I make backups of all important data so things like this cant happen.
Unfortunatly you will have learnt this the hard way!

---

### Post by Xun on 2009-05-02
I would like be sure I can't do anything else before installing a new Ubuntu.

With regards to make Backups, I'm 200% agree with you. I do about every week-end backups but I forgot my photos weren't in my backup disk ... That's why I'm so nervous about saying "good bye" to my photos ...

Xun

---

### Post by Xun on 2009-05-03
I have an another solution !!!

I remember that I did a DVD with my photos for watching them on TV but I used that DVD to burn a geexbox image (20mo on 300).

I made a quick formatage so, can I rescue my photos from that DVD ??
If I do, how can I make it with Gnu/Linux's or Windows software ?

Thanks a lot !

---

### Post by unutbu on 2009-05-03
Am I correct in understanding that the DVD is a read/writable DVD, and you have done a quick format of the DVD?

If so, you might be able to recover the pictures using photorec
```

sudo apt-get install testdisk
sudo photorec
```

---


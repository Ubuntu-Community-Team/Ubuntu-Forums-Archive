---
title: "Lost Password"
date: 2006-10-08
forum: Desktop Environments
---

### Post by Lord Of The Mings on 2006-10-08
I have a password problem, i just installed Ubuntu Drake, and i set my password as "1", and my username as "master". It finished installing, but now it won't let me sign in using the above user name and pass ](*,) . i have tryed every tweak of spelling, but it won't accept it. any help?

---

### Post by arkangel on 2006-10-08
well lets see if this works (experiment )

-reboot and start with the live cd 
- when the live cd is loaded , mount your partition  in /mnt , open a terminal 
**   sudo mount /dev/hda1  /mnt  **   
  you have to know  where your linux partiton is ( hda2 , hda3..)
if the hda1 is not your linux parttion  umount and mount the next one then see ,if hda2  is not    your linux parttion[I]  mount hda3 and so on , before mounting a new partion you have to unmount the previous one 
[/I], for unmount a partition 
 **  sudo umount /dev/hda1**

-once you have mounted the right partiton, in a terminal 
**sudo gedit /mnt/etc/shadow**

and look for a line 
master:**$1$1eb/cwSV$kgA6gpASxCXGhsU4rQKm/.**:13405:0:99999:7:::
in bold face is your password encrpited 
now paste  this  **$1$ZVQmeWuq$naVSjHAYm46/iAP2mol.k/**, between the :: instead of the previous one 
this is the encripted version of **ubuntu **  , your new password is now  ubuntu (if the algo for generating pass is the same in your computer thatshould work )

reboot  and username master , pass: ubuntu 

if that works   in a terminal  type
**passwd**

and as far as I know   UNIX PASSWORD SHOULD BE AT LEAST  6 CHARACTERS LONG

---

### Post by arkangel on 2006-10-08
just for clarification 
in the same manner you open the /etc/shadow open the /etc/passwd
and look for a line like this 
master:**x**:1001:100:master,,,:/home/master:/bin/bash
the x is really important  if you see a * or a ! your account is disabled  put a x instead

---

### Post by anaconda on 2006-10-08
Yep..
OR
Just select recovery-mode from grub, and then you are at command-line with root rights and you can change master:s password by
```
passwd master
```

Or you could just make a new user by 
```
adduser newuser_name admin
```
so that the newuser_name would also have admin rights.. eg it can use sudo-command..

---

### Post by arkangel on 2006-10-08
> **anaconda said:**
> Yep..
OR
Just select recovery-mode from grub, and then you are at command-line with root rights and you can change master:s password by
```
passwd master
```
....

so mine will work ?  i  always wanted to know if the algorithm  was the same for all computers

---

### Post by anaconda on 2006-10-08
Yep..
Your solution will also work.
Didn't know, so I had to try it.. and it worked.

Interesting. I would have guessed that the algorithm would have been different...

---

### Post by Lord Of The Mings on 2006-10-08
I think i'll try anaconda's way first, as i'm not really used to working with unix coding, and i really am not good with partitions.

---

### Post by armaguy on 2007-08-02
Cool! That's the exact solution I was looking for...

Freshly installed ubuntu and left it for 1-2 weeks, used a new password.... and shouldn't!

I was also wondering, how can i decrypt the algorithm to find the original password back?

Thanks!:guitar:

---

### Post by aysiu on 2007-08-02
> **armaguy said:**
> Cool! That's the exact solution I was looking for...

Freshly installed ubuntu and left it for 1-2 weeks, used a new password.... and shouldn't!

I was also wondering, how can i decrypt the algorithm to find the original password back?

Thanks!:guitar:
There's no easy way to decrypt the password to get the original back. Your best bet is to just reset the password to a new one.

---

### Post by armaguy on 2007-08-02
:(
Bou houu
I really wanted...

Well... Also i was curious about knowing how arkangel did found out that ubuntu was that chain of number, so I thought arkangel knew how to decrypt it.


Well it's still very fine :D I got a super fast answer, thank you very very much ubuntu community!

---

### Post by aysiu on 2007-08-02
I don't think arkangel *de*crypted the password. I think arkangel *en*crypted the password by changing her or his own password to *ubuntu* and then seeing what showed up in the /etc/shadow file.

Without trial and error and a clever cracking program, you can't just look at the encrypted string in /etc/shadow and tell what the plain text password is.

---

### Post by badseed on 2007-08-08
Hi.
Isn't this a bit unsecure?????

If my laptop is stolen it's easy for someone to change my password and use it......


Thanks
João Mendes

---

### Post by mcduck on 2007-08-08
> **badseed said:**
> Hi.
Isn't this a bit unsecure?????

If my laptop is stolen it's easy for someone to change my password and use it......


Thanks
João Mendes

The very second anybody gets physical access to your computer your security is gone. No matter what OS you use and what passwords you have. Unless you decide to encrypt all your disks any Live-CD will give full access to anything on the computer.. And even encrypted disks won't keep your data safe forever, it just takes a while to decrypt.

But if you like, you can set Grub to ask a password to access the recovery mode. Then you should also set the password for using Grub command line, and of course disable booting from CD's and USB sticks & set BIOS password.

---


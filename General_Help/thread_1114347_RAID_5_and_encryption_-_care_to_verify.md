---
title: "RAID 5 and encryption - care to verify?"
date: 2009-04-02
forum: General Help
---

### Post by Denmaru on 2009-04-02
Greetings!

After reading quite a lot about building your own Ubuntu-Fileserver for Mac Networks, I wanted to get input on a plan of mine.

Basically, I want to know how encryption using LUKS and a RAID 5 play together, especially considering the growth of the RAID on a 8.10 system.

My plan is to...

1) create a RAID-5 using 3 HDDs. This is fairly easy using mdadm. The Result is --> /dev/md0.

2) encrypt /dev/md0 using LUKS. According to [this guide]("https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid"), all it takes is a ```
luksformat -t ext3 /dev/md0
```
But will it use AES-256bit encryption, and the much faster i586_AES version on 8.10?

3) After all said and done, I merely add the encrypted RAID by using the UUID of *the encrypted RAID* to /etc/fstab. 

4) Now, here comes the part I'm a bit afraid of.

Will a "mdadm --grow /dev/md0 etc. pp" harm the encryption in any way? And is there anything I should take into account before letting my RAID grow?


I'd also like to apologize if this isn't the correct forum for this question - I couldn't decide wether to post it in security or in server.

---

### Post by Menschenfresser on 2009-04-03
I don't think it will make any problems but it would be nice to know for sure (I am planing to build a home file server with such a setup). One easy way to test this is to make a RAID with the loopback device and using some files instead of a real partition and then trying growing, shrinking, etc. Somehow I never managed to find a quite evening to find out!

---


---
title: "Truecrypt 6.1 gets very slow on large file copy"
date: 2009-03-04
forum: General Help
---

### Post by mogliii on 2009-03-04
Hi,

Ubuntu 8.04

recently I was copying a large file (60 GB dd-image) from an unencrypted internal ext3 harddisk to a Truecrpyt encrypted external harddisk (ntfs, usb2).

It started with 28 Mb/s but got slower gradually. At the end  (After maybe three hours) nautilus showed 8 mb/s, but might have been even slower as it is averaged over the whole process. I did not perform any other task during the copy process.

Is this an TrueCrypt issue? I mean I already spent 10 hours formatting the disk with truecrypt, so copying should be fast, and it shouldn't have to rely on the random generator.

Does anyone have an idea?

Hardware was Athlon 64 x2, 2 GB ram and MSI Neo2-Digital Motherboard, so pretty powerful.

---

### Post by Slim Odds on 2009-03-04
> **mogliii said:**
> 
Is this an TrueCrypt issue? I mean I already spent 10 hours formatting the disk with truecrypt, so copying should be fast, and it shouldn't have to rely on the random generator.

I guess you don't understand how disk encryption works.

1) It must randomize your entire file space so that used space is not distinguishable from unused space (that's why creation takes a while).

2) When copying a file, it must randomize the entire file (that's what encrypted files spaces do).

Any other questions?

---

### Post by mogliii on 2009-03-04
> **Slim Odds said:**
> Any other questions?
>> Yes.

First of all: If I understand you correctly then TrueCrypt Volumes are unsuited for large file backups (dd), as they need random numbers, and the entropy of the linux generator is not large enough to encrypt, lets say, 60 GB, with full speed.



Now about the encrypting process itself: That is how I understand it.

1) I buy a new harddisk and create a Truecrypt partition. The whole harddisk is being filled with random data (takes a while).

2) I copy a file. In that moment the encryption algorithm generates from the data that I want to encrypt, together with my unique password, combinations of bits. These look like random data, and can not be distinguished from the random data from step 1)

3) Only with the correct algorithm and my unique password, the combinations of bits from step 2) can be decrypted to my original data.

So why do I need random data when encrypting?

---

### Post by Gizenshya on 2009-03-04
depends on what you mean by "when encrypting."  did you mean with regardsto passwords?

encryption-grade algorithms are generated to make the password (more accurately, the encryption key) much harder to crack, as dictionary attacks and whatnot are useless.  In other words, it keeps the statistical possibility of getting the combination correct by using simple random brute force attack for any single guess as close to equal to 1/p as possible, where p is the total possible number of combinations.

if you are using a password AND hash to get the encryption key (which you seem to have implied)... I'm sorry to tell you, but you might as well not even have the thing encrypted.  Process is just as important as the encryption algorithm.  If they get the hash file, all they would need to do is brute force attack it to get your password, which is certainly far weaker than the encryption algorithm, in order to get your encryption key.  In other words... just guess your pass and all your effort is in vein.  AND, thats a best-case scenario.  That is assuming it's not in your RAM, or cached somewhere (which it probably is), or blah blah blah.  If they get your password and not your hash, you might be ok, tohugh (depending on how good the algorithm is... which really means how random it is- 'true' aka simple random or pseudo-random).  guard that hash mate lol.  my suggestion is have it on a secure USB key that is made for such a purpose.  if it's just a file on your computer (which, from what you've said, is the case), you're screwed.  lot of wasted effort, eh?

my point is... don't get confident.  many people do.  this is why gov documents get spread all the time, people who use expensive software incorrectly.  Just the other day encrypted pentagon files were released because someone made a stupid mistake with encryption.  you've been warned

have a nice day

---

### Post by Gizenshya on 2009-03-05
ohh, and by the way...

don't know if this needs to be said, but with all the trouble it takes to keep a hash safe (and thus the encrypted data safe), it is pretty easy to lose it.  lose the hash and even you can't get to the data, even with your pass.

it's a heck of a lot of work, and there is always that human component of misplacing a hash and getting it lost or stolen, or both lmao

and that's still only some of the problems.

---

### Post by Xebec on 2009-03-21
I have similar problem here. I'm formatting 1.5 terabyte WD (not that buggy Seagate) harddrive with Truecrypt, and the performance gets progressively worse with every percent. It started at about 100 MBps, and now, at about 65% I get only 28 MBps. Yes, hard drive geometry has some effect on performance - tracks are being written from the outside in. But it should not be that dramatic. Yesterday I formatted the HD without TrueCrypt - did not have that performance degradation at all. I think it's some internal Truecrypt bug.

BTW SMART shows that the HDD is perfectly fine.

---

### Post by mogliii on 2009-03-23
Hi,

when formatting that is pretty normal. It's also described in the truecrypt manual, that you should allow up to one day.

The point is, that the random data pool of the linux kernel is used to format the partition. This pool is filled using the random movement of mouse, key strokes, process times, memory usage and so on.

This pool gets empty after a while though, reducing the speed of random data available.
So don't worry.

The original thread is about copying large data into the truecrypt volume **after** formatting.

---

### Post by wishy.washy on 2010-01-22
Hi to all,

hardware:
lenovo X300 (1,2 core2duo, 4gb ram...)
2,5 inch sata 500 gb (ntfs)
truecrypt container formatet in fat 32

software:
ubuntu 9.10 
truecrypt 6.3


I have the same performance problems, but in my case writing on my truecrypt container is even slower than in your cases. 
If I copying files in my container, tthe transferrate will be around 3 MB/s. Maybe it's because of the formatting of my hard disk and my container. 
Maybe is there anyone who has a guess, how to speed up writing at the truecrypt container...would be great :)

greetings

---


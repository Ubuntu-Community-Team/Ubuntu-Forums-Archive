---
title: "Writing to NTFS via network"
date: 2005-11-09
forum: Desktop Environments
---

### Post by jongkind on 2005-11-09
My machine is networked to 2 other machines. As expected I can read and write to a machine with Windows '98 OS. What surprised me is that according the (shared) folder properties of another machine with Windows XP I have write permissions. I did n't try it out yet, since I'm concerned that I damage the integrity of the NTFS file systems if I actually write something to that folder via my Linux machine. 

Any thoughts on this?

Cheers, Herman

---

### Post by Kyral on 2005-11-09
NTFS Writing on Linux is very sketchy right now. I wouldn't try it

---

### Post by earobinson on 2005-11-09
What I would do if you are worried about breaking something is make a new ntfs partition on that computer, share it, then write to it.

My guess is that when a drive is shaired on a network the file type is irrelevant because computer A asks computer B what files it is sharing and computer B says file1, and file2. But computer A never dose any reading. In my mind the same would apply to writing. (I hope this makes a much sence to you as to me)

Think of it this way. If you tell a some one to write the sentence "I love ubuntu" and they write it in german. Then two weeks later you ask them what you had them write down, they read it and do the translation for you you never need to understand german to read or write.

This is all a guess. I COULD BE FLAT OUT WRONG

If the computer is really important I wouldent even try this

---

### Post by DrBair on 2005-11-09
Its perfectly safe... well as safe as windows writting it anyway because windows is writting it!

The windows drivers are doing all the writing, you're just talking to it over a network protocol which linux has down pretty good with samba.

I've always thought about having a really stripped down windows 2000 VM running in QEMU and writing to NTFS through a samba mount to it... Not the most efficient setup, but better than what we have at the moment and very  simple.

---

### Post by earobinson on 2005-11-09
[QUOTE=DrBair]Its perfectly safe... well as safe as windows writting it anyway because windows is writting it!

The windows drivers are doing all the writing, you're just talking to it over a network protocol which linux has down pretty good with samba.

I've always thought about having a really stripped down windows 2000 VM running in QEMU and writing to NTFS through a samba mount to it... Not the most efficient setup, but better than what we have at the moment and very  simple.[/QUOTE]
That was my guess, you said it better.

jongkind if you do try this let us know how it goes

---

### Post by ianpeters on 2005-11-09
Yes, I can confirm that writing to a NTFS-partition via network is perfectly safe. I do it everyday from my laptop to my main PC with Windows 2000.

Please, don't confuse this with NTFS-write support on a local disk which IS sketchy and may not work.

Summary: Network = SAFE!!
              Local drive/partition = NOT so safe

Cheers!

---

### Post by jongkind on 2005-11-09
Thanks for these replies. This makes life somewhat easier for e.g. data backup on a Windows network drive and sharing of data with Windows XP users.

Thanks, Herman

---


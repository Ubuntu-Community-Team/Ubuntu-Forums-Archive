---
title: "Recover encrypted folder in Ubuntu 10.04"
date: 2010-05-15
forum: Desktop Environments
---

### Post by Kikin-sama on 2010-05-15
Hi everybody! I'm in a bit of a pickle right now. I had a previous installation of Ubuntu 9.10 with an encrypted home folder on a separate partition. Recently I installed the brand new 10.04 replacing the old 9.10 (i.e. on formatted and installed) and selected the same partition for my home.

The problem is that I cannot access the old user's home folder and forgot to backup my data. I've been googleing around and found nothing on the matter of accessing an encrypted folder (i.e. decrypt that folder from another OS). I agree is a safe practice to encrypt your data, but how do you access it later on?

I hope someone has an answer for this.

Thanks in advance.

---

### Post by mister_playboy on 2010-05-17
I don't see how you could access it.  Your new OS doesn't have the keys to decrypt it... otherwise the encryption would be worthless, wouldn't it?

Maybe I'm missing something, but I think you are screwed.

---

### Post by sparky-steve on 2010-05-17
The only possible way to do this is if you wrote down the encryption key at the time you set up the encrypted drives.

If you didn't then you have 0 chance of getting your data back.

If you did, then there are threads on this forum to help you get the data back.... I've done it.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

Section headed "Recovering Your Data Manually"

SS

---

### Post by Kikin-sama on 2010-05-19
Ok, thank you both. Now I know there is a way to recover encrypted data. I think it does make sense to be able to do this since you're just denying access to your data to people that do not know your passphrase. Sadly 9.10 didn't give the option after installing to generate such passphare, so I lost my data.

Anyway, there's something new you learn everyday.

Tank you.

---

### Post by spezticle on 2010-06-19
when you install 9.10 and encrypt your /home folder, after you log in the first time, a window comes up telling you that you should generate your key to decrypt your  home folder if ever needed. it's when you type your password in here that you get the key to unlock the home folder.

---

### Post by ortermagic on 2011-09-01
I upgraded to natty two months ago,and for the first time ever I decided to use the encrypt "home" file option.
 I then installed Compiz (because I like the rotate cube function) unfortunately it would appear that compiz does not work with nautilus and I eventually got a blank screen with no functionality at all.
 I had already backed up "home" to dvd before I installed compiz, so I reinstalled 10.10, (forgetting the encryption factor implemented with the 11.04) of course the dvd became unreadable.
 I still have the long p/w for the 11.04 install but I have deleted and written over the whole drive with a clean install of 10.10 . Is it possible to recover these encrypted files from the dvd? help!

---

### Post by spezticle on 2011-09-01
i'm sure it's at least partially possible... it may be pretty complicated though... minimize the usage of the old /home partition area. the more you write new data and delete new data and rewrite the more difficult it will become. 

check out the following thread, it seems to be relevant:
[http://ubuntuforums.org/showthread.php?t=962561&highlight=recover+encrypted+partiton](http://ubuntuforums.org/showthread.php?t=962561&highlight=recover+encrypted+partiton)

---

### Post by ortermagic on 2011-09-01
Thanks for the quick reply...I have had occasion to recover lost files back in the day before I found Ubuntu, when I used a win based recovery programme successfully , I will probably try to do something like post #9 on the link you provided...can't try it right now but I will surely get back to you if I have any success

---


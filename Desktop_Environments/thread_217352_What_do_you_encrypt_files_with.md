---
title: "What do you encrypt files with?"
date: 2006-07-17
forum: Desktop Environments
---

### Post by VirtuAlex on 2006-07-17
What do you use to encrypt files? I'm looking for something light like password protected zip archive, but native to linux.

---

### Post by aysiu on 2006-07-17
*kgpg*? It's in the Universe repositories.

---

### Post by VirtuAlex on 2006-07-17
No, I'm using gnome. Even better if it would work from command line.

---

### Post by orb9220 on 2006-07-17
Truecrypt thier is a thread here where to download.

I use and it seems to work well and is very powerful.
only cli still windows version has a gui.
[http://www.truecrypt.org/](http://www.truecrypt.org/)
[http://www.ubuntuforums.org/showthread.php?t=199367&highlight=truecrypt](http://www.ubuntuforums.org/showthread.php?t=199367&highlight=truecrypt)

---

### Post by 3rdalbum on 2006-07-17
I use bcrypt to encrypt my files. It seems reasonably quick and is command-line only. It's available from the repositories.

---

### Post by reclusivemonkey on 2006-07-17
I don't encrypt, but I believe Seahorse is the Gnome default program for this;

[http://seahorse.sourceforge.net/](http://seahorse.sourceforge.net/)

Its in the repos.

---

### Post by VirtuAlex on 2006-07-18
Thanks for your input guys.

It looks like truecrypt is interesting animal, but I won't mess with compiling it from source. Will wait when it make its way into repositories. By the way I found some articles praising Loopback Encrypted Filesystem. Isn't truecrypt something like this?

bcrypt is almost what I'm looking for. I experimented with it a little and noticed that while encrypting it skips already encrypted files. It may be natural if you use just one key, but different key makes a big mess out of directory. I found more straightforward tool with similar name - ccrypt. It just encrypts files again in the same situation. I think I'll stick to it for now.

And seahorse... I installed it. It does not seem to work very well. First of all it did not make any launcher. Second, when I run it from command line it fails to generate any keys unless I run it as root and besides it gives some gtk related error messages. Third, it claims to integrate into nautilus, but I did not notice any sign of it out there. One of my professors used to tell that if you do not struggle you do not learn. I obviously do not know much about gnupg stuff, and seahorse does not seem to help it. I'll postpone struggle for some time.

---

### Post by orb9220 on 2006-07-18
I didn't compile they have the deb package at thier web site.
I just downloaded it to my folder then ran Gdepi package installler in ubuntu
and yer good to go.

---

### Post by VirtuAlex on 2006-07-18
I'd need amd64 package

---

### Post by tewest99 on 2007-08-29
> **VirtuAlex said:**
> Thanks for your input guys.

And seahorse... I installed it. It does not seem to work very well. First of all it did not make any launcher. Second, when I run it from command line it fails to generate any keys unless I run it as root and besides it gives some gtk related error messages. Third, it claims to integrate into nautilus, but I did not notice any sign of it out there. One of my professors used to tell that if you do not struggle you do not learn. I obviously do not know much about gnupg stuff, and seahorse does not seem to help it. I'll postpone struggle for some time.

I had the same problems with Seahorse ...   I did notice that under System ->Preferences->Encryption Preferences, you can enable seahorse from there ...

I was able to add the seahorse encryption plugin into G-Edit.  So at least I can encrypt text files from there, but I found NO Nautilus integration (i.e., being able to right click on a file and encrypt it from there ...)

Anyone know ow to get Seahorse working in Nautilus?

Thanks  :-)

---


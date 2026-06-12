---
title: "how much software is there for Ubuntu?"
date: 2006-08-11
forum: Desktop Environments
---

### Post by fakie_flip on 2006-08-11
I put together a few commands to make one that counts the number of packages available for Ubuntu. Others may have more or less depending on how many repositories he or she has added. This looks like plenty of software to keep me busy for a while.

```
ubuntu@ubuntu:~$ apt-cache pkgnames | wc -l
24019
ubuntu@ubuntu:~$

```

---

### Post by encompass on 2006-08-12
I am one off... what do you have that I don't automatix?
¶:

---

### Post by maniacmusician on 2006-08-12
well if you have all your repositories enabled, i think there's over 18,000 packages...not all programs of course, but still.

---

### Post by fakie_flip on 2006-08-12
> **encompass said:**
> I am one off... what do you have that I don't automatix?

you are right. i was trying out automatrix on a live cd. i dont mind trying out scripts, bash fork bombs, and linux viruses when i am using a live cd.

---

### Post by fakie_flip on 2006-08-12
> **maniacmusician said:**
> well if you have all your repositories enabled, i think there's over 18,000 packages...not all programs of course, but still.

try it and see if you get 18,000. i would like to see if you really do. what are you getting right now?

---

### Post by fakie_flip on 2006-08-12
> **maniacmusician said:**
> well if you have all your repositories enabled, i think there's over 18,000 packages...not all programs of course, but still.

this should eliminate some of the library packages that are just dependencies for other software.

```
apt-cache pkgnames | grep -v lib | wc -l 
```

---

### Post by Anduu on 2006-08-12
> **fakie_flip said:**
> this should eliminate some of the library packages that are just dependencies for other software.

```
apt-cache pkgnames | grep -v lib | wc -l 
```

16775 and I have a few extra repos like Quinn,PLF,cypherfunk,wine...

---


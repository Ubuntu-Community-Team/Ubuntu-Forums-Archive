---
title: "Random problems...fixable?"
date: 2009-03-18
forum: General Help
---

### Post by dch528 on 2009-03-18
As of a couple of days ago, Ubuntu has been giving me problems.

1. Sometimes when I try to login, it says it cannot write an authorization file because there is no more space in my hard drive, or something like that, and cannot send me to the desktop, and just restarts. If this happens, I would have to wait anywhere from an hour to 2 days to get on my laptop. Annoying to say the least.

2. Firefox no longer lets me go to the previous webpage, does not buffer videos, and does not do anything Java related.

3. Pidgin will not start. I tried to reinstall, but it will not let me because some programs "rely on it". I tried to install Kopete, and that wouldn't start up either. 

4. Ubuntu can no longer mount my 2 gig flash drive or my iPod, and if I try to connect them while already in Ubuntu, it freezes, or becomes extremely slow...

The first problem has been persistent, but the other three are new, and very confusing and frustrating. If anyone can help me I would appreciate it!

---

### Post by D3ath on 2009-03-18
> **dch528 said:**
> As of a couple of days ago, Ubuntu has been giving me problems.

1. Sometimes when I try to login, it says it cannot write an authorization file because there is no more space in my hard drive, or something like that, and cannot send me to the desktop, and just restarts. If this happens, I would have to wait anywhere from an hour to 2 days to get on my laptop. Annoying to say the least.

2. Firefox no longer lets me go to the previous webpage, does not buffer videos, and does not do anything Java related.

3. Pidgin will not start. I tried to reinstall, but it will not let me because some programs "rely on it". I tried to install Kopete, and that wouldn't start up either. 

4. Ubuntu can no longer mount my 2 gig flash drive or my iPod, and if I try to connect them while already in Ubuntu, it freezes, or becomes extremely slow...

The first problem has been persistent, but the other three are new, and very confusing and frustrating. If anyone can help me I would appreciate it!

Seems like there are some things that are missing. Try running these programs from a terminal to get what the errors you are getting. and for the login why not try creating a totally new user to log in to maybe something happened.  if you log in to the new user fine then delete the other user and your good to go. But these are just steps i would take.

---

### Post by ugm6hr on 2009-03-18
Is it possible you actually have run out of HD space.

You can check (from Recovery Terminal if necessary):
```
df -h
```

Otherwise, could this be a HD hardware problem?  Or a RAM hardware problem?

If you are sure these are not the issues, and you want to reinstall Pidgin:

```
sudo apt-get install --reinstall pidgin pidgin-data
```

I would suggest you try out the LiveCD again to ensure that works properly.  Use the memcheck function on it too.  If the LiveCD works, it may be a HD issue.

---

### Post by dch528 on 2009-03-18
Well, I reinstalled Pidgin, and it is still acting up. I noticed that i got this stuff in the terminal at one point:


Processing triggers for man-db ...
/usr/bin/mandb: can't write to /var/cache/man/5925: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/gl/5925: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/id/5925: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/ru/5925: No space left on device

...and more stuff saying what Ubuntu CAN'T DO...

Unfortunately I cannot find my LiveCD. I thought Ubuntu would solve all the problems that Windows presented, but it is now causing more. 

Just found out that I can't burn cds anymore either.

Help!!!

---

### Post by D3ath on 2009-03-18
> **dch528 said:**
> Well, I reinstalled Pidgin, and it is still acting up. I noticed that i got this stuff in the terminal at one point:


Processing triggers for man-db ...
/usr/bin/mandb: can't write to /var/cache/man/5925: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/gl/5925: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/id/5925: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/ru/5925: No space left on device

...and more stuff saying what Ubuntu CAN'T DO...

Unfortunately I cannot find my LiveCD. I thought Ubuntu would solve all the problems that Windows presented, but it is now causing more. 

Just found out that I can't burn cds anymore either.

Help!!!

Its telling you that there is no space left on the device.  It looks like your going to have to get a bigger HDD or clean some stuff up.

---

### Post by dch528 on 2009-03-18
> **D3ath said:**
> Its telling you that there is no space left on the device.  It looks like your going to have to get a bigger HDD or clean some stuff up.


Thanks, I feel like a douche, but at least this will fix it. Got a little carried away with the free apps, and the transfers from my old Windows comp. I've never actually seen my space at 0 bytes... it was so simple! Thanks guys, I will come back with more idiot problems if they persist!

---

### Post by D3ath on 2009-03-18
Not a problem.

---

### Post by dch528 on 2009-03-18
I know I am being pesky and dumb, but I found a reason why so much disk space is being used. When you have music on your desktop, in your filesystem etc., and you drag the folder to Amarok, it makes a duplicate of all the files and puts it in a designated folder under the first letter (example- drag Cannibal Corpse-The Wretched Spawn folder to Amarok, adds music, makes duplicate of all in folder under C/Cannibal Corpse/The Wretched Spawn) . So, in essence, you will have two copies of every track you added to Amarok in this manner. Is there any way to stop Amarok from doing this?

---

### Post by D3ath on 2009-03-18
> **dch528 said:**
> I know I am being pesky and dumb, but I found a reason why so much disk space is being used. When you have music on your desktop, in your filesystem etc., and you drag the folder to Amarok, it makes a duplicate of all the files and puts it in a designated folder under the first letter (example- drag Cannibal Corpse-The Wretched Spawn folder to Amarok, adds music, makes duplicate of all in folder under C/Cannibal Corpse/The Wretched Spawn) . So, in essence, you will have two copies of every track you added to Amarok in this manner. Is there any way to stop Amarok from doing this?

There should be a preference in the program to look at the library. I don't that program i use rhythmbox so i don't know off had i just know that you can tell the program where to look vs the program making the folder and copying for you.

---

### Post by dch528 on 2009-03-18
Ok, I will check it out, thanks for the help!

---


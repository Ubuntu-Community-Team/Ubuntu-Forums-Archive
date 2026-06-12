---
title: "Any way around sudo?"
date: 2006-01-14
forum: General Help
---

### Post by jsmidt on 2006-01-14
I'm sure this has been brought up before, but I searched and couldn't find it.  I like Debian's setup where root is different then the user who installs the system.  Also, it is a lot easier to type
```
su
```
 Instead of 
```
sudo -s -H
```

Is there any way to set up Ubuntu like Debian's su system?  If not I don't care but it would be nice.  :)

---

### Post by matthew on 2006-01-14
[quote=jsmidt]Is there any way to set up Ubuntu like Debian's su system?  If not I don't care but it would be nice.  :)[/quote]Yes, it can be done quite easily. Take a look at this page. Scroll down to the last part of the page and find the heading "Going back to a traditional root account" to find out how.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Aaron Hoy on 2006-01-14
thanks for that link.  I have been trying to figure out how to get it to ask for the root password on sudo for a while and everytime I ask on the forum someone lectures me about how they think having a root account is so bad.  Thanks for finally giving a concrete answer.

---

### Post by Seinfeld on 2006-01-14
Good.. But..

Although it is not allowed to login as "root", I think I have set up su on Breezy before.  But when I re-installed it again on my machine today I couldn't remember how I did set it up before. I was able to use "su" I am sure. Was that done by adding another user as "root" ?? :confused: 

However, using "sudo" is OK, what's in the link is quite satisfactory matthew but I notice that the UINX auto completion feature using the TAB key on the shell is disabled if used after typing "sudo". That is the only annoyance I have with "sudo".
Can that fixed ?? :rolleyes: 

Thanks

---

### Post by Seinfeld on 2006-01-14
Good.. But..

Although it is not allowed to login as "root", I think I have set up su on Breezy before.  But when I re-installed it again on my machine today I couldn't remember how I did set it up before. I was able to use "su" I am sure. Was that done by adding another user as "root" ?? :confused: 

However, using "sudo" is OK, what's in the link is quite satisfactory matthew but I notice that the UINX auto completion feature using the TAB key on the shell is disabled for competing commands if used after typing "sudo". That is the only annoyance I have with "sudo". Maybe file names are fine, but commands, it never works..
Can that fixed ?? :rolleyes: 

Thanks

---

### Post by jsmidt on 2006-01-14
I am greatful for your link.  Is there any way to keep sudo but make the "sudo" password different from my user password?

---

### Post by Seinfeld on 2006-01-14
Did you try using "passwd" command ??

---


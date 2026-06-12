---
title: "pure-ftpd"
date: 2005-12-21
forum: General Help
---

### Post by Ocxic on 2005-12-21
I'm trying to setup a ftp server, and i have a few questions about pure-ftp.

#1: how to i stop the service after i start it? (search the docs on the site doesn't say)

#2: is ther a gui i could use?

---

### Post by frodon on 2005-12-21
#2: no as far as i know

Why do you choose pure-ftp ?, it's just a question.
I asked that because i don't really like pure-ftp since it's not system rights based. I mean that, if i'm right, you can set pure-ftp rights with write access for a directory whatever system rights are for this directory.

I always perfered use proftpd which is based on system rights, if you wish to try it i can help you.

---

### Post by Ocxic on 2005-12-21
sure if you think that would be a better choice and if you put it that way it sounds more secure

---

### Post by frodon on 2005-12-21
I find proftpd more secure in the spirit because it will never overwrite system rights, but ... hey ... it's just my opinion ;)

What is your need about FTP server ? user access, anonimous access, passwords, ...
This is a guide i wrote about proftpd, it may help you to start : [http://www.ubuntuforums.org/showthread.php?t=79588](http://www.ubuntuforums.org/showthread.php?t=79588)

---

### Post by Ocxic on 2005-12-21
thanks, I just want it to use on my comp if i ever need anything from my computer when i'm elsewhere

---

### Post by frodon on 2005-12-21
Ok, so my guide is for you ;)

But with a FTP server you will only be able to transfer files, maybe you're looking for a remote desktop connection, so you will be able to control your whole computer the graphical way. ssh is also an interesting way to use remote access.
Use "remote desktop" or "ssh" as keyword in the search field of the forum and you will find many threads about it.

---

### Post by Ocxic on 2005-12-21
an ftp connection is fine, tho is there a way to connect to my computer and get a shell account?  that would be the best.

---

### Post by frodon on 2005-12-21
ssh is made to let you open a remote shell, here are some links which may help you : 
[http://ubuntuforums.org/showthread.php?t=27305](http://ubuntuforums.org/showthread.php?t=27305)
[http://www.ubuntuforums.org/showthread.php?t=103860](http://www.ubuntuforums.org/showthread.php?t=103860)
[http://www.ubuntuforums.org/showthread.php?t=84399](http://www.ubuntuforums.org/showthread.php?t=84399)
[http://ubuntuforums.org/showthread.php?t=30332](http://ubuntuforums.org/showthread.php?t=30332)
[http://ubuntuforums.org/showthread.php?t=30709](http://ubuntuforums.org/showthread.php?t=30709)
[http://ubuntuforums.org/showthread.php?t=53480](http://ubuntuforums.org/showthread.php?t=53480)

---


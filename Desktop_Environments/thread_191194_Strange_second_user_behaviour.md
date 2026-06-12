---
title: "Strange second user behaviour"
date: 2006-06-07
forum: Desktop Environments
---

### Post by seshomaru samma on 2006-06-07
I have Dapper running smoothly after some installation problems,
my wife is Japanese and hates the black theme I chose ,I therefore decided to create a new user for her with Japanese as default language and a milder theme.
Ever though my wife only uses firefox and views pictues I gave her user full administrator rights thru system>adminstration>users and groups .
Strangely, i can't "sudo nautilus" in her user (nothing happens) nor apt-get install anything (again nothing happnes). examples:
```
wife@ubuntu:~$ sudo apt-get install somesoftware
password:
wife@ubuntu:~$
```
another strange thing is that Picasa2 ("picasa for linux") doesn't work on her user. It comes up but if you try to import a file it just says: picasa is unable to continue.
Everything else works fine....

---

### Post by seshomaru samma on 2006-06-08
solved it!
edited the groups file in /etc
(picasa problem still persists but....never mind)

---


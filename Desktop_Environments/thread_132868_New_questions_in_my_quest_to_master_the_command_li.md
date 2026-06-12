---
title: "New questions in my quest to master the command line"
date: 2006-02-19
forum: Desktop Environments
---

### Post by ardchoille on 2006-02-19
I am getting quite proficient at cli but I have two more questions. I have a user "jason9" and I would like to add group "wheel" to the groups and add jason9 and root to group wheel. So, My questions are:

1) How do I add a new group (the "wheel" group) via command line instead of using the Users and Groups gui?

2) Once I have added the new group, how do I add users "jason 9" and "root" to the group via the command line?

thank you :)

---

### Post by xmastree on 2006-02-19
**apropos** is your new best friend.

Type **apropos group** in the terminal...

The first hit should be addgroup.

---

### Post by el3ktro on 2006-02-19
Thats an easy one: You can add groups with the "groupadd" command, users are added with the "useradd" command. To get your two users into the group wheel, you have to use the command "usermod". Type usermod --help or man usermod to find out, it's very easy.

Tom

---

### Post by heimo on 2006-02-19
You're probably trying to do something else than this achieves, but anyway:

Adding group:
```
sudo addgroup wheel
``` 
Adding user to group:
```
sudo adduser jason wheel
``` 
Removing user from group:
```
sudo deluser jason wheel
``` 
By default, wheel group is not special, but you can use pam_wheel.so to prevent other than users in wheel group to su themselves to root.
EDIT: If that's what you're after, then look at /etc/pam.d/su

---

### Post by ardchoille on 2006-02-19
[QUOTE=xmastree]**apropos** is your new best friend.

Type **apropos group** in the terminal...

The first hit should be addgroup.[/QUOTE]
Oooohh, that's quite nice. Thanks for the tip, I'll be using that from now on :)

---

### Post by ardchoille on 2006-02-19
[QUOTE=heimo]You're probably trying to do something else than this achieves, but anyway:

Adding group:
```
sudo addgroup wheel
``` 
Adding user to group:
```
sudo adduser jason wheel
``` 
Removing user from group:
```
sudo deluser jason wheel
``` 
By default, wheel group is not special, but you can use pam_wheel.so to prevent other than users in wheel group to su themselves to root.
EDIT: If that's what you're after, then look at /etc/pam.d/su[/QUOTE]
This is exactly what I was looking for :)
Thanks!

---

### Post by ardchoille on 2006-02-20
[QUOTE=heimo]By default, wheel group is not special, but you can use pam_wheel.so to prevent other than users in wheel group to su themselves to root.
EDIT: If that's what you're after, then look at /etc/pam.d/su[/QUOTE]
Well, to keep unprivileged users from calling su, you can simply do the following:
```
sudo addgroup wheel
``` 
to add the wheel group, then
```
sudo adduser jason wheel
``` 
to add a privileged user (jason in this example) to the wheel group, then
```

sudo chown root:wheel /bin/su
sudo chmod 4750 /bin/su

``` 
After all of that is done, non-privileged users will get a "denied" error when they attempt to su to another user. This also keeps non-privileged users from sitting at the keyboard and calling su repeatedly to try to guess the root password.

---

### Post by dcstar on 2006-02-20
[QUOTE=ardchoille]Oooohh, that's quite nice. Thanks for the tip, I'll be using that from now on :)[/QUOTE]
I always found "man -k whatever" to be easier to spell than "apropos whatever"    ;)

---

### Post by ardchoille on 2006-02-20
[QUOTE=dcstar]I always found "man -k whatever" to be easier to spell than "apropos whatever"    ;)[/QUOTE]
I agree.. and thanks for the tip :)

---

### Post by xmastree on 2006-02-20
Hmm.. Didn't know about that one.
Although, you don't actually need to spell apropos. **Apr<tab>** is enough to get you there...

---


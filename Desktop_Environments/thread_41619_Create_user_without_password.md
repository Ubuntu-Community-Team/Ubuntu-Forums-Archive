---
title: "Create user without password?"
date: 2005-06-14
forum: Desktop Environments
---

### Post by hanspb on 2005-06-14
Hi again,
On my previous Mandrake system I had no problem creating a user without a password, I just left the password field blank in the Create New User dialog. Now I have switched to Ubuntu and I want the same thing. It's a user for my kids, I don't want them to have to remember a password. First I tried in System>Administration>Users and Groups, but there I was forced to make a password. Then I tried "sudo adduser --disabled-password" from the console. It let me create the user without a password, but I was still not able to log in. Then I checked System>Administration>Users and Groups again, and the user had a password! Of course it was hidden (*******), but it was there, it must have been generated automatically. And as long as I don't know that password I can't log in.

 ](*,) 

So how do I do this now, is it not possible to have a user without a password, or is there something else that I have to try?

Hans Petter

---

### Post by DJ_Max on 2005-06-14
Try useradd via the command line.

---

### Post by Curlydave on 2005-06-14
I was trying to do this at first, but it wouldn't work for me either. You can make it log in automatically though with the default tab in "log in screen setup". Then you only need the pword when you need to mess with files.

---

### Post by imightbegiant on 2005-06-14
This should work:

```
$sudo useradd blankuser
$sudo passwd -d blankuser
```

Of course, always use caution in securing your box when leaving it wide open like this.

---

### Post by hanspb on 2005-06-15
Still no luck. No matter what I do I still get prompted for a password when I log in, even if I have removed the password with passwd -d username. Also, useradd did not create a home directory, like adduser did.

---

### Post by imightbegiant on 2005-06-15
check out [http://ubuntuforums.org/archive/index.php/t-12777.html](http://ubuntuforums.org/archive/index.php/t-12777.html)

---

### Post by logan2004 on 2005-06-15
hmmm

---


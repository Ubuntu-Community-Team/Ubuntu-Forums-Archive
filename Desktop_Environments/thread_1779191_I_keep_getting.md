---
title: "I keep getting"
date: 2011-06-10
forum: Desktop Environments
---

### Post by 9000cse on 2011-06-10
Failed to lock package manager

Hi all. Every time I try to bring in SW from USC, I keep getting the above. Starting to be a pain.
Help please.

Thanks.
Andy

---

### Post by drpjkurian on 2011-06-10
Hi
"ps -e | grep apt (might show you a number which is essentially a job number. My system was locked due to apt-get and showed me apt-get as job number 1594)

sudo kill 1594 (modify number to your current run)

This works perfect without having to delete the lock and causing unnecessary changes to your system"

use this:
Code:

```
ps -e | grep apt
```

get the ID and kill it.

---

### Post by 9000cse on 2011-06-10
Thanks [drpjkurian]("http://ubuntuforums.org/member.php?u=805294"), that seems to have worked.

Where can I find all these sudo commands?
I have a very old copy of 'The Complete Reference to LINUX, 2nd ed'. (I have had this since 1998, used to be useful)  but nothing listed in there. Come to think of it. Is this book of any use to me and UBUNTU?

Cheers
Andy

---

### Post by 3rdalbum on 2011-06-10
> **9000cse said:**
> Thanks [drpjkurian]("http://ubuntuforums.org/member.php?u=805294"), that seems to have worked.

Where can I find all these sudo commands?

They're not really "sudo commands" - sudo is a command, and the thing that comes after sudo is a different command.

Sudo just tells the system to "run the rest of this as root".

> I have a very old copy of 'The Complete Reference to LINUX, 2nd ed'. (I have had this since 1998, used to be useful)  but nothing listed in there. Come to think of it. Is this book of any use to me and UBUNTU?

Linux, and especially Ubuntu, moves so quickly that your 1998 reference guide is probably of little use except for if you wanted to learn some command-line basics like 'cd', 'chmod' and 'cron'. Even if your reference book was written in 2008 rather than 1998, it probably wouldn't be much more useful as things change THAT quickly.

---

### Post by collisionystm on 2011-06-10
> **9000cse said:**
> Thanks [drpjkurian]("http://ubuntuforums.org/member.php?u=805294"), that seems to have worked.

Where can I find all these sudo commands?
I have a very old copy of 'The Complete Reference to LINUX, 2nd ed'. (I have had this since 1998, used to be useful)  but nothing listed in there. Come to think of it. Is this book of any use to me and UBUNTU?

Cheers
Andy


Here is the book I have. You can read alot of it on Google Books.

[http://books.google.com/books?id=YkNiiLupct4C&printsec=frontcover#v=onepage&q&f=false](http://books.google.com/books?id=YkNiiLupct4C&printsec=frontcover#v=onepage&q&f=false)

---

### Post by 9000cse on 2011-06-10
Thanks guys, I'll bookmark that page, UNIX in a nutshell.
Cheers
Andy

---

### Post by collisionystm on 2011-06-10
[http://www.amazon.com/Official-Ubuntu-Book-Benjamin-Hill/dp/0132748509/ref=dp_ob_title_bk](http://www.amazon.com/Official-Ubuntu-Book-Benjamin-Hill/dp/0132748509/ref=dp_ob_title_bk)

[http://www.amazon.com/Official-Ubuntu-Server-Book-2nd/dp/0137081332/ref=pd_bxgy_b_img_c](http://www.amazon.com/Official-Ubuntu-Server-Book-2nd/dp/0137081332/ref=pd_bxgy_b_img_c)

---


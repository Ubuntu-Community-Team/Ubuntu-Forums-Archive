---
title: "delete usr files"
date: 2009-06-16
forum: General Help
---

### Post by kask1984 on 2009-06-16
hi every one ,
i am using ubuntu8.10 ,what will be there in "usr" folder. can i delete the folders,actually i have tried to delete some folder from "usr" folder but i was unable to do.how to delete the folders in "usr" folder it accupied about 2.3 GB space in my system.
thanks in advnace.

---

### Post by michy99 on 2009-06-16
/usr is a very important system folder. You do not need to be deleting anything from there unless you know exactly what you are doing.

---

### Post by ptn107 on 2009-06-16
You should not mess with any folders that are not owned by you or that lie outside your home folder.
> This directory contains the installed programs which are open to all users, the programs’ libraries, header files, manual pages, X Window system, telnet, ftp etc.. According to the Linux standards, /usr directory is shareable, meaning that all users can access the contents but can not modify them.

It is interesting to see that there is also a /sbin folder under /usr. The programs in /usr/sbin are the ones that can be run by the root only for system administration purposes. For example useradd command, which adds users to the system resides in /usr/sbin.

The /usr directory contains a lot of subdirectories which are very important to know one by one, such as /usr/local, /usr/include, /usr/bin, /usr/share, /usr/src. I strongly recommend you to google about these directories and learn about their contents if you want to move ahead with Linux.[1]

[1] [http://www.brighthub.com/computing/linux/articles/31515.aspx?p=4](http://www.brighthub.com/computing/linux/articles/31515.aspx?p=4)

---

### Post by drs305 on 2009-06-16
***usr*** is not short for ***user*** - they are not *your* user files. It is short for ***unix system resources***.

Link: 
[http://www.usna.edu/Users/cs/delooze/teaching/IC221/Lectures/LN02/class02.html]("http://www.usna.edu/Users/cs/delooze/teaching/IC221/Lectures/LN02/class02.html")

---

### Post by kask1984 on 2009-06-16
thanks alot michy99, ptn107 and drs305 for u r suggestions i dont delete those files.

---

### Post by aged hippy on 2009-06-16
> **drs305 said:**
> ***usr*** is not short for ***user*** - they are not *your* user files. It is short for ***unix system resources***.

Link: 
[http://www.usna.edu/Users/cs/delooze/teaching/IC221/Lectures/LN02/class02.html]("http://www.usna.edu/Users/cs/delooze/teaching/IC221/Lectures/LN02/class02.html")

... :shock:

Well, life is a constant learning process, isn't it ? :D

---

### Post by jonobr on 2009-06-16
aged hippy,

cool handle,

LOL

---

### Post by aged hippy on 2009-06-16
It's not so much a handle as a description. :lol: 8-)

---


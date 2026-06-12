---
title: "change home directory"
date: 2008-12-18
forum: General Help
---

### Post by rusty_jones on 2008-12-18
I want to change my home directory to another hard drive, how can I accomplish this?

Rusty

---

### Post by Achetar on 2008-12-18
Ok two options: 
1) Copy all of your /home/<username> files to a directory called <username> on your 2nd hard drive. Then mount the 2nd Hard drive as /home (Editing /etc/fstab is required for this. Google it).
2)
```

$ sudo usermod -md /path/to/new/home/directory

```

That will not only change the home directory locaion, but copy the files as well. If you just want to change the location, run it without the 'm' option
(eg:
```

$ sudo usermod -d /path/to/new/home/directory

```
)

---

### Post by jimmy the saint on 2008-12-18
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

there is a comprehensive looking howto

---

### Post by rusty_jones on 2008-12-20
I'm looking to move my home directory to another hard drive. I want to do this so I don't lose any of my info should something happen.

Rusty

---

### Post by Izek on 2008-12-20
>> delete post as original thread/title this was in said to move to a new HDD so that the user wouldn't lose data, basically making a copy of it <<

---

### Post by overdrank on 2008-12-20
Threads merged :)

---

### Post by kaibob on 2008-12-20
The following explains how to create a separate home partition:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by rusty_jones on 2008-12-20
I want to [COLOR="Red"]move[/COLOR] the whole structure to another HDD not copy.

Rusty

---

### Post by monkeyking on 2008-12-21
did you try the solution supplied by the second post.


btw remember to do a backup

---


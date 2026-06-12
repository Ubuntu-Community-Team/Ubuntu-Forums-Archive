---
title: "Man pages for network commands are not available"
date: 2009-05-07
forum: General Help
---

### Post by Electricalkhukuma on 2009-05-07
I CANNOT ACCESS THE MAN PAGES FOR NETWORK PROGRAMMING COMMANDS. e.g

man gethostbyname
man sys/socket.h
man socket

error msg:
" no man pages for these commands "

---

### Post by kanikilu on 2009-05-07
You need section 3 of the manual:
```
sudo apt-get install manpages-posix-dev
```

---

### Post by Electricalkhukuma on 2009-05-07
thnx but it says 

"Invalid operation manpages-posix-dev"

---

### Post by kanikilu on 2009-05-07
The only scenario I can think of where you would get that error, is if you forgot the **install** part of the command. For example:

```
sudo apt-get manpages-posix-dev
E: Invalid operation manpages-posix-dev
```

Check that you typed the command in correctly, or install it from Synaptic if you prefer...

---

### Post by Electricalkhukuma on 2009-05-07
Bundle of thanks brother \\:D/

My problem is solved !!
I wish you best of luck with lots of love

---

### Post by Iowan on 2009-05-07
Glad you found your information... I just found (via another thread) [http://manpages.ubuntu.com/]("http://manpages.ubuntu.com/").

---


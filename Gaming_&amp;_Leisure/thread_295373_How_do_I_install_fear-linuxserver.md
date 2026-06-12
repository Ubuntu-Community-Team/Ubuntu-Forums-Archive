---
title: "How do I install fear-linuxserver"
date: 2006-11-08
forum: Gaming &amp; Leisure
---

### Post by misfito on 2006-11-08
I downloaded the fear linuxserver 1.08, but I wasn't able to make it work. I've looked many times at: How to install anithing in ubuntu ([http://www.monkeyblog.org/ubuntu/installing/#source](http://www.monkeyblog.org/ubuntu/installing/#source)) and i followed the instructions described there but i got this:

user@User-s-computer:~$ cd /user/User/Desktop/fr.20671.0.fear-linuxserver-1.08.tar.gz_FILES ./configure [email]user@User-s-computer:~/Desktop/fr.20671.0.fear-linuxserver-1.08.tar.gz[/email]_FILES$ make
make: *** No targets specified and no makefile found.  Stop.
[email]user@User-s-computer:~/Desktop/fr.20671.0.fear-linuxserver-1.08.tar.gz[/email]_FILES$ sudo make install
make: *** No rule to make target `install'.  Stop.
[email]user@User-s-computer:~/Desktop/fr.20671.0.fear-linuxserver-1.08.tar.gz[/email]_FILES$ sudo checkinstall
sudo: checkinstall: command not found
[email]user@User-s-computer:~/Desktop/fr.20671.0.fear-linuxserver-1.08.tar.gz[/email]_FILES$

I don't know what to do next... [-(

---

### Post by Completenutter2 on 2006-11-19
does ./configure run without any errors?

---

### Post by Perfect Storm on 2006-11-19
What files does the tarball contains?
```
ls -a
```

---


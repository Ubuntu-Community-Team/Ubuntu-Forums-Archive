---
title: "Intalling and Running World Of Goo"
date: 2009-05-03
forum: General Help
---

### Post by brentwomble on 2009-05-03
I'm trying to install and run World of Goo on Jaunty 32 bit. I downloaded WorldOfGoo.tar.bz2 and unzipped it to /home/brent/WorldOfGoo.

What do I need to do to run it?

Total Ubuntu newb here.

---

### Post by brentwomble on 2009-05-03
This is some of the things I have tried in the terminal

brent@brent-desktop:~$ exec ./WorldOfGoo.bin
bash: /home/brent/WorldOfGoo.bin: No such file or directory
bash: exec: /home/brent/WorldOfGoo.bin: cannot execute: No such file or directory
brent@brent-desktop:~$ exec ./WorldOfGoo.bin
bash: /home/brent/WorldOfGoo.bin: No such file or directory
bash: exec: /home/brent/WorldOfGoo.bin: cannot execute: No such file or directory
brent@brent-desktop:~$ exec ./WorldOfGoo/WorldOfGoo.bin
bash: /home/brent/WorldOfGoo/WorldOfGoo.bin: Permission denied
bash: exec: /home/brent/WorldOfGoo/WorldOfGoo.bin: cannot execute: Success
brent@brent-desktop:~$ sudo exec ./WorldOfGoo/WorldOfGoo.bin
[sudo] password for brent: 
sudo: exec: command not found
brent@brent-desktop:~$ sudo ./WorldOfGoo/WorldOfGoo.bin
sudo: ./WorldOfGoo/WorldOfGoo.bin: command not found
brent@brent-desktop:~$ sudo
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
brent@brent-desktop:~$ exec ./WorldOfGoo/WorldOfGoo.bin
bash: /home/brent/WorldOfGoo/WorldOfGoo.bin: Permission denied
bash: exec: /home/brent/WorldOfGoo/WorldOfGoo.bin: cannot execute: Success
brent@brent-desktop:~$ /root

---

### Post by brentwomble on 2009-05-03
bump

---

### Post by akoskm on 2009-05-04
Try
```

chmod +x WorldOfGoo.bin
sh WorldOfGoo.bin

```
Hope that helps.

---

### Post by binbash on 2009-05-04
sudo chmod +x /home/brent/WorldOfGoo/WorldOfGoo.bin
./home/brent/WorldOfGoo/WorldOfGoo.bin

---


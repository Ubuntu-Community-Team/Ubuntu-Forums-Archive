---
title: "executing .bin files"
date: 2009-05-24
forum: General Help
---

### Post by bawig1 on 2009-05-24
Hi,

I have just downloaded an executable bin file and am trying to run it. If I type

[EMAIL="bawig1@bawig1-laptop:%7E/Desktop$./filename.bin"]bawig1@bawig1-laptop:~/Desktop$./filename.bin[/EMAIL]

I get 

bash: ./filename.bin: Permission denied

So I try and run it wih sudo, but when I try that I get

awig1@bawig1-laptop:~/Desktop$sudo ./filename.bin
sudo: ./filename.bin: command not found

What am I doing wrong?

thanks,

Brett.

---

### Post by ad_267 on 2009-05-24
chmod a+x filename.bin

That will make the file executable for all users. Then you can run ./filename.bin.

---

### Post by bawig1 on 2009-05-24
thanks, got it working :D

---


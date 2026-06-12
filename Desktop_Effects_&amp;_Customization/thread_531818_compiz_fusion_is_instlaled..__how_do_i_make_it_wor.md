---
title: "compiz fusion is instlaled..  how do i make it work?"
date: 2007-08-22
forum: Desktop Effects &amp; Customization
---

### Post by shorty28898 on 2007-08-22
i just isntlaled it but i dont know hw to get anything to work.  can wsomeone help  me out?

---

### Post by Chymera on 2007-08-22
type: compiz --replace in a terminal....

---

### Post by donteatsoap7 on 2007-08-22
i just tried that and got:

donteatsoap7@ubuntu:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
donteatsoap7@ubuntu:~$

---

### Post by misfitpierce on 2007-08-22
First off give us some info on machine... And also what are GPU / Vid card specs. If ATI you need to set up XGL session for sure.

---

### Post by donteatsoap7 on 2007-08-22
[This is my computer. I haven't upgraded or changed anything]("http://reviews.cnet.com/desktops/dell-dimension-2400-pentium/4507-3118_7-30824846.html")

---

### Post by Chymera on 2007-08-22
that error sounds suspiciously like ati, i saw a friend of mine getting it on end, and thats when i decided to go with nvidia. If its because of your ati card you can begin building a time machine to go back into the past  and stop yourself form buying an ati graphics card; if you will give it a search you will find that getting composite managers to run with some ati cards is a loosing battle....
EDIT: I was just writing while you made your last post.... hmmm....  i dont know anything about integrated gfx controllers under linux but i would think reconfiguring your x might do the trick... now lets see what the command for that was....

---

### Post by shorty28898 on 2007-08-22
lindo@ubuntu:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.



that is what came up when i tried to do it.

and also i think its in intel grahics drive..  so,...???

---

### Post by Chymera on 2007-08-22
```
sudo dpkg-reconfigure xserver-xorg
```

thats the comand you want to enter (after turning x off) if you would consider reionfiguring your x ....

---

### Post by shorty28898 on 2007-08-22
ok did that annddd nothing different is happening

---


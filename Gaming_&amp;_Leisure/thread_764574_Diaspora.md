---
title: "Diaspora"
date: 2008-04-24
forum: Gaming &amp; Leisure
---

### Post by Drezliok on 2008-04-24
I('m trying to get Diaspora working as it's gone opensource. I haven't figured it out.

[http://www.nighsoft.net/](http://www.nighsoft.net/)

Anyone get the game working?

---

### Post by Perfect Storm on 2008-04-24
I have a 64-bit guide: [here](http://gaming.gwos.org/doku.php/guides:64bit:project_diaspora)

---

### Post by Drezliok on 2008-04-24
No I am getting this error, yet I have all the newest stuff installed.
```

drezliok@TuxEater:~$ sh /home/drezliok/.Games/PDiaspora-launch.sh./pdiaspora: 
error while loading shared libraries: libSDL_gfx.so.13: cannot open shared object file: 
No such file or directory

```


but like I said it's installed
```
drezliok@TuxEater:~$ getlibs -p libsdl-image1.2 libsdl-gfx1.2-4 libpng3
[sudo] password for drezliok: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsdl-image1.2 is already the newest version.
libsdl-gfx1.2-4 is already the newest version.
libpng3 is already the newest version.
```

---

### Post by Perfect Storm on 2008-04-24
Did you:
```
sudo ln -s /usr/lib32/libSDL_gfx.so.4 /usr/lib32/libSDL_gfx.so.13
```


(fixed the link above, it seems the forum broke it).

By the way which version of Ubuntu do you use?

---

### Post by Drezliok on 2008-04-24
> **Artificial Intelligence said:**
> Did you:
```
sudo ln -s /usr/lib32/libSDL_gfx.so.4 /usr/lib32/libSDL_gfx.so.13
```


(fixed the link above, it seems the forum broke it).

By the way which version of Ubuntu do you use?

```
drezliok@TuxEater:~$ sudo ln -s /usr/lib32/libSDL_gfx.so.4 /usr/lib32/libSDL_gfx.so.13
[sudo] password for drezliok: 
ln: creating symbolic link `/usr/lib32/libSDL_gfx.so.13': No such file or directory

```

I am running Hardy heron 32bit.

---

### Post by Perfect Storm on 2008-04-24
> **Drezliok said:**
> ```
drezliok@TuxEater:~$ sudo ln -s /usr/lib32/libSDL_gfx.so.4 /usr/lib32/libSDL_gfx.so.13
[sudo] password for drezliok: 
ln: creating symbolic link `/usr/lib32/libSDL_gfx.so.13': No such file or directory

```

I am running Hardy heron 32bit.

Then you should never use that guide as it specific for 64-bit.


Instead:
```
sudo ln -s /usr/lib/libSDL_gfx.so.4 /usr/lib/libSDL_gfx.so.13
```

---

### Post by sideaway on 2009-04-18
I'm a little stuck;
I used this line:
```
sudo ln -s /usr/lib/libSDL_gfx.so.4 /usr/lib/libSDL_gfx.so.13
```
Everything appeared to work smoothly. Except I can't launch the game? 
 Here's my launcher
```
#!/bin/bash

cd ~/.Games/PDiaspora
./pdiaspora
```

Whenever I run the launcher, nothing happends... Just, nothing, no errors or anything, any idea?

---

### Post by Perfect Storm on 2009-04-18
Try run the script via the terminal instead. There's a better chance to see what's wrong.

---

### Post by jjaeger4 on 2009-04-22
I skipped the whole hassle and would like to note that the Project Diaspora Windows Version runs very smooth in Wine.

w00t. =)

---


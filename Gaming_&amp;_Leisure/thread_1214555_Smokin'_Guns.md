---
title: "Smokin' Guns"
date: 2009-07-16
forum: Gaming &amp; Leisure
---

### Post by spcwingo on 2009-07-16
Anybody else tried [[COLOR="Red"]this[/COLOR]]("http://www.smokin-guns.net/") game?  I think it's a keeper!

---

### Post by accLinux on 2009-07-16
I can't get it to play (:

---

### Post by spcwingo on 2009-07-16
Make sure that the file named smokinguns.x86 is marked as executable.  After that try launching from the terminal to see the error codes.  For instance, say that the folder Smokin' Guns is in your Home folder.  Rename that folder to Smokin_Guns.  Then, to launch from the terminal just:

```
cd Smokin_Guns
```

Followed by:

```
./smokinguns.x86
```

If it gives you error codes and you need help to resolve, just copy/paste in your next post.

---

### Post by accLinux on 2009-07-16
Ok, here is the output from the terminal:



[B]nick@nick-desktop:~$ cd ~/Smokin_Guns
nick@nick-desktop:~/Smokin_Guns$ ./smokinguns.x86
./smokinguns.x86: *error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory*
[/B]


Seems like I need yet another library: I've had problems with almost all of my games and libs in 9.04.....................Alien Arena 2009, et, UrT, now this............................Wow! Not easy!

---

### Post by spcwingo on 2009-07-16
You can try installing with:

```
sudo apt-get install libopenal0a
```

If that doesn't get it (it may be different on Jaunty...I'm still on Hardy), just search in synaptic for libopenal.

---

### Post by PureLoneWolf on 2009-07-17
> **accLinux said:**
> Ok, here is the output from the terminal:

[B]nick@nick-desktop:~$ cd ~/Smokin_Guns
nick@nick-desktop:~/Smokin_Guns$ ./smokinguns.x86
./smokinguns.x86: *error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory*
[/B]
I had the same issue - try ```
sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0
``` in a terminal.

---

### Post by tommcd on 2009-07-17
Here is an article about "Smokin' Guns" from linux.com:
[http://www.linux.com/archive/feature/142226](http://www.linux.com/archive/feature/142226)

---

### Post by accLinux on 2009-07-21
> **PureLoneWolf said:**
> I had the same issue - try ```
sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0
``` in a terminal.

Hey thanks man. it now works (:



Where do you guys get these terminal commands, and what does this one do?

---

### Post by spcwingo on 2009-07-22
You're just making a symbolic link (in Windows terms these would be called shortcuts).  Let's break down that command.

```
sudo
```

is Super User DO.

```
ln -s
```

is LiNk with a switch of -s (symbolic)

```
/usr/lib/libopenal.so.1
```

is the file to be linked to and finally,

```
/usr/lib/libopenal.so.0
```

is the link itself.

It's refreshing to see someone who actually wants to know what the commands do and why.  Most people just want it to work with little to no regard as to why it works.  Thank you for being genuinely interested.  :)

---

### Post by accLinux on 2009-07-30
> **spcwingo said:**
> You're just making a symbolic link (in Windows terms these would be called shortcuts).  Let's break down that command.

```
sudo
```

is Super User DO.

```
ln -s
```

is LiNk with a switch of -s (symbolic)

```
/usr/lib/libopenal.so.1
```

is the file to be linked to and finally,

```
/usr/lib/libopenal.so.0
```

is the link itself.

It's refreshing to see someone who actually wants to know what the commands do and why.  Most people just want it to work with little to no regard as to why it works.  Thank you for being genuinely interested.  :)

Thanks for the explaination! Learning more all the time!

---

### Post by Rumbl3 on 2009-07-30
was just reading about this game lol sounds awesome the multiplayer bank robbery. DLing right now. Ahhhh quake 3 engine ftw on linux gaming :)

---

### Post by xgr3gx on 2009-11-02
Anybody have luck getting Smokin' Guns to run on x86-64 Ubuntu?  I had it working fine in 64bit Gentoo.  
I installed the 32bit Compat libraries (ia32 package) but I still get errors about missing libraries, but the libraries do exist.  I think the 32bit app is trying to load 64bit libs. 
Any one have any luck?  
Thanks, 
Greg

---

### Post by spcwingo on 2009-11-07
What errors do you get when you run it from a terminal?

---

### Post by mysteriousdarren on 2009-11-09
I use Smoking guns with x86-64 Ubuntu Karmic, it works really well on how much I've been playing it. I also used it in Jaunty. I played for several hours and did not have any trouble at all. Give it a try, its a fun game.

---

### Post by gradinaruvasile on 2009-11-09
Guys, install it from here:

[http://www.playdeb.net/updates/?q=smokinguns](http://www.playdeb.net/updates/?q=smokinguns)

It worked for me without any engineering involved.

PS Great game!

---

### Post by Legendário on 2010-01-04
It's a very good game. But unfortunately lacks people on the servers.

---


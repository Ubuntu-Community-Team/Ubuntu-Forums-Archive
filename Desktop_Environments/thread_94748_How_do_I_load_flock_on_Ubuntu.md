---
title: "How do I load flock on Ubuntu"
date: 2005-11-24
forum: Desktop Environments
---

### Post by RAV TUX on 2005-11-24
I have been using flock alot on my other computer would like to load this browser on Ubuntu?:???:

---

### Post by akseli on 2005-11-25
[QUOTE=yozef]I have been using flock alot on my other computer would like to load this browser on Ubuntu?:???:[/QUOTE]

Ok, it *should* be rather simple. 

1. go to [http://www.flock.com/developer/]("http://www.flock.com/developer/")
2. Download the Linux Build
3. Untar the file you downloaded into any directory you want /home/[username] is the ideal.
4. Open up a Terminal window and type in:
```
sh ~/flock/flock
```
and that will pull up your browser.

If you want to create a link to simply click on to run the browser:
1. go to your desktop
2. right click
3. pick "create launcher"
4. Name it Flock (or whatever you want)
5. in Command type in:
```
sh ~/flock/flock
```
6. Pick any icon you want for it.
7. Hit OK

and you're done.
If you need any more help don't hesitate to contact me through here or by e-mail (you'll get a faster reply through e-mail)

---

### Post by RAV TUX on 2005-11-26
follow up I downloaded but I don't know how to untar...and not sure if I picked the right method of downloading? can you please give more simple very beginner  step by step instructions...it would be greatly appreciated.:p


this is what comes in my terminal:

sh ~/flock/flock
sh: /home/yozef/flock/flock: No such file or directory

---

### Post by akseli on 2005-11-27
[QUOTE=yozef]follow up I downloaded but I don't know how to untar...and not sure if I picked the right method of downloading? can you please give more simple very beginner  step by step instructions...it would be greatly appreciated.:p


this is what comes in my terminal:

sh ~/flock/flock
sh: /home/yozef/flock/flock: No such file or directory[/QUOTE]


Ok, you have to download the file that ends in .tar.gz (flock-0.4.10.en-US.linux-i686.tar.gz)
After you download this place copy paste it into: /home/jozef
then rightclick on the icon and hit "extract here"
Now you can open up a console and type in:
```
sh ~/flock/flock
```
which should start up your browser.
To create the shortcut icon just go to your desktop, right click and choose create launcher. There give it any name you want and under command type in: 
```
sh ~/flock/flock
```
Choose any icon you want and hit OK

---

### Post by damianmann on 2005-12-15
It works fine now. Excellent

---

### Post by bhilton on 2005-12-16
When I try to execute the steps above, I get...

[I]./flock/flock-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
[/I]

Poking around on the web, I have found a few references that state I should install *compat-libstdc++*, however, I can't find it.

Does anybody have any ideas?

Thanks,

Brad

---

### Post by 23meg on 2005-12-16
```
sudo apt-get install libstdc++5 
``` should help.

---

### Post by bhilton on 2005-12-16
It worked, thanks!

---

### Post by disruptor108 on 2006-01-10
> Ok, you have to download the file that ends in .tar.gz (flock-0.4.10.en-US.linux-i686.tar.gz)
After you download this place copy paste it into: /home/jozef
then rightclick on the icon and hit "extract here"
Now you can open up a console and type in:

```
sh ~/flock/flock
```

which should start up your browser.

I did this and got this error:

```
/home/westhusing/flock/run-mozilla.sh: line 166: /home/westhusing/flock/flock-bin: cannot execute binary file
```

---

### Post by zutronius on 2007-07-27
The last step did not work. The shortcut I made to launch Flock does nothing.

---


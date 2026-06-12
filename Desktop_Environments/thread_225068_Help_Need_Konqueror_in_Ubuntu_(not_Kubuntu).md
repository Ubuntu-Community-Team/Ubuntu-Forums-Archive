---
title: "Help? Need Konqueror in Ubuntu (not Kubuntu)"
date: 2006-07-29
forum: Desktop Environments
---

### Post by luckylucky on 2006-07-29
Someone please help?

In the past on a previous installation of Ubuntu (not Kubuntu) I somehow (no idea how) managed to get Konqueror installed.  I love it (for sftp & other stuff).

I've tried to find it in synaptec, but it doesn't seem to be there.  Of course I have Universe & Multiverse enabled.

[COLOR="Red"][B][SIZE="4"]Can someone please explain how to get Konqueror installed into Ubuntu?  Thanks in advance for your help.
[/SIZE][/B][/COLOR]
LuckyLucky

---

### Post by dio525i on 2006-07-29
i don't know for sure...but seems like you could just "apt-get install konqueror" and it would do it no?

---

### Post by Uncle Spellbinder on 2006-07-29
Just checked Synaptic Package Manager. It's there for me.

[[IMG]http://img150.imageshack.us/img150/9756/synapticfz2.th.png[/IMG]](http://img150.imageshack.us/my.php?image=synapticfz2.png)

---

### Post by aysiu on 2006-07-29
It's not in the Universe or Multiverse. It's in the regular repositories.

Can you post the output of these commands? ```
sudo aptitude update
sudo aptitude install konqueror
cat /etc/apt/sources.list
```

---

### Post by wong3000 on 2006-07-29
I have just discovered this just now. 
Select the Synaptic Package Manager under the Administration and look for the World Wide Web in the left corner. The Kongueror package will appear in the list. Click it and Apply. 
There you go. :p 
Hope this helps:KS

---

### Post by Ziox on 2006-07-29
use sudo aptitude install konqueror, it'll make removing it faster and easier

---

### Post by luckylucky on 2006-07-29
Wow!  That sure was quick!!! Thanks for all the help!  Thanks everyone!

I don't know why I didn't think of this myself, but the person who suggested doing this:

apt-get install konqueror

worked for me!  Thanks everyone!!!

LuckyLucky

---


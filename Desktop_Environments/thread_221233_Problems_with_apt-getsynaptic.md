---
title: "Problems with apt-get/synaptic"
date: 2006-07-22
forum: Desktop Environments
---

### Post by cyclister on 2006-07-22
Having now 2 kinds of diffrent problems with my synaptic and apt-get
In synaptic this occure 
W: Failure to recive [http://us.archive.ubuntu.com/ubuntu/pool/main/z/zlib/zlib1g-dev_1.2.3-6ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/z/zlib/zlib1g-dev_1.2.3-6ubuntu4_i386.deb)

So I change my list in repos that didnt do the trick, but went a little further ahead, though

Then in apt-get I have 
E: Unable to open lockfile /var/lib/apt/lists/lock - open (13 Premission denied)
E: Unable to lock listcatalogue

This is kind of translate from my language to english but hope someone know what I should do :( 

Think this aint so much of a problem.
All started out beacuse I did a very stupid move in my accounts :( but that are correct.
Then I switched gfx card and that also are done and Im like halv nub on this.

---

### Post by taurus on 2006-07-22
Okay, for a billion times, us.archive.ubuntu.com is down so you can either way until tomorrow to try apt-get again or edit your /etc/apt/sources.list and remove the "us" in front of all the lines in there...

```

sudo gedit /etc/apt/sources.list

```

---

### Post by Billquinn1 on 2006-07-22
I think the lock error is just because you still had synaptic open when you tryed to apt-get. It does not like that. I think taurus is right about the us repos.

---

### Post by Thund3rstruck on 2006-07-22
I'm using this [great repo listing]("http://www.psychocats.net/ubuntu/sources") since the us.* one is down

---

### Post by cyclister on 2006-07-23
Gee thanks added that other repo to my list that Thund3struck did show.

>  Okay, for a billion times, us.archive.ubuntu.com is down so you can either way until tomorrow to try apt-get again or edit your 

How often do apt-get sometimes go down?
Little curious what can happen sometimes?

---

### Post by st00ner on 2006-07-23
ive been using ubuntu for about 1 month, and this is the first time.

---

### Post by cyclister on 2006-07-23
Like almost a year but when you have a nice system why fix and trix so it might brake down so many month I do not give a damn about apt-get and such.

Little odd that when you most need it, it's gone always murphys and his fricking law's.
Murphys law the law of all "sickness"
(not know in english here)
Damn you murphy, damn you ;)

---


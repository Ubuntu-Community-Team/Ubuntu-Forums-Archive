---
title: "You are missing the following 32-bit libraries, and Steam may not run: libc.so.6"
date: 2015-03-04
forum: Gaming &amp; Leisure
---

### Post by yomen-tohmaz on 2015-03-04
Hey everyone I'm some what new to Linux.  I have used Elementary first but I thought of switching to Ubuntu, which I did.  But I'm having trouble with Steam right now.  The error I'm getting every time I try to start it is... 

You are missing the following 32-bit libraries, and Steam may not run:
libc.so.6

I have read some other forums and I did what they said but none of them work.  I'll keep looking for an answer both through replies to this post and through other forums.  Also I am using Ubuntu 14.04.

Thanks for any help.

Yomen Tohmaz

---

### Post by MikeCyber on 2015-03-05
Probably alike:
[http://unix.stackexchange.com/questions/85505/need-to-install-glibc-2-14-on-wheezy](http://unix.stackexchange.com/questions/85505/need-to-install-glibc-2-14-on-wheezy)
for 32bit you need the files ending with .i386 something alike:
sudo apt-get install libc6-i386
or use synaptic.
Did you properly install the latest steam from the website? It should do all. I would rather redownload/install steam and proprietary graphics driver.

---

### Post by m-j-feeney on 2015-03-05
I started a thread on the newbie section. I am having the same issue. I was able to get the lib error to go away after using some apt-get lines. It seemed to work then I tried to open steam again and got another lib error message just with a different number.

---

### Post by Mat_Bigelowe on 2015-12-12
None of this is working and I have been trying for days! Please someone help me, I have a huge LAN coming up and if steam isn't working I can't do anything and I'll have to spectate my own LAN. Sorry for being a little demanding, it's just that I'm new to Linux and really forums in general except for dabbling in Reddit so this is really confusing/ annoying for me.
Thanks, Mat

---

### Post by QDR06VV9 on 2015-12-12
> **Mat_Bigelowe said:**
> None of this is working and I have been trying for days! Please someone help me, I have a huge LAN coming up and if steam isn't working I can't do anything and I'll have to spectate my own LAN. Sorry for being a little demanding, it's just that I'm new to Linux and really forums in general except for dabbling in Reddit so this is really confusing/ annoying for me.
Thanks, Mat
Hi Mat
First off some more info is required
Post back the output of this in the terminal
```
lsb_release -a
```
And this also
```
apt-cache policy steam
```
Then we shall get a little better start as to how to proceed..

---


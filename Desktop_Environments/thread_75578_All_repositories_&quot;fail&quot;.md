---
title: "All repositories &quot;fail&quot;"
date: 2005-10-13
forum: Desktop Environments
---

### Post by corstar on 2005-10-13
Hi, I am having heaps of troule getting the apt repos working. I've tried all and individual selections of the repositories and get a "Failed" on every single one of them.

The mirrors I'm using are au(apt chose this for me) so I wouln't think they would be under so much bandwidth pressure.

Please help, without apt I'm very limited to what I can do on Ubuntu.

---

### Post by vrecan on 2005-10-13
all the repositories right now are under extreme load.. you could have luck with another one but right now the best I can get is around 15k so I would just hold off for a little bit.

---

### Post by corstar on 2005-10-13
this also happens on hoary (my desktop) and has been broke for a week or so..

What details should I post to help give a clearer picture?

---

### Post by oldblue on 2005-10-13
he's right.  the us domain is getting around 15-25 kB/s right now.  Should taper off tomorrow or the next couple of days.  Did you try other mirrors?  If no other mirrors are working, then there may be something wrong with your repository setup.  But the problem is probably that the au mirror is down.

---

### Post by oldblue on 2005-10-13
try posting your sources.list file located in /ect/apt.

---

### Post by SqdnGuns on 2005-10-13
Getting 37.4 kB/s at the moment............  :(

---

### Post by corstar on 2005-10-13
Here's my hoary sources. (I don't know how to create a scroll box around the text)

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary main restricted
 deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary-updates main restricted
 deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by corstar on 2005-10-13
I think I will get another iso now.
Let's see if a new install helps....:???:

---

### Post by oldblue on 2005-10-13
Have you tried a different mirror?  The file seems in order and if you were having problems with apt in hoary as well then I am inclined to believe that your mirror is down.  When you run apt-get update or upgrade from the terminal is it saying that it can't find certain files?  If it is giving some sort of failed to retrieve or locate error then it is your mirror most likely.  I don't know the mirrors that are closer to you, so you might try replacing au with us just to see what happens.

---


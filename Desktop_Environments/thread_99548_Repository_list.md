---
title: "Repository list?"
date: 2005-12-05
forum: Desktop Environments
---

### Post by tymanthius on 2005-12-05
I tried Ubuntu Breezy this weekend and loved it so much I wiped my Mandriva install and am now happily blowing in the breeze!  

What I would like to know, however, is there a list of all (or MOST) repositories anywhere?  Something like easyurpmi.org?

Thanks for any info!

Tymanthius

---

### Post by Qrk on 2005-12-05
```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

```

Will give you all the official Ubuntu repositories, but only main is officially supported. Just uncomment your /etc/apt/sources.list entry untill it looks like this one.

---

### Post by BLTicklemonster on 2005-12-05
go to the terminal

applications>accesories>terminal

and type in this


sudo gedit /etc/apt/sources.list


Press enter, enter you password, and copy and paste what is in the previous post, then save.

Now if you are lazy, you can cheat...

right click on the desktop, and click on create launcher, then name it Repository List, then go to the part where it says, "Comm_a_nd:" and type in 


sudo gedit /etc/apt/sources.list

and I think you ought to check the box that says run in terminal, I always do, being a noob, lol.

Save it, then you can just double click it, and type in your password whenever you need it.

---

### Post by tymanthius on 2005-12-07
That's kinda what I thought, but I do read about other repo's for special packages (like Enlightenment 17), so  I was just wondering if anyone had compiled a 'complete' list.

Thanks for the replies.

---

### Post by RAOF on 2005-12-07
The more (non-official Ubuntu) repos you add to your sources.list, the more chance that something will break.  A 'complete' list of all the unofficial repos would by **huge**, and a bit unnecessary - all the howto's which use additional repos will include them in the howto.

---

### Post by BLTicklemonster on 2005-12-08
Which is why I do what I do. I can keep pages of repos stored away, and load them up in a jiffy. Thing is, I got to get them all back, lol.

---


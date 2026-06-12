---
title: "[SOLVED] Duplicate sources.list entry error"
date: 2006-09-21
forum: Desktop Environments
---

### Post by ropers on 2006-09-21
I'm having this problem in "Add/Remove..." and in the Synaptic Package Manager:

[IMG]http://ropersonline.com/downloads/sources.list-error.png[/IMG]

I tried to track down those duplicate entries but I am stumped. Any ideas?

Many thanks in advance, 
--ropers

---

### Post by bswilson on 2006-09-21
You need to look in the file **/etc/apt/sources.list** for the duplicate entry.  Before editing it, make a backup copy.  You can use **gedit** to make the changes.

```
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.BAK
$ gksudo gedit /etc/apt/sources.list
```

---

### Post by ropers on 2006-09-23
Thanks for your reply. :)

I have already looked at sources.list but just can't seem to find the problem. What are we looking for? Entire duplicate lines? Or something else? I'm sure there is a vi command (Yep, I prefer vi over gedit. Sosumi.) for searching for duplicate lines but I don't know it.

I've uploaded my current sources.list here:
[http://ropersonline.com/downloads/sources.list](http://ropersonline.com/downloads/sources.list)

Thanks for your help! :)

---

### Post by Zwack on 2006-09-23
Well... I can't see any duplicates but it seemed like I'd seen this before... 

A quick google search pointed me to someone else with the same problem in Hoary...

[http://www.ubuntuforums.org/archive/index.php/t-6198.html]("http://www.ubuntuforums.org/archive/index.php/t-6198.html")

Try ```
sudo apt-get clean ; sudo apt-get check
```

I hope that this helps,

Z.

---

### Post by ropers on 2006-09-24
Thank you. I did this -- and haven't had the problem since. The issue wasn't always reproducible though, so I guess I'll just wait and see if it reoccurs. If I don't post another message here in due time then it's fairly safe to assume that this fixed the problem.

Many thanks for your help! :)
--ropers

---

### Post by helmeteye on 2006-12-05
I tried the sudo clean deal.  It didn't work for me.

---

### Post by r0cks0ul on 2007-06-28
Well I had the same problem with Feisty and I finally figured out a fix 
I had this problem twice already on my first machine and yes i found duplicates and so i removed those lines 

But not on this new machine that im working with so i googled and found this!!!!
didn't help at all 

Error that i was having:

==========================================================
W: Duplicate sources.list entry [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) feisty/main Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
==========================================================

So what I did: *** Put spaces(new line)  between them ***

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Originally the last 3 sources at the end of the line were like these:

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Hope it helps!!!!

---


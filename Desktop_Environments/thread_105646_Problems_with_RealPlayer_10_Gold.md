---
title: "Problems with RealPlayer 10 Gold?"
date: 2005-12-18
forum: Desktop Environments
---

### Post by erik-the-red on 2005-12-18
The installation process was fine with the *.bin downloaded from Real's website.

However, there seems to be some problems making a symbolic link from the RealPlayer directory in my /home to /usr/bin.

It just won't run if I type "realplay" in the terminal, where the symbolic link is at /usr/bin/realplay.

What's wrong?

---

### Post by erik-the-red on 2005-12-20
At least one other person has used the *.bin and not from synaptic, right?

IIRC synaptic only has Realplayer 8.

---

### Post by dcstar on 2005-12-20
[QUOTE=erik-the-red]At least one other person has used the *.bin and not from synaptic, right?

IIRC synaptic only has Realplayer 8.[/QUOTE]
There is a Debian Realplayer 10 binary in this repository:

[ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

I use a slightly later version, but I seem to remember this one worked for me (someone may want to give it a try and report back)

---

### Post by erik-the-red on 2005-12-21
Thanks, I'll have to check into that.

---

### Post by erik-the-red on 2005-12-21
OK, I now know why I was unable to get realplay running. It was definitely because I installed it to my home directory and did not install the binary as root. So, I did and it prompted me to create system-wide symbolic links.

Now, the problem is as follows: I type realplay in the terminal, and it opened, but whenever I try to open a file, realplayer crashes and this spits out:

```

/usr/bin/realplay: line 75:  7520 Segmentation fault      $REALPLAYBIN "$@"

```

I've noticed that this is a frequent occurrence with Breezy. Many apps don't seem to like SCIM 1.0.2 anymore. This also occurred when I tried Firefox 1.5 RC 3 and Thunderbird 1.0.7.

---

### Post by nicoblue on 2005-12-21
I too have had major problems in getting realplayer,why cant ubuntu have a third party app installing device like xandros does and also suse has !
 The skill and knowledge level in ubuntu should make that so easy,not being able to get realplayer is the sole reason I do not use ubuntu as my first choice distro!
It must be said that if you cannot easily listen to your national radio station,(BBC) then this distro does not deserve to be no. 1

---

### Post by DrFedora on 2005-12-21
***This needs to be in a folder called /usr/local/Realplayer/ to work.****
You need to be root for this install and chmod a+x R*********
run the file with ./Real************
i put it in the "/usr/local/Realplayer/" folder (it asks you to name it) 
say yes for the symbolic links and yes to the usr

---


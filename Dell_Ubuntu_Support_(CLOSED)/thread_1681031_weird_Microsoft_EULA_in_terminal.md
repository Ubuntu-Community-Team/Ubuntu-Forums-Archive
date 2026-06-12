---
title: "weird Microsoft EULA in terminal"
date: 2011-02-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by josh6190 on 2011-02-03
Just got my Dell Mini 1018 and installed Ubuntu 10.10 on it. While waiting for an email for Realtek containing the wireless driver, I decided to give Compiz Fusion a shot. It works great, but after attempting to install the plugins-extra, I got a Microsoft EULA agreement regarding a bunch of stuff. Whats that about? A MS eula in my linux terminal? not cool! I don't know whats the deal on that but anyone with past experiences on the matter if you coud please help out it would be great. It's happened a few times on the occasion that I wish to install a program

---

### Post by cipherboy_loc on 2011-02-03
What command gives you the Microsoft EULA? Is it an apt-get or another command?


Cipherboy

---

### Post by josh6190 on 2011-02-03
I cant remember the whole command but it's an apt-get I was almost positive

---

### Post by cipherboy_loc on 2011-02-03
Try:

```

history | grep -i 'apt-get' | tail -n 5

```


That should give you the last couple of apt-gets that you have run.



Cipherboy

---

### Post by howefield on 2011-02-03
Could well be ttf-mscorefonts-installer, installed as a dependency of another application if you didn't install it independantly.

---

### Post by ThePiper on 2011-02-05
> **howefield said:**
> Could well be ttf-mscorefonts-installer, installed as a dependency of another application if you didn't install it independantly.


Yes, it is the ttf-mscorefonts-installer. It popped up when I did my latest Update. I moved to Ubuntu to get away from Microsoft End User License Agreements so to see an MS EULA pop up on my machine was not something that made me very happy. :frown:

I have declined the EULA and now wait in morbid fascination to see if anything crashes or won't work which is what happens if you decline EULA's on MS Windows.

I will post on Launch Pad if and when I have trouble. If it gets really bad, I will move to another distro.

---

### Post by howefield on 2011-02-05
> **ThePiper said:**
> Yes, it is the ttf-mscorefonts-installer. It popped up when I did my latest Update. I moved to Ubuntu to get away from Microsoft End User License Agreements so to see an MS EULA pop up on my machine was not something that made me very happy. :frown:

But surely you must have expected it ?

It doesn't install by itself. 

> I have declined the EULA and now wait in morbid fascination to see if anything crashes or won't work which is what happens if you decline EULA's on MS Windows.

I will post on Launch Pad if and when I have trouble. If it gets really bad, I will move to another distro.

Just to point out that ttf-mscorefonts-installer isn't part of an Ubuntu default install.

---

### Post by ugm6hr on 2011-02-05
Ubuntu does not stop you from installing any proprietary software, which obviously includes software from Microsoft (and Adobe, and others).
Canonical have no control over any proprietary EULA from software vendors. For them to deliberately disable *voluntary* installation of such software would likely upset more people than the status quo.

---

### Post by josh6190 on 2011-02-07
hey all sorry I was absent from the forums from a bit! @Cipherboy, I have since used other apt-get commands that havent had the problem, so the information that command would bring back would not help me too much, but thats ok, because I haven't had the pop-up since. @howefield, and @ThePiper it was indeed the ttf-mscorefonts-installer! Is there something I can do to install this to prevent a further failed installation of another program? Anyways, thanks for all the help guys!

---

### Post by PRC09 on 2011-02-07
Another post on the said subject.....


[http://georgia.ubuntuforums.org/showthread.php?t=1645960](http://georgia.ubuntuforums.org/showthread.php?t=1645960)

---


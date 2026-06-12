---
title: "Inspiron 700m does not start after Upgrade or with LiveCD"
date: 2010-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bubucgn on 2010-05-02
I just upgraded my Dell Inspiron 700m from 9.10 to 10.04, no error messages, seemingly all went fine.
After reboot I see the ubuntu logo with the running dots.
Then very briefly a small distorted image is shown, after that a black screen and nothing else.
I tried to boot from the LiveCD. Same symptoms.
The LiveCD boots well on other systems.

I have just finished reinstalling 9.10 ...

---

### Post by P4man on 2010-05-02
try safe graphics mode. 
From the livecd, press escape when you get the initial purple screen with the keyboard logo. Then in the menu at the bottom chose "nomodset".

Im guessing you have intel onboard graphics and are hit by this issue:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

---

### Post by Unicast on 2010-05-02
And there's a weath of information here: [http://ubuntuforums.org/showthread.php?t=1463294](http://ubuntuforums.org/showthread.php?t=1463294)

Just googled the Inspiron 700m - looks like you have the 855GM chipset, which isn't playing nicely with Lucid for everyone.

I took the extreme step of installing a newer kernel - working very well for me so far.

---

### Post by P4man on 2010-05-02
> **Unicast said:**
> 
Just googled the Inspiron 700m - looks like you have the 855GM chipset, which isn't playing nicely with Lucid for everyon

Ah, indeed. some workarounds here as well:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

but frankly, Id avoid lucid with that gpu for now.

---


---
title: "Am I the only one who got another shafted system from an update?"
date: 2006-09-19
forum: Desktop Environments
---

### Post by tomBorgia on 2006-09-19
Commit Log for Tue Sep 19 10:08:20 2006

Upgraded the following packages:
libgnutls12 (1.2.9-2ubuntu1) to 1.2.9-2ubuntu1.1
linux-headers-386 (2.6.15.24) to 2.6.15.25
linux-image-386 (2.6.15.24) to 2.6.15.25

Installed the following packages:
linux-headers-2.6.15-27 (2.6.15-27.48)
linux-headers-2.6.15-27-386 (2.6.15-27.48)
linux-image-2.6.15-27-386 (2.6.15-27.48)

Guess what, this broke my xserver =D> (not for the first time). I'm back on 2.6.15-23 cuz it works with NVIDIA.

I'm not a linux n00b and I love ubuntu except for the blatant LACK of testing regarding the updates... if Microsoft broke the GUI through a system update Slashdot/etc would have a field day... 

Perhaps its just my system that got ill today... sorry for ranting... I've seen so many "sort the updates" threads here ](*,)

---

### Post by Ramses de Norre on 2006-09-19
```
sudo aptitude install linux-386
```
You somehow seem to have uninstalled the meta package for your kernel which causes the restricted modules not to be updated -> broken drivers.

Ubuntu is absolutely not to blame for this.

---

### Post by tomBorgia on 2006-09-19
"You somehow seem to have uninstalled the meta package" - well I didn't do it... so how is ubuntu not to blame :lol:

---

### Post by johanster on 2006-09-19
Also had the same problem. Had to revert to the old kernel.

Xorg.log said:
```

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***

```

And your right about the testing. Not that I would like the Ubuntu project to imitate Debian in that regard, but thurough testing would be preferred, especially for the stable release.

---

### Post by tomBorgia on 2006-09-19
BTW... thanks for the fix tho.:D

---

### Post by johanster on 2006-09-19
Oh wait, Ramses you're right. It is me who is to blame. I didn't have the restricted modules metapackage installed, only the one for my previous kernel version.
*hangs head in shame*

---

### Post by Ramses de Norre on 2006-09-19
This isn't about testing from the ubuntu side, they just can't hold everyones hand and tell you to make sure you have installed the restricted-modules and maybe also grub so you can boot..

It's your own responsibility to check whether you've got the restricted-modules installed when you use the nvidia drivers.. And that meta package gets installed by installation so if you don't have it you removed it somehow..

You can't start complaining about every update just because the devs messed up once.

---

### Post by tomBorgia on 2006-09-19
"It's your own responsibility to check whether you've got the restricted-modules installed" Fair point but I thought I had them. Sorry to rub you the wrong bud, I thought I'd done a very calm rant! and its the only time I've complained...
Thanks for helping anyway Ramses

---

### Post by Ramses de Norre on 2006-09-19
I just think it's unfair that you see people getting all upset with every update since that Xserver incident, sorry if I sounded a bit too harsh..
I guess I needed to express this feeling sometime.

And I'm glad you've got your system back up ;)

---

### Post by tomBorgia on 2006-09-19
awww... group hug...

---

### Post by missmoondog on 2006-09-19
> **tomBorgia said:**
> "It's your own responsibility to check whether you've got the restricted-modules installed" Fair point but I thought I had them. Sorry to rub you the wrong bud, I thought I'd done a very calm rant! and its the only time I've complained...
Thanks for helping anyway Ramses

it's my responsibility? heck, if i thought i knew enough about linux to know that i'm supposed to have the restricted modules installed, i'd be able to compile my own kernel or write my own distro, or something!

i've NEVER removed any type file like that and all 7 of my machines got foobarred after these last couple incidents!

"this isn't about testing from the ubuntu side, they just can't hold everyones hand and tell you to make sure you have installed the restricted-modules and maybe also grub so you can boot.."

this is ALL ABOUT testing. or, lack of, i should say! ](*,)

---


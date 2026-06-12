---
title: "[Jaunty] msttcorefonts doesn't appear to be working in Firefox"
date: 2009-04-24
forum: General Help
---

### Post by turezky on 2009-04-24
I have just installed Ubuntu Jaunty and have updated the Firefox to 3.0.9.
After I installed the "msttcorefonts" package, the resulting appearance of the pages didn't change. New fonts were not applied, as in previous Ubuntu releases.
Is there a workaround?

---

### Post by r4w on 2009-04-24
I have the same problem. And when I use skype the same happens:s

---

### Post by turezky on 2009-04-24
Yep, Skype doesn't show the msttcorefonts too :(

---

### Post by dcstar on 2009-04-24
> **turezky said:**
> Yep, Skype doesn't show the msttcorefonts too :(

The **msttcorefonts** package is now replaced by the **ttf-mscorefonts-installer** package, do you have this installed?

---

### Post by Kareeser on 2009-04-24
Really? I've installed msttcorefonts on three computers in the past two days with no problems... all fonts installed and render correctly.

Under what conditions should ttf-mscorefonts-installer be used?

---

### Post by turezky on 2009-04-25
No luck :(
The ttf-mscorefonts-installer was already installed when I tried to do this. I tried both removing msttcorefonts and reinstalling ttf-mscorefonts-installer, but without any results.

---

### Post by turezky on 2009-04-25
> **Kareeser said:**
> 
Under what conditions should ttf-mscorefonts-installer be used?
Seems like ttf-mscorefonts-installer is installed whenever you install msttcorefonts (a dependency?).

---

### Post by praveenmarkandu on 2009-04-25
i also have the same problem which i started a thread here:
[http://ubuntuforums.org/showthread.php?t=1129820](http://ubuntuforums.org/showthread.php?t=1129820)

the thread was closed when the jaunty development forum was closed.
msttcorefonts is a dummy package which does install ttf-mscorefonts-installer. it still doesnt work.

```
sudo fc-cache -rv
```
doesnt seem to work

*i think* the issue is only when you do an upgrade instead of a fresh install. im still waiting for some sort of workaround.

---

### Post by turezky on 2009-04-25
I did a fresh install :)

---

### Post by turezky on 2009-04-25
Bump!

---

### Post by turezky on 2009-04-25
Guys from [this]("http://ubuntuforums.org/showthread.php?t=1135125") thread seem having found a workaround, but it didn't work at my computer. If anyone succeeds please reply here :)

---

### Post by r4w on 2009-04-25
I made a fresh install too

---

### Post by praveenmarkandu on 2009-04-26
> **turezky said:**
> Guys from [this]("http://ubuntuforums.org/showthread.php?t=1135125") thread seem having found a workaround, but it didn't work at my computer. If anyone succeeds please reply here :)

didnt help me as well

---

### Post by r4w on 2009-04-26
Any ideas guys?

The problem is really annoying.lol

---

### Post by r4w on 2009-04-29
```
sudo apt-get install ubuntu-restricted-extras
```
solved firefox's problem for me (even though not skype's)

---

### Post by turezky on 2009-05-01
> **r4w said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```
solved firefox's problem for me (even though not skype's)

Didn't work for me :(

---

### Post by CoreyB. on 2009-05-24
I have this problem too, it worked fine when I used it on Intrepid, but does not work on a fresh install of Jaunty.

---


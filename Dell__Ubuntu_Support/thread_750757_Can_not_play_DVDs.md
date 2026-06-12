---
title: "Can not play DVDs"
date: 2008-04-09
forum: Dell  Ubuntu Support
---

### Post by Denny Johnson on 2008-04-09
Running Feisty and Totem on 1420n
I've read everything related that I can find here.
What I've done:
Installed the ubuntu restricted extras package, and
```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
```
sudo apt-get install libdvdcss2
```
```
sudo apt-get install w32codecs
```
I did this last night and was stoked:) when I could play a DVD.......but then it stopped 10 minutes from the end and I could not get it to finish.:(
Today I tried another DVD, it stopped after 30 minutes. A small window popped up "An error occurred......could not read from resource"
So close but so far away :confused: 
Any help greatly appreciated.
Thanks

---

### Post by meho_r on 2008-04-09
Check dvd discs, maybe there are scratches causing them to stop. Or maybe your dvd drive is the problem. From what you said, it shouldn't be any software/codecs/player problem...

---

### Post by Denny Johnson on 2008-04-10
I tried a few more things, was about ready to give up, then found this
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)
installed VLC and watched a DVD:)
thanks stchman

---


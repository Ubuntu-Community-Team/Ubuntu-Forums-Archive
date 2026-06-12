---
title: "[SOLVED] apt troubles"
date: 2006-10-01
forum: Desktop Environments
---

### Post by beneedict on 2006-10-01
Hi!
My adept crashed yesterday and now I have following problem:

sudo apt-get -f install
-->Segmentation fault (core dumped)

same with aptitude:
sudo aptitude
Aua!  SIGSEGV erhalten, sterbe...
Segmentation fault (core dumped)

adept is not working any more either...

I am using ubuntu edgy eft AMD64 with kubuntu-desktop (works great actually!)

PS.: I have already tried "apt-get clean" and so on...

---

### Post by wanamoa on 2006-10-01
Hello,

i've got the same problem with apt...](*,) 
I've tried apt-get clean but nothing works. I desperate to find a solution, i can't install packets anymore.

PS: sorry, my english may be light

---

### Post by rubengs on 2006-10-01
Same problem here apt-get is really needed, this failure is critical. I'm running edgy generic.

---

### Post by rubengs on 2006-10-01
Solution from other thread: 


[http://www.ubuntuforums.org/showthread.php?t=266566&highlight=apt-get+error](http://www.ubuntuforums.org/showthread.php?t=266566&highlight=apt-get+error)

Hi,


check if there's a new version of apt in the repos
[http://packages.ubuntu.com/edgy/base/apt](http://packages.ubuntu.com/edgy/base/apt)

if yes, then download and install with
dpkg -i <name>

or check if you still have some older working version of apt in /var/cache/apt/archives.... and install that and then do not upgrade it until you know this issue is fixed in repos...


- Tero
  	
Join Date: Jul 2005
Beans: 4
Re: Segfault when apt-get anything
Thanks!

Solved downgrading to dapper version and upgrading again. Hope it's just an accident...[/HTML][/HTML]

---


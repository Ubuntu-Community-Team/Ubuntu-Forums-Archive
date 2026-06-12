---
title: "Problems installing Firefox"
date: 2006-09-27
forum: Desktop Environments
---

### Post by fatsheep on 2006-09-27
I'm a 64-bit user and as many 64-bit users do I installed 32-bit firefox to get plugins like flash, java, and mplayer working.  Unlike most 64-bit users I went the extra mile and replaced 64-bit firefox with 32-bit firefox.  BAD MISTAKE - Now all my gecko based applications are brocken.  Apparently yelp, epiphany, and all other gecko applications depend on the DEFAULT firefox to work.  

I have removed firefox 32-bit and installed it in a seperate directory.  Now I'm trying to the 64-bit (default) firefox.  I'm running into problems.  When I try to install the "firefox" package in synaptic I get this error message:

> 
**The following problems were found on your system:**

E: /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.7-ubuntu0.6.06_amd64.deb: trying to overwrite `/usr/lib/mozilla-firefox', which is also in package j2re1.4


The funny thing is that the j2re1.4 package isn't installed and  /usr/lib/mozilla-firefox does not exist:

> fatsheep@fatsheep:~$ **sudo rm /usr/lib/mozilla-firefox**
Password:
rm: cannot remove `/usr/lib/mozilla-firefox': No such file or directory


---

### Post by pay on 2006-09-28
you could force Firefox to install, though I wouldn't recommend it sudo dpkg -i --force-all /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.7-ubuntu0.6.06_amd64.deb
It will most likely cause problems if you do that. If that directory that its complaining about isn't there then maybe creating it will help.:confused:

---

### Post by fatsheep on 2006-09-28
Turns out all I had to do was install that JRE package and then install firefox. ](*,)  Thanks for the help.

---


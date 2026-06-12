---
title: "How to update GPG key?"
date: 2005-11-09
forum: Desktop Environments
---

### Post by Dvirp on 2005-11-09
I recently got this error when I updated apt: 
```
GPG error: http://us.archive.ubuntu.com breezy-updates Release: The following  signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

After poking around [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) I noticed there is a file with the GPG signature.  What command can I issue to update my GPG key so I don't have to be warned that my packages are not verified?

---

### Post by aysiu on 2005-11-09
Take the *us* out of that address. See the first link in my sig.

---

### Post by abovett on 2005-11-11
I'm running four Breezy boxes - all with the same sources.list file - and one of them is giving this same "invalid signature" error when I do apt-get update but the other three are fine. I'm pointing at archive.ubuntu.com and security.ubuntu.com.

Here's the actual error:
```
W: GPG error: http://archive.ubuntu.com breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

```

and here's my sources.lst file:
```
deb http://archive.ubuntu.com/ubuntu/ breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted

deb http://archive.ubuntu.com/ubuntu/ breezy universe
deb-src http://archive.ubuntu.com/ubuntu/ breezy universe

deb http://archive.ubuntu.com/ubuntu/ breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy multiverse

deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted

deb http://archive.ubuntu.com/ubuntu/ breezy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ breezy-updates universe

deb http://archive.ubuntu.com/ubuntu/ breezy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy-updates multiverse

deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted

deb http://security.ubuntu.com/ubuntu/ breezy-security universe
deb-src http://security.ubuntu.com/ubuntu/ breezy-security universe

deb http://security.ubuntu.com/ubuntu/ breezy-security multiverse
deb-src http://security.ubuntu.com/ubuntu/ breezy-security multiverse

deb ftp://ftp.nerim.net/debian-marillat sid  main

deb http://ubuntu.tower-net.de/ubuntu/ breezy java

```

Any ideas, anyone?

---

### Post by abovett on 2005-11-11
Fixed it!

I changed mirrors (to the US one) by changing arcive.ubuntu.com to us.archive.ubuntu.com and did an apt-get update, then changed it back and did it again!

I guess changing mirrors causes it to reload the keys or something whilst just doing apt-get update with the same source didn't touch tghe keys. Don't know why the problem occurred in the first place, though :(

Andy B

---

### Post by Wandering Wombat on 2005-11-11
No matter what I do I constantly get the badsig warning 

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com> <<< who is this guy lol, tell him to please fix his signature ;) 

Oh breezy how can you be so good yet have these niggling little problems lol, oh well maybe I will just start from scratch when I get my shiny new Breezy install CD's! You just get it sorted the way you want......., oh never mind lol.

---


---
title: "apt-get timeout?"
date: 2005-06-23
forum: Desktop Environments
---

### Post by IchBin on 2005-06-23
I've been trying to gett firefox installed for quite a while now. I try to run apt-get update, but everytime I do I get mostly timed out on the connections. Here's a little snippet of my console.
```
Err http://us.archive.ubuntu.com hoary Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://security.ubuntu.com hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com hoary Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://us.archive.ubuntu.com hoary-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Ign http://security.ubuntu.com hoary-security Release
```

These time outs take **forever.** 
Additionally, when I try to 'apt-get install mozilla-firefox' I get all the timeouts again and it will not let me install. Is there something I need to do to make apt-get work?

Here's a copy of my sources list.

```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

## Multi Universe added by me. :)
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe
```

---

### Post by rachii on 2005-06-23
did you run ```
sudo apt-get update
``` after adding the repositories

---

### Post by IchBin on 2005-06-23
[QUOTE=rachii]did you run ```
sudo apt-get update
``` after adding the repositories[/QUOTE]
 Yes that's what the first command was that I did. Then after being unable to because of time out I tried apt-get install mozilla-firefox and had the same problem.

---

### Post by IchBin on 2005-06-23
I thought to myself, maybe you should try your eth0 (wired ethernet) instead of your wireless connection. I did, and it works! Anyone have a clue why I can surf/email/ssh through my wireless and not apt-get?

The next problem would be that after installing firefox I cannot browse the web. It simply will not connect to any site I put in the address bar. I can ping to any site from the terminal. I can browse with Konquerer. But I can't browse with Firefox. I have it set to automatically connect to the internet. I even tried auto detect settings. Nothing worked. Any thoughts?

---


---
title: "Beryl removes alot of rightclick options on the apps"
date: 2007-06-28
forum: Desktop Effects &amp; Customization
---

### Post by Sjovan on 2007-06-28
Hey, my problems is that I can't se stuff like move to workspace right/left, 1-4 any more. What has happend? how can i config this?

---

### Post by hyperair on 2007-06-28
That happens due to the incompatibility of the windows navigator constructor kit library (libwnck18) with viewports. To fix this, go to Synaptic Package Manager, and look for libwnck18, libwnck18-common, and libwnck18-dev. For each one of them, Package->Force Version, and select 2.16-*. After which, you have to lock the versions to ensure that update-manager doesn't try to upgrade them (Package->Lock Version)

---

### Post by Sjovan on 2007-06-28
ah, i got my self another prob.....

> W: Failed to fetch [http://ubuntu.beryl-project.org/pool/feisty/main/libwnck/libwnck18_2.16.1-0ubuntu1.1_i386.deb](http://ubuntu.beryl-project.org/pool/feisty/main/libwnck/libwnck18_2.16.1-0ubuntu1.1_i386.deb)
  404 Not Found [IP: 80.77.247.17 80]


W: Failed to fetch [http://ubuntu.beryl-project.org/pool/feisty/main/libwnck/libwnck-common_2.16.1-0ubuntu1.1_all.deb](http://ubuntu.beryl-project.org/pool/feisty/main/libwnck/libwnck-common_2.16.1-0ubuntu1.1_all.deb)
  404 Not Found [IP: 80.77.247.17 80]

then i tryed to download a packeg man....

```
root@---:/home/sjovan/Desktop/libwnck/libwnck-2.16.1# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... configure: error: newly created file is older than distributed files!
Check your system clock

```

---

### Post by hyperair on 2007-06-29
Why don't you try the first option again? It seems to work for me. Perhaps the server was down at that time?

---

### Post by Sjovan on 2007-06-29
> **hyperair said:**
> Why don't you try the first option again? It seems to work for me. Perhaps the server was down at that time?
No, same erro to day :/

---

### Post by hyperair on 2007-06-29
Replace [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/).... with [http://208.113.193.9/](http://208.113.193.9/).....

See if it works. That's the IP I get anyway. If not, PM me with your email, I'll just send the debs over to you.

---

### Post by munkar on 2007-07-01
apparently i can't force versions on the libwck packages.... :(

---

### Post by hyperair on 2007-07-01
Oh you'll have to add the Beryl repositories:

Add this to System->Administration->Software Sources under third party repositories
"deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main" (without quotes)

And under Authentication, add this file: [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) (You'll have to download it to somewhere you can find first)

Then close it, let it reload the repository, upgrade (sudo apt-get upgrade) and then carry out the above instructions.

---

### Post by munkar on 2007-07-03
that worked -- thanks so much! :)

---

### Post by Sjovan on 2007-08-10
> **hyperair said:**
> Oh you'll have to add the Beryl repositories:

Add this to System->Administration->Software Sources under third party repositories
"deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main" (without quotes)

And under Authentication, add this file: [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) (You'll have to download it to somewhere you can find first)

Then close it, let it reload the repository, upgrade (sudo apt-get upgrade) and then carry out the above instructions.

But in my case nothing realy helps... Like now i'm trying to download the file and this is what i get...

```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
--00:19:33--  http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
           => `root@lupine.me.uk.gpg'
Resolving ubuntu.beryl-project.org... 80.77.247.17
Connecting to ubuntu.beryl-project.org|80.77.247.17|:80... 

```

As you can se... I don't realy connect.

alot of people have talked about the IP 208.113.193.9 and as you can se i'm trying to connect to some other IP. It's realy strange. Got the same situation in post [#3]("http://ubuntuforums.org/showpost.php?p=2930762&postcount=3")

what's wrong?

---

### Post by hyperair on 2007-08-11
Yeah you're getting a really weird IP there. In that case, I suggest that you go into your /etc/apt/sources.list file, replace all instances of "http://ubuntu.beryl-project.org" with "http://208.133.193.9" and change the command that you are currently running in the terminal to this:
```
wget http://208.133.193.9/root@lupine.me.uk.gpg
```

Alternatively, you can check out [www.opendns.com](www.opendns.com).

---

### Post by Sjovan on 2007-08-12
now i'm running opendns and everything looks good on that site, but it didn't help much.
```
sjovan@analplugg:~$ ping 208.133.193.9
PING 208.133.193.9 (208.133.193.9) 56(84) bytes of data.

--- 208.133.193.9 ping statistics ---
15 packets transmitted, 0 received, 100% packet loss, time 14000ms

sjovan@analplugg:~$ wget http://208.133.193.9/root@lupine.me.uk.gpg
--14:08:07--  http://208.133.193.9/root@lupine.me.uk.gpg
           => `root@lupine.me.uk.gpg'
Connecting to 208.133.193.9:80... 

sjovan@analplugg:~$ wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
--15:25:19--  http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
           => `root@lupine.me.uk.gpg'
Resolving ubuntu.beryl-project.org... 80.77.247.17
Connecting to ubuntu.beryl-project.org|80.77.247.17|:80...

```
This is what then of my /etc/apt/sources.list looks like...
```
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://no.archive.ubuntu.com/ubuntu/ feisty-backports main restricted uni$
# deb-src http://no.archive.ubuntu.com/ubuntu/ feisty-backports main restricted$

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://208.133.193.9 feisty main
deb-src http://208.133.193.9 feisty main

```
As you can se that didn't help much. There has to be a other file to edit or something.

---

### Post by hyperair on 2007-08-12
Okay, so that just sucks. Perhaps you could try using a proxy? It's evident that your ISP is blocking access to the website.

---


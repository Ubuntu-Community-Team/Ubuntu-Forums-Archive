---
title: "No Opera in software manager 8.04 LTS"
date: 2009-05-14
forum: General Help
---

### Post by droople on 2009-05-14
Hi All

I just installed 8.04 TLS and tried to install Opera.

I went to software manager, chose all Repositories,searhed Opera, no result :(

Anyone have any ideas?

Thank you in advance.

Cheers

---

### Post by konqueror7 on 2009-05-14
opera is not included in the software repos...try doing this...open the terminal

type
```
sudo gedit /etc/apt/sources.list
```

append the following line
```
deb http://deb.opera.com/opera/ lenny non-free
```
save and close

next, again in the terminal type,
```

sudo apt-get update
sudo apt-get install opera

```

---

### Post by droople on 2009-05-14
> **konqueror7 said:**
> opera is not included in the software repos...try doing this...open the terminal

type
```
sudo gedit /etc/apt/sources.list
```

append the following line
```
deb http://deb.opera.com/opera/ lenny non-free
```
save and close

next, again in the terminal type,
```

sudo apt-get update
sudo apt-get install opera

```


Thank you konqueror7.

Why they don't put Opera in Ubuntu?

---

### Post by konqueror7 on 2009-05-14
i really don't know, but what i know is that ubuntu select software applications that are used more often or are just sufficient for a basic user's needs...

---

### Post by droople on 2009-05-14
> **konqueror7 said:**
> i really don't know, but what i know is that ubuntu select software applications that are used more often or are just sufficient for a basic user's needs...

Thank you.

But you cannot say that Opera don't have enough users.....

---

### Post by rob1408 on 2009-05-14
Opera isn't an open source browser so it goes against the whole Ubuntu philosophy.

---

### Post by Arndt on 2009-05-14
> **konqueror7 said:**
> opera is not included in the software repos...try doing this...open the terminal

type
```
sudo gedit /etc/apt/sources.list
```

append the following line
```
deb http://deb.opera.com/opera/ lenny non-free
```
save and close

next, again in the terminal type,
```

sudo apt-get update
sudo apt-get install opera

```

I also want to install Opera (for the cases where Firefox doesn't do the right thing), but at the end of the step "apt-get update", it said

```
W: GPG error: http://deb.opera.com lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: You may want to run apt-get update to correct these problems
```

(When I ran it again, it said the same thing.)

---

### Post by kpkeerthi on 2009-05-14
Opera is in "Canonical Parner" repository. You can enable it from System -> Admin -> Software Sources. Partner repository contains closed source apps and hence not enabled by default. [[More]("https://help.ubuntu.com/community/Repositories/Ubuntu")]

---

### Post by Arndt on 2009-05-14
> **kpkeerthi said:**
> Opera is in "Canonical Parner" repository. You can enable it from System -> Admin -> Software Sources. Partner repository contains closed source apps and hence not enabled by default. [[More]("https://help.ubuntu.com/community/Repositories/Ubuntu")]

Doing that didn't help. From googling a little, it seems to mean that some mirror or other does not have the correct public key, but that downloading is supposed to work anyway. But I don't know how to get rid of the message.

Disregarding the message, fetching 'opera' did seem to work, thank you.

---

### Post by Bartender on 2009-05-14
Have you tried installing Opera from the Opera website?
Go to this website
[http://www.opera.com/browser/download/?os=linux-x86-64&ver=9.64&local=y](http://www.opera.com/browser/download/?os=linux-x86-64&ver=9.64&local=y)
and download the version of Opera for your version of Ubuntu.  Save the download to your desktop.  When finished, you should be able to click on it and package installer should do the rest.

---

### Post by kpkeerthi on 2009-05-14
> **Arndt said:**
> Doing that didn't help. From googling a little, it seems to mean that some mirror or other does not have the correct public key, but that downloading is supposed to work anyway. But I don't know how to get rid of the message.

Disregarding the message, fetching 'opera' did seem to work, thank you.

Adding the partner repository will not fix your APT GPG key issue. I just pointed out that opera is in a Ubuntu repository. 

> **Arndt said:**
>  But I don't know how to get rid of the message.
You have remove the bad deb line (lenny) from your sources.list

> 
Disregarding the message, fetching 'opera' did seem to work, thank you.
It got installed  from partner repository since you have that in your source.list

---


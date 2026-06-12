---
title: "Gwibber doesn't let me add any account on 10.4 LTS"
date: 2011-05-20
forum: Desktop Environments
---

### Post by karimone on 2011-05-20
I just added the ppa for gwibber stable and I installed the Gwibber 3.0.0.1 because the default gwibber on ubuntu 10.4.2 LTS doesn't let me add twitter account. Now, after launching the application, I can't add ANY account.

Here the screenshot where the selection of the service is **empty**.

[[IMG]http://img607.imageshack.us/img607/9127/gwibber.png[/IMG]](http://img607.imageshack.us/i/gwibber.png/)

Any help?

---

### Post by victorius on 2011-06-15
I have the exact same problem now on Ubuntu 10.10. I added the PPA and updated Gwibber.

Now -> no accounts and no possibility of adding new ones.

Did you find a solution to this problem?

---

### Post by karimone on 2011-06-16
No solution at the moment :-(

---

### Post by whchen on 2011-08-06
> **karimone said:**
> I just added the ppa for gwibber stable and I installed the Gwibber 3.0.0.1 because the default gwibber on ubuntu 10.4.2 LTS doesn't let me add twitter account. Now, after launching the application, I can't add ANY account.

Here the screenshot where the selection of the service is **empty**.

[[IMG]http://img607.imageshack.us/img607/9127/gwibber.png[/IMG]](http://img607.imageshack.us/i/gwibber.png/)

Any help?

try delete gwibber dir in ~/.cache and ~/.config:

```
rm -r ~/.cache/gwibber
rm -r ~/.config/gwibber
```

---

### Post by zhangjuneric on 2011-08-23
not sure if you solve the problem. I had the similar problem but get it solved. This is the way I did it. First kill the gwibber service from the system monitor. Then open the terminal and remove it. Check the following post to know how.

[http://ubuntuforums.org/showthread.php?t=1506578](http://ubuntuforums.org/showthread.php?t=1506578)


After that I reinstall gwibber just as usual.

sudo apt-get install gwibber

Everything is back to normal now.

Wish u good luck
[IMG]chrome://livemargins/skin/monitor-background-horizontal.png[/IMG]	[IMG]chrome://livemargins/skin/monitor-background-vertical.png[/IMG]	[IMG]chrome://livemargins/skin/monitor-play-button.png[/IMG]

---

### Post by fishtron on 2011-08-31
Looks like gwibber doesn't automatically install any of its service plugins by default. To install all of them, do:

```
sudo apt-get gwibber-service*
```

or selectively install the ones you want.  Search through apt for "gwibber-service" to see the list:

```
apt-cache search gwibber-service
```

---

### Post by jfed on 2011-08-31
Just out of curiosity, why did you post this in the "Desktop Environments" section? You'd probably get better results if you posted in the "General Help" section, as this issue really has nothing to do with graphical environments :p

---


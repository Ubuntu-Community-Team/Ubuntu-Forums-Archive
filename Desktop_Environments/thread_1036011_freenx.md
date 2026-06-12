---
title: "freenx"
date: 2009-01-10
forum: Desktop Environments
---

### Post by num on 2009-01-10
Hello,

I am trying to install FreeNX on the latest version of Ubuntu. I have tried several tutorials on how to do this but they are outdated and no longer work. Can someone tell me what i have to do to install the server software? Or provide a working tutorial?

---

### Post by kellemes on 2009-01-10
You mean this?
[https://help.ubuntu.com/community/FreeNX]("https://help.ubuntu.com/community/FreeNX")

---

### Post by num on 2009-01-10
yes thank you it installed but i cannot find it in the applications. what do i do?

this is what happened when i installed it:

[http://pastebin.com/m1fea4779](http://pastebin.com/m1fea4779)

---

### Post by kellemes on 2009-01-10
You should replace "VERSION" with "intrepid" in those added lines in /etc/apt/sources.list

---

### Post by num on 2009-01-10
and i should reinstall?

---

### Post by num on 2009-01-10
i still get the following issues:

[http://pastebin.com/m755fcd68](http://pastebin.com/m755fcd68)

---

### Post by kellemes on 2009-01-10
> **num said:**
> and i should reinstall?

Just follow the link I send but replace "VERSION" with "intrepid".

So the 2 lines you had to add to sources.list would be..
```
deb http://ppa.launchpad.net/freenx-team/ubuntu intrepid main
deb-src http://ppa.launchpad.net/freenx-team/ubuntu intrepid main
```

Than..
```
sudo apt-get update
```

etc..

---

### Post by num on 2009-01-10
yes i have tried that and i get the errors, see the pastebin link.

---

### Post by num on 2009-01-10
it just refuses to install. what to do?

---

### Post by num on 2009-01-10
please help

---

### Post by num on 2009-01-10
anyone?

---

### Post by Kokopelli on 2009-01-10
```
#
Do you want to ignore this warning and proceed anyway?
#
To continue, enter "Yes"; to abort, enter "No": y
#
Unrecognized input.  Enter either "Yes" or "No".
#
Do you want to ignore this warning and proceed anyway?
#
To continue, enter "Yes"; to abort, enter "No": y
```
you need to type "Yes" or "No"  not "y" or "n"  type "Yes" (sans quotes) then enter.

---

### Post by num on 2009-01-18
how can i configure FreeNX server to connect?

---

### Post by num on 2009-01-19
when i use nomachine to connect, i get an error saying that the user "root" cannot be authenticated. what is wrong?

---


---
title: "QuteCom (skype replacement)"
date: 2009-02-14
forum: Desktop Environments
---

### Post by andrea000 on 2009-02-14
Hi all

Does anyone know were or how i can download Qutecom? :( It is a open source soft phone previously known as WengoPhone.It is a opensource replacement for skype.
I am using ubuntu 8.04 with all the updates. 

Thank you

XOXOXO

---

### Post by cosine352 on 2009-02-14
[http://www.qutecom.org/](http://www.qutecom.org/)

did you tried Ekiga ?

---

### Post by andrea000 on 2009-02-14
No i looked at it is it any better then qutecom?on qutecom website i can't find the package to download.
Any help please.

---

### Post by mikewhatever on 2009-02-14
The link titled **Ubuntu packages:** is on the front page, however, the fact that they don't offer direct links should be taken as a hint. You might be better off using Ekiga after all.

---

### Post by benerivo on 2009-02-14
Ekiga should do the same job (or even just install skype?), but to get Qutecom, i would look at [https://edge.launchpad.net/~cavedon/+archive/ppa](https://edge.launchpad.net/~cavedon/+archive/ppa)

To install it, try...```
gksudo gedit /etc/apt/sources.list
```and add...```
deb http://ppa.launchpad.net/cavedon/ppa/ubuntu hardy main
```...to the end of the file. Then do...```
sudo apt-get update
``` and then open synaptic package manager to find and install it.

---

### Post by andrea000 on 2009-02-15
you all were right i got Qutecom installed and it wasn't that good
at all so installed ekiga Ekiga worked great 

Thanks a lot for your help guys    :popcorn:

---

### Post by foresto on 2009-05-18
Looks like the Ubuntu package on their site is out of date, and it's not in the Jaunty repository yet, but there is a backport request:

[https://bugs.launchpad.net/jaunty-backports/+bug/377644](https://bugs.launchpad.net/jaunty-backports/+bug/377644)

Update:  I just compiled QuteCom from the Karmic repository, and am pleased to find that it works with one of my SIP accounts that Ekiga fails with.  I think I'll stick with it.

---

### Post by FirstByté on 2009-05-25
I seem to have some firewall problems with my Ekiga. Even after I opened some ports [5000 to 5100 and so on] on my DLink DIR 300 wireless router, it still has issues connecting. I fired up KPhone and... voa lah! It's been working.

So you might wanna give KPhone a try. [I use Ubuntu 9.04 Jaunty]

```


sudo apt-get install kphone

```

---

### Post by cheffe76 on 2009-05-28
Here you might find an ubuntu package of qutecom for 9.04 


[https://edge.launchpad.net/~cavedon/+archive/qutecom](https://edge.launchpad.net/~cavedon/+archive/qutecom)


cheers

---

### Post by juaninse on 2009-09-02
Unfortunately ekiga's sound playback (ekiga 3.2.0) does not work in Jaunty.   I wonder why they included it if it wasn't working with pulse audio.

---

### Post by oguillaume on 2009-10-15
QuteCom binaries 
```
http://ppa.launchpad.net/cavedon/qutecom/ubuntu/pool/main/q/qutecom/
``` 

QuteCom Jaunty apt-get list.sources / synaptic repository are
```
deb http://ppa.launchpad.net/cavedon/qutecom/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/cavedon/qutecom/ubuntu jaunty main
``` 

Additional QuteCom Jaunty repositories:
```

deb http://ppa.launchpad.net/cavedon/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/cavedon/ppa/ubuntu jaunty main
```

Save the PPA Key text for the repository into a text file and important it in synaptic or using the comman line
```
http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xC1FE1A7B426FF7FA 
```

---


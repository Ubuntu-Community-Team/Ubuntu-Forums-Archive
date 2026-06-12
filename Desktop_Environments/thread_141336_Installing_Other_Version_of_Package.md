---
title: "Installing Other Version of Package"
date: 2006-03-08
forum: Desktop Environments
---

### Post by GordonFreeman83 on 2006-03-08
Hi all, I was wondering if anybody could help. I've been using linux for quite while and Ubuntu aswell but not sure how to do this.

I want to install PHP as a package through Synaptic, but the versions listed there are incompatible with what I'm doing. Is there a way to specify or browse through other versions of that package? For instance to find PHP 5.0.4 instead of PHP 5.0.5? Or can I obtain that package (.deb) from anywhere else?

Any help would be really appreciated! Thanks.

---

### Post by MichaelZ on 2006-03-08
Hello,

May be you can uninstall the new version, download the desired one and then install it.

Best wishes,
Michael

---

### Post by dave84 on 2006-03-08
hi!

i'm using *aptitude* most of the time.
here you can (just a short describtion):
1: search by entering a '/'
2: mark to install with '+'
3: get more info with 'enter'
4: scroll with the mouse keys
...

just search for the package you would like to install, press enter, scroll down and choose an other version with '+'.

that's it\\:D/ 

lg david

---

### Post by GordonFreeman83 on 2006-03-09
Sorry I'm not sure I explained myself correctly.

I know how to uninstall and install versions of software using the various utilities like apt-get synaptic etc. That's not the problem. The problem is the version that is offered is one i can't use. By this I don't mean php5 or php4, I mean the specific version number. For instance, if you go to Synaptic and click php5, or if you apt-get install php5 , the actual version that you get from that is 5.0.5 . You see I need a different specific version. php5 is OK, I can use php5, but the specific version of 5 that installs when you select or click that is one that I cannot use.

So my question is how can I control that and get a specific version, for instance 5.0.4 . Can I change an option somewhere, or is there a place I can go to to get that specific version. It's not that I can't use php5 and need php4 for instance, you see it's that actual version number that gets installed i need to control.

Any help would be awesome, thanks guys.

---

### Post by kkass on 2006-03-21
Here is the apt-get command to do what you are asking:

```
sudo apt-get install php5=<version-spec>
```

For example, the command to get the current version is as follows:

```
sudo apt-get install php5=5.0.5-2ubuntu1.2
```

---


---
title: "Loggin Menu"
date: 2013-04-03
forum: Desktop Environments
---

### Post by mayagrafix on 2013-04-03
I have installed a couple of other GUI (Lubuntu for example) on top of my normal Ubuntu OS to test them out but now would like to remove them from the Loggin Menu.

I tried **apt-get remove lubuntu** and got this message: 
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lubuntu

Any ideas? Thanks for your help, it is much appreciated :)

---

### Post by ibjsb4 on 2013-04-03
Go here

[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

---

### Post by mayagrafix on 2013-04-03
Followed ur advise, now machine will not boot. Recovery mode freezes on you are in **Low Graphics Mode** screen. If I use Live CD to re install Ubuntu OS, will it erase my files?

---

### Post by cortman on 2013-04-03
> **mayagrafix said:**
> Followed ur advise, now machine will not boot. Recovery mode freezes on you are in **Low Graphics Mode** screen. If I use Live CD to re install Ubuntu OS, will it erase my files?

Yes, it will, unless you copy them to an external HDD.
Before you do that though, can you run

```
sudo apt-get install ubuntu-desktop
```

and see if you can reinstall any pacakges you may have accidentally removed?
It seems strange that this should happen, as the link ibjsb4 gave you is known for being very reliable.

---

### Post by mayagrafix on 2013-04-03
my bad probably. I also ran apt/get auto something when promted by CLI after above link finnished. No big deal, was planning on removing Windows partition and re installing OS anyway. Managed to hook up USB drive to LiveCD and copy my Home folder, so no big deal.

---

### Post by mayagrafix on 2013-04-03
Well it wasn't so bad after all is said and done. There is an option on the Ubuntu Live CD to reinstall or recuperate an already installed or existing Ubuntu OS, which saves your docs and any extra applications you might have previously installed (but no such luck with Thunderbird Mail), and Firefox has its Sync thingy for bookmarks and add ons. Took me about a couple of hours to get going. Ce'st la vie!

---


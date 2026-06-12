---
title: "Problems installing KeepassX on 9.04 (Jaunty)"
date: 2009-05-05
forum: General Help
---

### Post by brian_hayward on 2009-05-05
I just did a clean install of Ubuntu 9.04 on my computer and i am having trouble installing KeepassX.  I can't find it in synaptic Package Manager, and while I'm not a command line wizard i've tried to install it from source which didn't work.  

Has anybody else been having the same trouble.  Can anybody offer me some suggestions as to why I can't install.  Any help and suggestions are greatly appreciated, thanks.

---

### Post by soro2005 on 2009-05-05
Get it from [here](http://www.getdeb.net/app/KeePassX)

It's in the universe repository, by the way. If you enable that in Synaptic (Preferences --> Repositories), you should find it. But the Getdeb version is more current.

---

### Post by HuckleSmothered on 2009-05-06
Once you check your repositories from soro2005's post, type in the terminal:
sudo apt-get install keepassx

---

### Post by brian_hayward on 2009-05-07
I finally got KeepassX installed...thanks for your responses.  However, how i got it installed is bothering me.  The same thing happened to me after i installed 8.10.  After the install, i could not find KeepassX using the synaptic package manager.  a few days later it finally shows up in the package manager.  Why is that?  Does my system need to be updated a time or three before repositories are updated, or is it something else I'm missing?

---

### Post by kostkon on 2009-05-07
> **brian_hayward said:**
> I finally got KeepassX installed...thanks for your responses.  However, how i got it installed is bothering me.  The same thing happened to me after i installed 8.10.  After the install, i could not find KeepassX using the synaptic package manager.  a few days later it finally shows up in the package manager.  Why is that?  Does my system need to be updated a time or three before repositories are updated, or is it something else I'm missing?
You need to use the regular search in Synaptic and not the quick-search, which in some cases doesn't work as supposed to.

*KeePassX* offers a *PPA*, you can add it to your software source list and you'll get automatic updates every time there is a new version of it.

Its PPA is [here]("https://launchpad.net/~keepassx/+archive/ppa").

---

### Post by brian_hayward on 2009-05-13
> **kostkon said:**
> You need to use the regular search in Synaptic and not the quick-search, which in some cases doesn't work as supposed to.

*KeePassX* offers a *PPA*, you can add it to your software source list and you'll get automatic updates every time there is a new version of it.

Its PPA is [here]("https://launchpad.net/~keepassx/+archive/ppa").

Thanks for the reply...another piece of the puzzle has just now been put in place.

---

### Post by HuckleSmothered on 2009-05-14
If immediately after an OS install, you need to update your packages before you can find ... well, most anything. 

This command in a terminal will do it:
> sudo apt-get update

Then the "apt-get install" command should find it.

---


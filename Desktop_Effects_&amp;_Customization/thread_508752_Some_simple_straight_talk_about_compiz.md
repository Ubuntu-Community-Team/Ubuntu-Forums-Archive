---
title: "Some simple straight talk about compiz"
date: 2007-07-24
forum: Desktop Effects &amp; Customization
---

### Post by Afkpuz on 2007-07-24
Ok, i need some me-specific help with beryl.  I'm running ubuntu 7.04 with an ati x700 radeon mobility graphics card.  Is there anyone kind enough to walk me through how to install compiz?  I have a basic knowledge of linux, but I cannot for the life of me get it working.  Every guide I've found on the forums doesn't work for me.  Am i simply forbidden from using beryl/compiz because of my graphics card?

---

### Post by michael37 on 2007-07-24
I have 64-bit Ubuntu Fiesty and I got Compiz running perfectly on my ATI Radeon Mobility X1400 card.

I realize the guides have been confusing, but here is what worked for me:

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

(Skip Method A, and carefully follow the ATI section for Method B, worked well for me)

and

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

My strong recommendation is to UNINSTALL compiz and all compiz packages before you begin with these two guides.  When you install compiz, you should install CompizFusion from another repository listed in the second guide.

---

### Post by Afkpuz on 2007-07-25
How can I find out which driver I'm using?  It says I need the fglrx driver.  Is that default on a fresh install?

---

### Post by michael37 on 2007-07-25
> **Afkpuz said:**
> How can I find out which driver I'm using?  It says I need the fglrx driver.  Is that default on a fresh install?

Excellent question.  There are two drivers for ATI video cards: "ati" driver and "fglrx" driver.

"ati" driver is the open source one with excellent 2D performance but no 3D performance.  ***This is the default driver.  Do not use it*** if you want 3D graphics (such as Desktop effects).

You want the "fglrx" driver.  How to determine that?

1. Log in, select System/Administration/Restricted Drivers Manager.  If you don't have such item, search the FAQs how to install it.

2. In Restricted Drivers Manager, you will see ATI driver.  Make sure it is selected and marked "in use".  If not, make it so.
You may need a reboot.

3. After the computer comes back up, open a terminal and run this command:
```
grep fglrx /etc/X11/xorg.conf
```

You should see output:
```
  Driver:     "fglrx"   
```

---


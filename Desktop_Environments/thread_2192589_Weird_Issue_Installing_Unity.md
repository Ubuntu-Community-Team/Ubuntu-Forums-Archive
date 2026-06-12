---
title: "Weird Issue Installing Unity"
date: 2013-12-08
forum: Desktop Environments
---

### Post by wewantutopia on 2013-12-08
Hi there.  I'm running 12.04 LTS.  I just had some something break causing issues with a black screen, no xorg etc.  

I'm back to a functioning desktop except I have no unity.  If i try to install unity it asks for libunity-core-....  If I try to install that it asks for something else.  If i try to install that it asks for unity-services.  If I try to install that it will, BUT, it wants to first uninstall 156 programs which look to be ALL of my gnome programs.

I'm not sure what to do.  How do I get unity back without uninstalling everything!!???

---

### Post by Bashing-om on 2013-12-09
wewantutopia; Hello ,

As a 1st approximation what results from:
```

sudo dkpg-reconfigure unity

``` maybe -if it can not be configured - will give some hints where the problem lies.

[INDENT][INDENT]maybe yes, maybe not so yes
[/INDENT][/INDENT]

---

### Post by BBQdave on 2013-12-09
> **wewantutopia said:**
> Hi there.  I'm running 12.04 LTS.  I just had some something break causing issues with a black screen, no xorg etc.

No issues running Ubuntu Unity 12.04LTS, system up to date. Did you install other DE's? Sometimes that can mess with a system, as different DE's do not always play nice with each other.

Easiest restore of your system, would be, back up data and fresh install :)

---

### Post by wewantutopia on 2013-12-10
Sorry I just checked my email and saw these replies. 

I ended up creating a fresh, identical install on a different partition on the same hard drive.

This ppa broke my system: ppa:videolan/master-daily while trying to install the Tunein Radio plugin for VLC. 

Thanks for the replies!

---

### Post by Bashing-om on 2013-12-10
wewantutopia; Great !

Any solution is better than no solution, huh . (Re-)install is one sure fire solution, always works .

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---


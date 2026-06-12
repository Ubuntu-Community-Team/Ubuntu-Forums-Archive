---
title: "I need some help installing a noobslab mac theme"
date: 2016-03-17
forum: Desktop Environments
---

### Post by joe200 on 2016-03-17
Here's the mac theme i was talking about.
[http://www.noobslab.com/2014/04/macbuntu-1404-pack-is-released.html?m=1](http://www.noobslab.com/2014/04/macbuntu-1404-pack-is-released.html?m=1)

I am using Ubuntu trusty 14.04 and i am getting some difficulties. when i try to install slingscold and the indecatier synapse, it says that they do not exist. Also, i downloaded the unity tweak tool and it does not show up anywhere. lastly, when i change the theme for the top of windows, but it just turns blue and nothing else.

---

### Post by Frogs Hair on 2016-03-17
Hello and Welcome

Try the following command. ```
unity-tweak-tool
```  If PPA packages are not found (synapse or others) it's usually a connection problem or the fault of those who maintain the PPA. As I remember noobslab has a contact link on the web site. 14.04 has gone through some changes since release and perhaps some MacBuntu packages need updates.

---

### Post by buzzingrobot on 2016-03-18
I just took a look and those packages are still in the Noobslab PPA. So a connection issue seems likely. 

This incantation in a terminal  --  
> dpkg -s packagename | grep Status

will tell you if a package is installed.  E.g., "dpkg -s unity-tweak-tool | grep Status".

---


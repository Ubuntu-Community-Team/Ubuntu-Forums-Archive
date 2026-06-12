---
title: "netbook desktop environment"
date: 2010-11-05
forum: Desktop Environments
---

### Post by vinay nadig on 2010-11-05
hi, i recently upgraded from 10.04 to maverick(desktop edition).
the problem is my netbook edition environment is not working properly.. can any1 tell me how to reset/reinstall the packages for netbook environment? 
thnx in advance..  :)

---

### Post by sikander3786 on 2010-11-05
Is Gnome itself working properly?

There are actually 2 netbook packages named ubuntu-netbook and ubuntu-netbook-remix.

I think the ubuntu-netbook-remix is the older one and ubuntu-netbook is the newer one with unity.

You can check which one is installed. Purge it and reinstall.

---

### Post by vinay nadig on 2010-11-05
nope, it still doesnot work. :(
i purged all the ubuntu-netbook packages, logged out and checked in the login screen just to make sure.
sure enough, the ubuntu netbook option had disappeared.
logged in and reinstalled it. but the problem still persists.. :(
here s the screenshot of my desktop
[http://imagebin.ca/view/9czHuzb.html](http://imagebin.ca/view/9czHuzb.html)

notice the 2 bars at the top and left..
those are supposed to be my panels.. :(

btw, thnx for the quick reply. :)
any more ideas??

---

### Post by sikander3786 on 2010-11-05
Not sure about that.

However you can install the latest netbook interface (and also the default desktop interface from 110.04 onwards) by,

```
sudo apt-get install unity
```

[http://linux-software-news-tutorials.blogspot.com/2010/06/install-unity-interface-in-ubuntu-1010.html](http://linux-software-news-tutorials.blogspot.com/2010/06/install-unity-interface-in-ubuntu-1010.html)

Give it a try.

---

### Post by vinay nadig on 2010-11-05
yup did that and it worked.. but the side panel is still not visible. :(
did a google search and it is a bug i guess..
thnx for the reply.. :)
cheers!!

---


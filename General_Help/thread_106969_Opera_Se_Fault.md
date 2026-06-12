---
title: "Opera Se Fault"
date: 2005-12-21
forum: General Help
---

### Post by EEPS on 2005-12-21
Hi, I am trying to install the Opera web Browser, I only saw one package called "opera" in Synaptic and it sayed it was not a real package. I downloaded the Ubuntu package for opera from their web site instead. It is for Ubuntu 5.10 and everything, I ran sudo dpkg -i opera.... and it installed correctly after I installed some dependancies (qtlibs and some xlibs) When I run opera from the console, I get "Segmentation fault" no error or anything. Any one else succesfully installed opera? Is their a real opera package in apt?

-Thanks

---

### Post by kairu0 on 2005-12-22
I have installed the Breezy version of Opera from opera.com several times without any problem. Are you using SCIM, by chance?

Also, here are the official apt repositories for Opera to add to /etc/apt/sources.list if you like:

```
# The Opera Web Browser
deb http://deb.opera.com/opera/ stable non-free
deb http://deb.opera.com/opera/ testing non-free
deb http://deb.opera.com/opera/ unstable non-free
```

---

### Post by EEPS on 2005-12-22
I don't believe I am using SCIM, just default install of ubuntu..., I will try the repositories though thanks

---

### Post by cowlip on 2006-01-08
Hi, it's likely mozilla plugin problems

Try to follow this thread: [http://my.opera.com/community/forums/topic.dml?id=108820&t=1130281303&page=1](http://my.opera.com/community/forums/topic.dml?id=108820&t=1130281303&page=1)

Clear ~/.opera/pluginpath.ini of everything except the first path (or change them to 0 instead of 1)

and try: [http://my.opera.com/community/forums/topic.dml?id=108820&t=1130281303&page=1](http://my.opera.com/community/forums/topic.dml?id=108820&t=1130281303&page=1)

---


---
title: "How do sources.list entries work?"
date: 2005-02-05
forum: Desktop Environments
---

### Post by adamw on 2005-02-05
I am noticing various degrees of behavior when I modify sources.list, and I was wondering if someone could explain how this works.  The question is, why can I, for example, download "httrack" when my configuration is:


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main universe multiverse

but not when it is:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty-security main restricted universe multiverse

Also, if I change "warty" to "hoary" in order to get a newer version of, say, Firefox and then change it back to warty, will I possibly break my system if I ever try to apt-get remove one of the dependant libraries which Firefox has?

---

### Post by llamakc on 2005-02-05
You can have both warty and hoary sources lines and specify which one you want by using the -t flag:
 
 apt-get install -t unstable some_packagename
 
 Or you could use pinning so that Warty is used other than firefox. Could run into dependency hell though. I've done this in the past to pin down uw-imapd. Check `man apt_preferences` for more.

---

### Post by az on 2005-02-05
You need both sources.list entries.

"will I possibly break my system"
probably.  Instead of playing with Hoary, use the Warty backports.  Search the forum for the url.  Install Hoary if you want to shake it down and find bugs, but not if you are worried about creating problems.

---

### Post by adamw on 2005-02-06
Thanks for the tip on the backports.  Unfortunately, my main dev box is a powerbook laptop and backports doesn't have anything for PPC (doh!).  But I will definitely try it out on my AMD box.

---


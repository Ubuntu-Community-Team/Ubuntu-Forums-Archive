---
title: "How to set up the limit for session time?"
date: 2008-12-07
forum: General Help
---

### Post by yesint on 2008-12-07
Dear All,
I need to restrict certain user to be logged in no more than 2 hours each day. When this time is used, the user should be logged out automatically and the login should be blocked till next day.
To my surprise I didn't find any good answer to this apparently simple problem. What is the best way to do this? 

Thanks in advance for any suggestions!

---

### Post by .nedberg on 2008-12-07
Funny you should ask...

I and a couple of other forum members are developing timekpr for that exact reason. Find out more about it here:
[http://ubuntuforums.org/showthread.php?t=887769](http://ubuntuforums.org/showthread.php?t=887769)

If you use Intrepid you can add my ppa for the beta versions, or download it from my web page.

```
deb http://ppa.launchpad.net/nedberg/ubuntu intrepid main
deb-src http://ppa.launchpad.net/nedberg/ubuntu intrepid main
```

or

[www.nedberg.net/timekpr_0.2.2~b5_all.deb]("www.nedberg.net/timekpr_0.2.2~b5_all.deb")

The ppa will be updated with beta versions, and could potentially include new bugs along the way. But if you are up for some testing, then pleas try it and report any problem on launchpad or in the main thread!

---

### Post by yesint on 2008-12-08
Looks great! I'll definitely try your solution. 
However, I'm curious how is it possible to do the same with standard linux tools?

---

### Post by .nedberg on 2008-12-08
> **yesint said:**
> Looks great! I'll definitely try your solution. 
However, I'm curious how is it possible to do the same with standard linux tools?

Well, timekpr uses some pretty "standard" linux tools. Python mainly, pam and bash. It is based on a pure bash script. You would need only a selection of bash commands to do the same as timekpr, but you would not get notifications, problems with multiple users and configurations.

---

### Post by yesint on 2008-12-08
I've tried timekpr. It works nice, but it also sets the 5h limit for ordinary user, while not asked to do this. This is weird and not acceptable.

---

### Post by .nedberg on 2008-12-08
> **yesint said:**
> I've tried timekpr. It works nice, but it also sets the 5h limit for ordinary user, while not asked to do this. This is weird and not acceptable.

Hummm, it should not do that! Are you sure the user is kicked? At the moment there is a known "problem" with the timekpr-client. It will notify any user, also unrestricted ones, about the time left until midnight. Unrestricted users are not kicked though.

---

### Post by .nedberg on 2008-12-08
I can also inform you that I just commited a fix to this problem! I will (probably) release a new .deb by the end of the week!

---


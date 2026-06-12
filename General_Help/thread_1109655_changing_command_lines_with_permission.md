---
title: "changing command lines with permission"
date: 2009-03-29
forum: General Help
---

### Post by imparja2 on 2009-03-29
I want to do the following: 

Originally Posted by Xiong Chiamiov  View Post
Thank you very much. I haven't had problems with rebooting, only shutting down (no idea why), so in the file /etc/init.d/halt I changed the line
Code:

halt -d -f -i $poweroff $hddown

to
Code:

halt -d -f $poweroff $hddown

I tried to display this file and when i made the change I couldn't save it. It said permission denied how can I save this change and get around this problem?

can I just do it from the terminal what command line should I type?

---

### Post by dcstar on 2009-03-29
> **imparja2 said:**
> I want to do the following: 

Originally Posted by Xiong Chiamiov  View Post
Thank you very much. I haven't had problems with rebooting, only shutting down (no idea why), so in the file /etc/init.d/halt I changed the line
Code:

halt -d -f -i $poweroff $hddown

to
Code:

halt -d -f $poweroff $hddown

I tried to display this file and when i made the change I couldn't save it. It said permission denied how can I save this change and get around this problem?

can I just do it from the terminal what command line should I type?

```
sudo gedit whatever
```

---


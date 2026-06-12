---
title: "Help with terminology"
date: 2009-01-07
forum: General Help
---

### Post by maestrobwh1 on 2009-01-07
I have very sluggish performance in firefox with Intrepid on some fairly adept machines.  Tabs and dropdown boxes appear slowly and well, it is unusable.

I found this post in bugs, but the bug was closed because it is a system issue for that person.

> Ok, nevermind. I found the problem... it's because **the local loopback wasn't upping at boot **and it made some GTK apps slow.

Fixed it and it's fine now.


I don't know what the **the local loopback wasn't upping at boot ** is, other than "lo."  How can I check this?

---

### Post by hangfire on 2009-01-07
> **maestrobwh1 said:**
> I have very sluggish performance in firefox with Intrepid on some fairly adept machines.  Tabs and dropdown boxes appear slowly and well, it is unusable.

I found this post in bugs, but the bug was closed because it is a system issue for that person.



I don't know what the **the local loopback wasn't upping at boot ** is, other than "lo."  How can I check this?

Run the command:

**ifconfig -a**

The output should include an "lo" entry with an inet addr of 127.0.0.1.

-HF

---


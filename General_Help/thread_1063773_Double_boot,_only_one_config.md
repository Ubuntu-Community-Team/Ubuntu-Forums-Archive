---
title: "Double boot, only one config"
date: 2009-02-08
forum: General Help
---

### Post by Memes11 on 2009-02-08
Well, I have double boot Win XP pro 64bits - Ubuntu 8.10 64bits, I seldom boot on windows but still do it sometimes, but I want to be able to use it for some basic stuffs without needing to reconfig everything. I also want to be able to reinstall and come back quickly to the same config, so, I want to be able to use a common config for both OS.

I already setup Thunderbird so whatever the OS I booted, when I start Thunderbird, I always have the same mails folders, so, whatever the OS I am using, the downloaded mails are available in the other when I'll boot on it. I guess you understand what I mean.

Now I want to extend this to more properties, can you help me to find a thread or a webpage describing how to do :
- Thunderbird email-account parameters
- Thunderbird address book
- Mozilla Firefox bookmarks (if you have the tuto for Opera, it is welcome too)

Thanks in advance.

---

### Post by Memes11 on 2009-02-08
bump

---

### Post by Memes11 on 2009-02-09
nobody?

---

### Post by blazemore on 2009-02-09
If you've allowed your Linux installation to access your Windows partition, you can do this really easily.

On Windows, hit Super+R and run
```
firefox -profilemanager
```

Create a new profile, and set the storage to a simple directory (eg C:\Firefox Profile)

Run Firefox (This is important or the profile files won't be created)

Then on Linux run the same thing, create a new profile and set its location to the folder you defined in Windows (eg /windows/Firefox Profile).

Now your bookmarks, passwords and settings will be shared.

I don't use Thunderbird, but I'd imagine the same would apply.

---

### Post by Memes11 on 2009-02-09
Thanks a lot for this answer, I'll have a look on it tonight.

---

### Post by blazemore on 2009-02-09
Let me know if you run into problems.

---

### Post by Memes11 on 2009-02-10
Thanks a lot for this solution. 

I really appreciate as it works great but it is also a very clean solution (I found one other on the web but far less clean so I won't talk about it).

Thanks again

---

### Post by Memes11 on 2009-02-10
ah yes, one more, running ```
thunderbird -profilemanager
``` do the trick for thunderbird.:P:P:P:P:P

---


---
title: "HELP...installation of package interrupted."
date: 2009-05-11
forum: General Help
---

### Post by mickeyd1965 on 2009-05-11
hi,
I was trying to install frostwire and it stalled part way through the installation process. When i tried to run "synaptic package manager" it said, 


     E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


 can anyone please tell me how to correct the problem.


Thanks,  mickeyd1965.

---

### Post by Cheesemill on 2009-05-11
You just have to do what the error message tells you, open a terminal and type
```
sudo dpkg --configure -a
```
Enter your password and your done.

Cheesemill

---

### Post by AndThenWhat on 2009-05-11
Yeah all you need to do is open a Terminal window (Applications -> Accessories -> Terminal) and type in:

```
sudo dpkg --configure -a
```

Then hit enter, wait for it to finish and you're golden to re-run the Frostwire installer.

---

### Post by mickeyd1965 on 2009-05-11
Thanks alot that fixed it. I thought i had typed what you said , but it did nothing . I must have missed something the first time.
thanks greatly.

mickeyd1965

---


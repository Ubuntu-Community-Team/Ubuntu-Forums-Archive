---
title: "[SOLVED] synaptic issues!"
date: 2009-01-09
forum: General Help
---

### Post by imtheguido on 2009-01-09
Alright, so when I go to try and open synaptic manager I get this error:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

So fallowing directions, I try and use that exact command and get:

```
dpkg: requested operation requires superuser privilege
```

I continue to get the first error message when trying to install the same program with the sudo apt-get command in terminal. Anyone have any clue as to what is going on here? >.<

---

### Post by Giant Speck on 2009-01-09
> **imtheguido said:**
> Alright, so when I go to try and open synaptic manager I get this error:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

So fallowing directions, I try and use that exact command and get:

```
dpkg: requested operation requires superuser privilege
```

I continue to get the first error message when trying to install the same program with the sudo apt-get command in terminal. Anyone have any clue as to what is going on here? >.<

Did you try typing "sudo dpkg --configure -a" instead of just "dpkg --configure -a"?

---

### Post by imtheguido on 2009-01-09
Alright. I figured it out. Turns out I tried to install a sun-microsystems app earlier via terminal, but it was unable to support the proper options for me to continue, so it broke 3 packages in the process. Which was causing lots of problems. Thanks for the help! That sudo worked by the way. Man do I feel like a moron. lol.

---

### Post by Giant Speck on 2009-01-09
> **imtheguido said:**
> Alright. I figured it out. Turns out I tried to install a sun-microsystems app earlier via terminal, but it was unable to support the proper options for me to continue, so it broke 3 packages in the process. Which was causing lots of problems. Thanks for the help! That sudo worked by the way. Man do I feel like a moron. lol.

It happens to the best of us.  You're not a moron.  :)

---


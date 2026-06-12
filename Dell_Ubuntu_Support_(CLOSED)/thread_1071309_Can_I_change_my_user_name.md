---
title: "Can I change my user name?"
date: 2009-02-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JohnnyStorm on 2009-02-16
Hello everyone,
I was just wondering if ther was a way to change my user name. Thanks!

JohnnyStorm

---

### Post by sofasurfer on 2009-02-16
I haven't tried it but maybe at system>administration>users-groups.

---

### Post by sofasurfer on 2009-02-16
I just tried the method I just mentioned. It does not work.

---

### Post by dernsber on 2009-02-16
usermod -l username new_username

Won't change your home directory name, but will change your username to what you want for login purposes... oh, sudo it.

---

### Post by troublescoot on 2009-02-17
> **dernsber said:**
> usermod -l username new_username

Won't change your home directory name, but will change your username to what you want for login purposes... oh, sudo it.

Outstanding. Thank you.

Saved me about six hours of random fumbling around. :P

---


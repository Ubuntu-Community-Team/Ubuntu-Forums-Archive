---
title: "need gcc for uni work.  But it doesn't work!"
date: 2005-08-08
forum: Desktop Environments
---

### Post by snoochems on 2005-08-08
Okay.  I'm new to linux. 
I only just installed Ubuntu on my laptop because i'm studying a c/c++ programming subject at uni.

So far, i really like linux.  It's a bit of a learning curve for a 'Windows only' person though.

Anyways, i went into the 'Synaptic Package Manager' and installed everything that had 'gcc-4.0' in it's name.

I was thinking I was really clever and smart, and then when i went to test it with a 'helloworld.c' program, i got a msg saying that 'gcc: command not found'/

So, what am i doing so wrong?

---

### Post by DJ_Max on 2005-08-08
You would have been better off doing 
```
sudo apt-get install build-essential
```

Only use GCC 4 if you know what you're doing.

---

### Post by snoochems on 2005-08-09
Do i have to uninstall gcc 4?

Why wouldn't it work BTW?  is there a different command for using gcc 4?

What is it?

---


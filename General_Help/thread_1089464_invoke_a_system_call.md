---
title: "invoke a system call"
date: 2009-03-07
forum: General Help
---

### Post by jordanguyoflove on 2009-03-07
hi,

I compiled the latest version of the kernel and added a new system call to it called helloworld.
This new system call prints helloworld in a kernel log file.

Now how do I invoke the helloworld system call using C ?

Thanks.

---

### Post by jordanguyoflove on 2009-03-07
hi,

I compiled the latest version of the kernel and added a new system call to it called helloworld.
This new system call prints helloworld in a kernel log file.

Now how do I invoke the helloworld system call using C ?

Thanks.

---

### Post by Xiong Chiamiov on 2009-03-07
You did what?  Why?  If you post the specifics of what you did, and what you're trying to accomplish, then it'll be easier to help you.

Oh, and don't repost an issue because it wasn't answered in 40 minutes.

---

### Post by overdrank on 2009-03-07
Please do not create multiple threads on the same issue. Threads merged :)

---

### Post by jordanguyoflove on 2009-03-07
Well 

> #include <linux/errno.h>
#include <sys/syscall.h>
#include <linux/unistd.h>

_syscall0(int, helloworld);

main()
{
helloworld();
}

That gives me error. 

> s.c:5: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;helloworld&#8217;


I don't know how to fix it.
Please someone help me.
I've been working on this for days.

---

### Post by jordanguyoflove on 2009-03-07
bump

---


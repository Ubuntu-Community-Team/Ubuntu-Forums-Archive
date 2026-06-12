---
title: "suspend -&gt; restart"
date: 2009-03-06
forum: General Help
---

### Post by jtharp on 2009-03-06
i'm a new ubuntu user, and have encountered a problem with the suspend function.  it works perfectly, except that it resumes immediately.  it does not stay suspended, but rather wakes up instantly.  is there a "true" i need to change to a "false" somewhere, or something simple to fix this?

please respond in easy to follow instructions, as i am new.

---

### Post by LegendofTom on 2009-03-06
This is usually attributed to an external part, such as your mouse waking it up.  Maybe you can disable "mouse wake up computer".

---

### Post by jtharp on 2009-03-07
i'm sure thats not it, anybody else have an idea?

---

### Post by pavsid on 2009-03-11
Hi,

LegendofTom is probably right. I have this exact same problem and also had it in Vista until disabling "allow this device to wake the computer" for the mouse.

Unfortunately i don't know how to do the same in Ubuntu - which is what brings me here.

Can anybody shed any light?

---

### Post by pavsid on 2009-03-14
I've found the solution...

If your motherboard has jumpers for all USB hubs then you need to set them ALL to +5VSB, seems bizarre but it worked for me.

[Check this post]("http://www.gossamer-threads.com/lists/mythtv/users/316830#316830")

Hope that helps

---

### Post by Lil_Pete on 2009-03-22
I have exactly the same problem.

If I hibernate it then all is well, but if I send it to sleep then it just wakes back up again instantly. It's a tad annoying as it seems to be suspending properly as it wakes up cleanly!

Currently reading though "https://wiki.ubuntu.com/UnderstandingSuspend" in an attempt to understand how I can trace the problem...but any help such as where to look for the logs would be appreciated!

If it makes any difference my computer is;
Acer Travelmate 3200 series (laptop)
ATI 9.2 Drivers (for a Mobility 9700)
Ubuntu 8.10
(i think that's all the useful information..)

---


---
title: "The keyboard's repetitive attack !"
date: 2006-09-18
forum: Desktop Environments
---

### Post by popof on 2006-09-18
Hi !
I've a problem with my keyboard. I've installed the (last) alternate version of ubuntu... everything worked well until gdm started: when I try to insert my login, the keyboard locks: hellooooooooooooooooooooooooooooo (if I wait more than 0,5sec the last letter repeats itself 20x).](*,) 

I tried:

-> to upgrade to a newer kernel
-> to generate a new xorg.conf (via X -configure)
-> ...

What's strange is that I've not this problem in pts (when X server doesn't run).

Can you help me ?

Thankssssssssssssssssssssssssssssssss

---

### Post by Ramses de Norre on 2006-09-18
```
xset r rate 195 35
```

From the man page: > If the server supports the XFree86-Misc extension, or the XKB extension, then a parameter of 'rate' is accepted and should  be  followed by zero, one or two numeric values. The first specifies the delay before autorepeat starts and the second specifies the repeat rate. In the case that the server supports the XKB extension, the delay is the number of milliseconds before autorepeat starts, and the rate is the number of repeats per second. If the rate or delay is not given, it will be set to the default value.


Adjust the numbers to your needs, experiment a bit with it. When you've found what you need you can add it to the startup commands.

---

### Post by popof on 2006-09-18
Thank you for your reply. 
In fact, it doesn't solve the issue :(.

When I press a touch, for example s at T=0, at T=0,5 the s repeats itself:
                                                        
T=0 s        <s>   <-- I press only 1 time "a"
T=[0+;0,5]   <s>   <-- Normal behaviour (nothing happens)
T=~0,5s later   <ssssssssssssssssssssssssssssss>

Huhhhh ? That's why in general only end of words are repeatedddddddddddddddddddddd (when I stop to write))))))))))))))))))

Strange... thank you ;)

---

### Post by Ramses de Norre on 2006-09-18
Well, doesn't the behavior change when you lower the second number of the command I gave you?

Or do you mean the repeating starts when you aren't pushing the key anymore? 
That would be really odd..

---


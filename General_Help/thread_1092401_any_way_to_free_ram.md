---
title: "any way to free ram?"
date: 2009-03-10
forum: General Help
---

### Post by chriskin on 2009-03-10
intrepid seems to be using too much ram, there is always about 1gb at use, without running any really resource needy app.

can i use any application to free up ram? 

:popcorn:

---

### Post by Rallg on 2009-03-10
Hmmm... Out of 2G available on my system, Intrepid is only using 270Mb (system plus the browser). That's about normal. I do not use swap. I only have one desktop (that is, no compiz cube or anything like that).

If you go to System > Administration > System Monitor, processes tab, you can see what is using your cpu.

---

### Post by prince_niceguy on 2009-03-10
the RAM usage is divided in app usage and cache and buffers. Out of 1 GB how much is being used by app? If it is not high then I would not worry about it as cache and buffer are data read from the hard drive for faster access.

---

### Post by chriskin on 2009-03-10
ouch
vuze takes up 200mb and songbird another 100mb


yet the one i cannot understand is why nautilus takes 75mb , is it normal?

---

### Post by __Ryan__ on 2009-03-10
Linux will greedily use as much RAM as as it can. This is a good thing as it enables your applications to be as responsive as possible.

However if your system monitor shows a specific program using a lot which you don't recognize, this my be an issue.

---

### Post by chriskin on 2009-03-10
> **prince_niceguy said:**
> the RAM usage is divided in app usage and cache and buffers. Out of 1 GB how much is being used by app? If it is not high then I would not worry about it as cache and buffer are data read from the hard drive for faster access.

where am i supposed to see this ?

---

### Post by prince_niceguy on 2009-03-10
Sorry I use kubuntu, so I use ksysguard which gives all the data. For gnome I am not sure.

You can always check in terminal typing command

```
free
```

Like in my case following is the output.

             total       used       free     shared    buffers     cached
Mem:       1025008     993712      31296          0      20096     208800
-/+ buffers/cache:     764816     260192
Swap:      2931788     101804    2829984


meaning total use is 764816B (I have firefox, zimbra taking bulk of the RAM) and 260192B are free... so the sum total of these i.e. 993712 is the RAM being used, but only 764816B are being used in app and still 260MB is available for apps if required.

Hope this helps.

---

### Post by chriskin on 2009-03-10
i see..
most of it is not used, it is reserved like you said

thank you :)
:popcorn:

---


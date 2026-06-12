---
title: "Running IE6 on Ubuntu...."
date: 2009-03-10
forum: General Help
---

### Post by ragtag on 2009-03-10
I want to try to run Internet Explorer 6 (aka Internet Exploder 6) on Ubuntu. 

As for why in the world I would want to run that horrible browser?
:o
Well, I'm helping my sister with a web page, and it seems users with IE6 are having trouble with one part of the page. I need to be able to recreate the problem on my machine so that I can fix it.

Any ideas?

I have the latest version of Wine, but am not sure where you can get IE6 from.

---

### Post by Rabid Moth on 2009-03-10
I'm not entirely positive on this  but I don't think you can just install IE6 since IE is also implemented into so many other Windows components. I think the best bet would be to run a VM and go that route rather then trying to get all things that IE needs. If I'm wrong I hope someone else can help :) I know if you uninstall IE the rest of Windows is messed up.

---

### Post by BillyRose on 2009-03-10
I recommend using virtualbox or vmware to run a virtual windows instance. Of course that means you will need a license key to insall it into the VM though.

---

### Post by DeMus on 2009-03-10
> **Rabid Moth said:**
> I'm not entirely positive on this  but I don't think you can just install IE6 since IE is also implemented into so many other Windows components. I think the best bet would be to run a VM and go that route rather then trying to get all things that IE needs. If I'm wrong I hope someone else can help :) I know if you uninstall IE the rest of Windows is messed up.

MS always stated that IE is part of the OS, so I also think it will be impossible to install it on Wine. A VM would be the best solution. Or, if you still have some spare parts on your hard disk(s) try a dual boot with one the Windows versions.

---

### Post by orlox on 2009-03-10
One thing wine has been able to do for quite a while, is to run internet explorer. You can even choose from different versions to install. To check this, go to:
```

http://www.rubyrailways.com/install-internet-explorer-on-ubuntu-dapper-in-3-easy-steps/

```
It's  quite dated, but it should do the job. I used that like a year ago and it worked just right.

---

### Post by Vince4Amy on 2009-03-10
IEs4Linux will work for you: 

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by ragtag on 2009-03-10
Thanks, that worked like a charm. Got it working and fixed the bug in the page.

---

### Post by StormRoBoT2 on 2009-05-06
how about IE7 and 8? can it work too?

---


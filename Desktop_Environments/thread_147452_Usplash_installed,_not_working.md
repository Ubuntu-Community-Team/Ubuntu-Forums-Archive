---
title: "Usplash installed, not working"
date: 2006-03-20
forum: Desktop Environments
---

### Post by arthur on 2006-03-20
On my STANDARD 5.10 installation, there is no way I can make it work.
Have googled and searched everywhere in our forums, nothing :(.

Shouldn't it work out-of-the-box?

---

### Post by oakz on 2006-03-20
Yes, it should. Did you install/reinstall usplash manually or was it installed for you by default when you installed Ubuntu? Also, have you changed kernels? The usplash config is handled by your current linux kernel, not the usplash package....try reinstalling the usplash package and then reconfiguring your kernel image to pick up any usplash changes:

$ sudo dpkg-reconfigure linux-image-$(uname -r)

Hope that helps.

---

### Post by Irony on 2006-03-20
Not sure what you mean as you provide no background but have a look at this;

[http://ubuntuforums.org/showthread.php?p=837110#post837110](http://ubuntuforums.org/showthread.php?p=837110#post837110)

---

### Post by arthur on 2006-03-20
Cheers, Irony.
In fact, I always get an error message at startup, related to that annoying vesafb.ko file which is supposed NOT to exist!

I am not too keen on fiddling around to solve something which is just about "aesthetics", but I think I may give it a go (I am afraid something really important could break).

:-?

---

### Post by arthur on 2006-03-20
BRILLIANT!!
Did it on my previous kernel, and it worked.
So applied it to the latest one, sure it will here too.

Thanks :D

---


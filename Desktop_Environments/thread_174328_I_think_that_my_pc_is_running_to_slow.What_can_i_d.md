---
title: "I think that my pc is running to slow.What can i do?"
date: 2006-05-11
forum: Desktop Environments
---

### Post by zigoto on 2006-05-11
Hi, iam newbie on linux(ubuntu). I am using ubuntu 5.10, i think that my pc is running to slow, i have a better performance on windows xp(when it is fresh installed). I know few things about linux, but not much. what can i do to hava a better perfom. By the way, i have laptop, P4 3.0 G with 512 Ram and a ATI radeon 9000, with 64 mb...
It is a acer aspire 1605 LM!

If someone know i to have a better perform, please tell me


Regards

---

### Post by MichaelZ on 2006-05-11
Hello,

May be this thread could be of some interest:

[http://www.ubuntuforums.org/showthread.php?t=74197&highlight=prelink]("http://www.ubuntuforums.org/showthread.php?t=74197&highlight=prelink")

Best wishes,
Michael

---

### Post by louis_nichols on 2006-05-11
There is no simple answer to this question, I believe. It might be things like: applications that have running daemons (e.g. servers) or resource-hungry desklets (gdesklets are known to eat a computer alive :) ) or not having installed the proprietary drivers of the video card, or even not having enabled dma for the cd drive (to check, issue in terminal the command **hdparm /dev/hdc**).

Do you think any of this might be your case?

Also, run in terminal the command **top** and see what processes are at the top, using many CPU cycles.

---

### Post by K.Mandla on 2006-05-11
I agree; there are a lot of things that could be going wrong, but a computer with those specs should fly. I would suspect video drivers first, but that's only one of a dozen things that might need tweaking.

I assume you're using Gnome? You could install Xubuntu over top of that, and perhaps that might speed things up a little.

---

### Post by zigoto on 2006-05-11
you have reason, can be a lot of things, i dont think that is my video drivers, because i have compile the kernel to install my especific video drive, i dont have
gdesklet installed...

thanks for the help

---

### Post by zigoto on 2006-05-11
I know what is "eating" all my memory, i have installed a theme to be like a mac, and  when i open firefox i only have 10 mb free of ram, and the pc run slow, i uninstall and now it is run great!!

Thanks
Regards

---


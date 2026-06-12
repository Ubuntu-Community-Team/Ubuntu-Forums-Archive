---
title: "Windows apps making GRUB 2 unbootable"
date: 2011-01-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by stanz on 2011-01-18
I found this information the other day--and thought it needed here.
This answers all the other threads, concerning Dell/Hp & m$ - messing with our *buntu installs.
Offered is way to prove it, and pitch in to hopefully stop;

> ...where we need to defend ourselves against the predatory practices of  some companies making us look bad: a relatively small number of people  do enough detective work to realize that it's the fault of a particular  Windows application, but many more simply blame our operating system  because it won't start any more.{above quote taken from the link below}
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian]("http://www.chiark.greenend.org.uk/ucgi/%7Ecjwatson/blosxom/debian")

I hope this helps others...
I simply wiped my disk to rid myself of the issue...if you need the dual boot-this issue needs to end!

;)

---

### Post by JRV on 2011-01-21
I had this problem after installing Ubuntu on a friends Dell computer.  

To fix it I downloaded the Rescatux disk from this site: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Boot this live CD and follow the prompts.

This is the easiest way I know of to fix Grub2.

Then I locked out Windows so it can't happen again.  
Turn off the executable flag for /etc/grub.d/30_os-prober.
Then do a "sudo update-grub".

---


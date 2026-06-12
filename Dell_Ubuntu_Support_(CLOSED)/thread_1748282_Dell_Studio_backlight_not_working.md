---
title: "Dell Studio backlight not working"
date: 2011-05-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mattrob33 on 2011-05-03
I had this problem a few months ago and installed [Kamal Mostafa's patch]("https://launchpad.net/%7Ekamalmostafa/+archive/linux-kamal-mjgbacklight") and everything worked. I just had to re-install my operating system (to 10.10), and I am trying to install the patch again but cannot get it working.

I added the PPA ppa:kamalmostafa/linux-kamal-mjgbacklight and updated. The Ubuntu Software Center shows the repository and shows that everything has been installed. However, there is no option to boot from this kernel and /sys/class/backlight does not show intel_backlight.

Any suggestions? Thanks in advance.

---

### Post by mattrob33 on 2011-05-04
Ok I just installed a kernel update for the patch and after installing it, everything is working fine -- I didn't have to do anything to fix it.

---


---
title: "change runlevels?"
date: 2006-08-31
forum: Desktop Environments
---

### Post by millerdc on 2006-08-31
I'm use to red hat/fedora and I'm having problems adjusting to how Ubuntu works. I went to change my inittab file so it is set to init 3. However it was set to init 2 and not 5. Under RH/fedora by default it is set to init 5 and if you change it to init 3 it wont start X. How do I do the same thing under ubuntu? I can't even do an init 3 in the terminal like I can with RH/Fedora.

---

### Post by meng on 2006-08-31
One way is to have an extra grub option, just adding 3 onto the end of the kernel options line. However, be aware that by default, runlevels 2-5 are identical, and you will have to change your /etc/rcX.d manually, unless you use something like sysv-rc-conf (which I don't find to be comprehensive enough).

---

### Post by WelshChris on 2006-09-01
Like the OP, I'm relatively new to Ubuntu having used various others - Slackware, RH, Mandrake.  Why on earth are all the runlevels in Ubuntu identical?  Surely someone realised there may be a need for a user to boot without gdm?

I'm probably old fashioned, but if I wanted a console boot I used to change inittab's default runlevel to 3.  Simple as that.

<Sigh>

---

### Post by meng on 2006-09-01
I think your point is excellent. Mind you, having an extra grub option seems to me the best option in any case. Don't forget the word "Ubuntu" is derived from the ancient African word for "can't configure Debian".

---


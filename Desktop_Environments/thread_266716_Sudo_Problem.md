---
title: "Sudo Problem"
date: 2006-09-27
forum: Desktop Environments
---

### Post by damn_fw on 2006-09-27
Hi everyone,

I´m having a little problem with sudo, when I execute a "sudo make"
he asks for my password and them it starts do compile, but the $PATH disappears, and some libraries cannot be found.
I tried a sudo -i and i exported the PATH but, it still cannot find the libraries. What am I doing wrong?

Tks

---

### Post by wieman01 on 2006-09-27
You need to post the output, otherwise it will be very hard to help you. When you do "sudo make", try this:
> sudo make >> [COLOR="Red"]my_log_file.txt[/COLOR]
And then upload [COLOR="Red"]my_log_file.txt[/COLOR] so that we can have a glance at it.

---


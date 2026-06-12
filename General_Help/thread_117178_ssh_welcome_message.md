---
title: "ssh welcome message"
date: 2006-01-14
forum: General Help
---

### Post by 5ketcher on 2006-01-14
hi @ all,

does anybody know how to change the ssh welcome message?

[I]The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.[/I]

thx, jan

---

### Post by adwait on 2006-01-14
I think you can edit /etc/issue.net for that.

---

### Post by 5ketcher on 2006-01-14
no that's not the file I'm searching for. I'd like to change the text written in the upper post.

---

### Post by matthew on 2006-01-14
```
sudo gedit /etc/motd
```Delete what is there and type in whatever you want.

EDIT: motd = message of the day. Changing this will change the text displayed whenever you login to this machine.

---

### Post by 5ketcher on 2006-01-14
thx matthew that's what I'm searching for :D

---


---
title: "Firestarter wont startup"
date: 2006-01-27
forum: Desktop Environments
---

### Post by shade11 on 2006-01-27
I have tried and tried to get Firestarter to run on startup but no luck. I have followed the instructions but it doesnt help.

Here is my /etc/sudoers file that contains the code I put in.
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL

username ALL= NOPASSWD: /usr/sbin/firestarter
username ALL= NOPASSWD: /usr/sbin/simplewifi

```

And in sessions I added sudo firestarter --start-hidden
at order number 20.

Please tell me what to do.

(Yes I am using initNG if that has anything to do with it, but it wouldnt startup even before I used initNG.)

---

### Post by byen on 2006-01-27
> username ALL= NOPASSWD: /usr/sbin/firestarter
username ALL= NOPASSWD: /usr/sbin/simplewifi

Dont you have to replace the "username" with the actual user name? ([linky]("http://ubuntuforums.org/showthread.php?p=663298#post663298"))
Well..thats what I did..and it seems to work fine.. See if it helps.Goodluck!

---

### Post by shade11 on 2006-01-27
Yes, thanks. It works now. I was wondering about simplewifi but now it is fixed.

Thanks.

---

### Post by byen on 2006-01-28
Cool man.. glad I could help!

---

### Post by shade11 on 2006-01-28
I also changed the order before you replied to 50. It still works, but will there be any conflictions?

---

### Post by byen on 2006-01-28
I dont think so.. but when I first read a how-to about firestarter...it mentioned order 20 so that firestarter starts off much earlier than other programs which access the web, thus running the firewall before others (with a standard 50). Im not sure if this is right..but it made sense... if someone knows the right answer to this.. I'd be glad to learn too.. :-)

---

### Post by shade11 on 2006-01-28
so if I change it to 20 it will still startup right?

---

### Post by byen on 2006-01-28
yes.. there shouldnt be a problem if you change the order to 20. I can say that cuz I once changed the order to 50 for a couple of days and changed it back to 20 to see what difference it made (i saw none). But it wouldnt do any damage to try and see it yourself ;-)

---

### Post by shade11 on 2006-01-28
I changed it to 20. It still works. So thanks.:)

---


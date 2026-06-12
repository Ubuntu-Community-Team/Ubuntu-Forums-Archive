---
title: "Sudoer permissions"
date: 2008-12-03
forum: General Help
---

### Post by kalamityjane on 2008-12-03
Hello. Today I attempted to setup a FTP server. I port forwarded but then I decided to back out after I set everything up. After I reset my router my friends were complaining that my website was offline. So, my first brilliant idea was to restart my computer. Everything booted up normally. Then more problems started appearing. ```
sudo /etc/rc.d/init.d/httpd restart
``` returned ```
kalamity is not in the sudoers file.  This incident will be reported.

``` Can't use add/remove either. I have searched the ubuntu forums for a solution but I have yet to see a solution. Ubuntu 8.04 by the way...

I also lost 4 GB:(

---

### Post by Nepherte on 2008-12-03
You will have to put yourself in the sudoers file. Boot in the recovery mode. This will leave you with a terminal as root. Type
```
visudo
```
and put
```

yourusername     ALL=(ALL) ALL

```
in it, where yourusername is replaced with your actual user name. the visudo command will open /etc/sudoers with the command line editor vi, which might be a little difficult to use. Instead you could use nano:
```

EDITOR=nano visudo

```

Another possibility is to add yourself to the admin group (I believe that's what the group is called, if admin is listed in the file visudo opens it's ok):
```

gpasswd -a yourusername admin

```

---

### Post by kalamityjane on 2008-12-03
well that helped me with one of my problems. However I still can't use synaptic update manager, add/remove, and every time I try to unlock network configuration I get this message. 

"could not authenticate"

---

### Post by sisco311 on 2008-12-03
open a terminal and post the output of:
```
id -G
```
and
```
sudo cat /etc/sudoers
```

---

### Post by kalamityjane on 2008-12-03
I'll just reinstall

---

### Post by mkvnmtr on 2008-12-03
They say you can fix anything that could be wrong and we really should learn how. But I can reinstall and be back up in about one hour. Sometimes it takes me two days to fix something I have messed up. I must have reinstalled 30 times. If I am in a hurry it's a lot faster.

---


---
title: "scim process started twice by difference user"
date: 2005-05-27
forum: Desktop Environments
---

### Post by yccheok on 2005-05-27
hello, i just manage to install hoary. it works great and i was quite happy with it. many thanks to the ubuntu team!

i have some problem with the scim. i realize that there is two scim keyboard icons in my taskbar. when i perform 

[I]yccheok@ubuntu:~$ ps -ef | grep scim
yccheok   7613     1  0 01:37 ?        00:00:00 /usr/lib/scim-1.0/scim-launcher-daemon simple all socket 0 none none --no-stay
yccheok   7640     1  0 01:38 ?        00:00:00 /usr/lib/scim-1.0/scim-panel-gtk -c socket -o none -d --no-stay
root      7983     1  0 01:43 ?        00:00:00 /usr/lib/scim-1.0/scim-launcher-daemon simple all socket 0 none none --no-stay
root      8033     1  0 01:46 ?        00:00:00 /usr/lib/scim-1.0/scim-panel-gtk -c socket -o none -d --no-stay
yccheok   8264  8060  0 02:01 pts/0    00:00:00 grep scim[/I]

I realize that the same scim process are started twice by difference users.

1. may i know which config file starts the scim process automaticaly when i log in? where i should start look into to solve this problem? 

thanks a lot

&#25105;&#21487;&#20197;&#36755;&#20837;&#21326;&#25991;&#20102;

cheok

---

### Post by adrian440 on 2005-06-05
I notice this only when I start an administration-type application, like synaptic. Then I get two scims, one for root, and one for me. It disappears after synaptic is finished though. 

Perhaps your session includes some gtk application that is being run as root.

---


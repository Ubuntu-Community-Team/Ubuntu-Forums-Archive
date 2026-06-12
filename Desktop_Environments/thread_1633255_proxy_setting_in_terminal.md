---
title: "proxy setting in terminal"
date: 2010-11-29
forum: Desktop Environments
---

### Post by alokmahor on 2010-11-29
Dear all, 
 I am using Ubuntu 10.04, in the earlier version I just  need to enter <export http_proxy="[http://10.10.78.22:3128]("http://www.google.com/url?sa=D&q=http://10.10.78.22:3128&usg=AFQjCNFOYaecrQ-ZZLpVTx8funiS--W6Hg")">  and <export ftp_proxy="[http://10.10.78.22:3128]("http://www.google.com/url?sa=D&q=http://10.10.78.22:3128&usg=AFQjCNFOYaecrQ-ZZLpVTx8funiS--W6Hg")">  to set the proxy in terminal. but in the 10.04 and 10.10 its not  working. I also set system wide proxy in preferences still I am not  getting proxy set in terminal. so I am unable to use wget and other commands. how are you guys getting proxy set in terminal in 10.04 and 10.10?

---

### Post by nilarimogard on 2010-11-29
It works just fine in both Ubuntu 10.04 and 10.10. So check your proxy...

---

### Post by alokmahor on 2010-11-29
that was bug i tihnk
[https://bugs.launchpad.net/ubuntu/+source/wget/+bug/232469](https://bugs.launchpad.net/ubuntu/+source/wget/+bug/232469)

and [https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/534225](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/534225) shows that this has been fixed.

---


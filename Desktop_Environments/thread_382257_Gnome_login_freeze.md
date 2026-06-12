---
title: "Gnome login freeze"
date: 2007-03-11
forum: Desktop Environments
---

### Post by Thudy on 2007-03-11
When I typed "startx", it wait about 5-10 min to let me login and there is a message box said

" There was an error starting the GNOME Settings Daemon  ..................."

Then I tried to use the administrator tools, some of these tools take so long to response. Especially the time and date adjustment, users setting etc. 

I saw some people have the same problem as me, any suggestions?

Thanks

---

### Post by Thudy on 2007-03-11
I modified the /etc/network/interface  to enable lo, then everything works fine now.

A couple of days ago the university domain shut down, I failed to connect  to internet.
Then I delete lo and disabled search domain "xxx.edu".

I think there are many administrator tools use "lo" to connect to localhost. When gnome start, it uses administration tools to do some initial jobs. Without "lo", may it use "eth0"?
So it is slow and freeze for a while.

---


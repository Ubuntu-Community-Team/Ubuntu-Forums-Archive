---
title: "proftpd"
date: 2009-03-04
forum: General Help
---

### Post by slouchez on 2009-03-04
Hello I installed proftpd and all looks ok, to the point where if looks like it starts/ stops as it should - BUT
[1] when I try to log in I get
/ # ftp 192.168.10.2                                                            
Connected to 192.168.10.2.                                                      
421 Service not available, remote server has closed connection                  
ftp> 
as it it isn't running

[2] and I can't see it running on my host:
sylvain@sylvain-laptop:/etc/proftpd$ sudo /etc/init.d/proftpd stop
 * Stopping ftp server proftpd                                           [ OK ] 
sylvain@sylvain-laptop:/etc/proftpd$ ps ax
=====> saved to "before"
sylvain@sylvain-laptop:/etc/proftpd$ sudo /etc/init.d/proftpd start
 * Starting ftp server proftpd                                                   - warning: the DisplayFirstChdir directive is deprecated and will be removed in a future release.  Please use the DisplayChdir directive.
                                                                         [ OK ]
sylvain@sylvain-laptop:/etc/proftpd$ ps ax
=====> saved to "after"
sylvain@sylvain-laptop:/etc/proftpd$ cd /home/sylvain/Desktop/
sylvain@sylvain-laptop:~/Desktop$ diff before after
96c96
<  6018 tty7     Ss+    1:02 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xaut
---
>  6018 tty7     Rs+    1:06 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xaut
111c111
<  6333 ?        Sl     0:05 nautilus --no-default-window --sm-client-id default2
---
>  6333 ?        Sl     0:06 nautilus --no-default-window --sm-client-id default2
136c136
<  6748 ?        Sl     0:06 gnome-terminal
---
>  6748 ?        Sl     0:07 gnome-terminal
139c139
<  6802 ?        Sl     1:24 /usr/lib/firefox-3.0b5/firefox
---
>  6802 ?        Sl     1:26 /usr/lib/firefox-3.0b5/firefox
143c143,144
<  9020 pts/0    R+     0:00 ps ax
---
>  9039 ?        S      0:01 gedit file:///home/sylvain/Desktop/new%20file
>  9106 pts/0    R+     0:00 ps ax
sylvain@sylvain-laptop:~/Desktop$ 
NO MEANINGFUL DIFFRENCE

It seems basic to me - so there's a fundamental misunderstanding on my part or ????

Help. All I want is a simple server for lab use only. :(
grrrr.

---


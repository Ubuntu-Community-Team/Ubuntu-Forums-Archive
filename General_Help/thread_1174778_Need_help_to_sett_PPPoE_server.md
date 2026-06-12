---
title: "Need help to sett PPPoE server"
date: 2009-05-31
forum: General Help
---

### Post by Romala on 2009-05-31
Hello!
Could anybody know the best way how to make *pppoe-server* on a startup?
The command
```
$ sudo pppoe-server -I eth1 
```
works only before a reload.
And what does ```
 -k 
```option mean
  > -k     The  -k  option  tells  the  server  to use kernel-mode PPPoE on
               Linux.  This option is available only on Linux kernels 2.4.0 and
               later,  and  only  if the server was built with kernel-mode sup&#8208;
               port.

Thanks

---

### Post by Romala on 2009-06-07
You may to use a script
> #!/bin/sh
sudo pppoe-server -I eth1 .....
exit 0

*/etc/network/if-pre-p.d/pppoesstart*
but it should
> sudo chmod +x /etc/network/if-pre-p.d/pppoesstart
before.
Thank you

---


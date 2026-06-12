---
title: "XDMCP only starts after logging in locally"
date: 2010-06-17
forum: Desktop Environments
---

### Post by lvnatic on 2010-06-17
Hello, 

I installed Lucid Lynx on a desktop with the intention of primarily accessing it remotely. I enabled XDMCP by editing  /etc/gdm/custom.conf file and setting Enable=true under the XDMCP section. XDMCP works, but only after logging in to the machine directly first. When the machine boots  i can run netstat and see that nothing is listening on the XDMCP port until i log into it. Does anyone know of a way that I can get XDMCP to start at boot, rather than after I log in?

Thanks!

---


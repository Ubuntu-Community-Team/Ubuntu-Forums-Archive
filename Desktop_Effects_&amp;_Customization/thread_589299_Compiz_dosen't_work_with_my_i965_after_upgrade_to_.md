---
title: "Compiz dosen't work with my i965 after upgrade to gutsy"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by Damwid on 2007-10-24
Compiz doesn't work any more after upgrading from feisty to gutsy. My video card is intel i965,  neither 'i810' nor 'intel' driver can make compiz work, following is the output of compiz:
```
> compiz --replace
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2992' found 
aborting and using fallback: /usr/bin/metacity
```
and glxinfo output:
```

>glxinfo | grep direct
direct rendering: Yes

```

Can any one help me? My xorg.conf and Xorg.0.log is attached.

---


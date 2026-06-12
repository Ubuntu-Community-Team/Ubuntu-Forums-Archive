---
title: "help w/ xgl / aiglx on ubuntu 7.10"
date: 2007-11-06
forum: Desktop Environments
---

### Post by pcstalljr on 2007-11-06
ok i just installed ubuntu 7.10 about a week ago but i cant get my compiz fusion to work...... hers what i get when i try " compiz --replace "  

pc@pcs-pc-pcs-comp:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

ok now i know i need xgl or aiglx but i dont know how to install it. ive looked at guide and thay dont tell me how to install xgl on 7.10 gusty just 7.04 and that doesnt help me........if it helps......im running this on my vmware cause i do not have a back up disk for my windows xp and i cant risk loseing my os.......please help if you can.....thanks in advance!!

---

### Post by bingoUV on 2007-11-06
```

sudo apt-get install xserver-xgl

```

Many people report slow performance issues with xgl, so beware. Since ubuntu 7.10 could not enable effects for you, this suggests there are some problems with your graphics card. They could be minor, but ubuntu plays safe and does not enable effects. Which is your graphics card ?

---


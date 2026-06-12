---
title: "Seamless rdesktop not working"
date: 2008-12-03
forum: General Help
---

### Post by dignus on 2008-12-03
Hi there,

I've installed Windows XP under VMWare server on my Intrepid workstation. All works well, I can rdesktop to it with no problems. Now I want seamless integration. Followed the steps like I did with other installations, but now when I rdesktop with seamless options I get my normal fat rdp session:

```
user@host:~$ rdesktop -A -s 'c:\seamless\seamlessrdpshell.exe c:\windows\explorer.exe' pc3982vm -u user -p password
Autoselected keyboard map en-us
WARNING: Remote desktop does not support colour depth 24; falling back to 16
```

My WS is Ubuntu Intrepid 32 bits, target OS is Windows XP Prof SP 3. I verified the location of seamlessrdpshell.exe. When I execute the path in windows explorer, it confirms it's there (with an error of course). 

Any ideas?

---

### Post by lusmo on 2009-06-04
I have the same problem. Any idea?

---


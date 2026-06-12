---
title: "Can Ubuntu connect remotely to windows xp?"
date: 2009-02-18
forum: General Help
---

### Post by Solorflare on 2009-02-18
Is there a way to connect to a windows xp computer via ubuntu, so I can fix a persons computer running windows xp via a remote assistance request?

---

### Post by whoop on 2009-02-18
vnc : [http://2.bp.blogspot.com/_IucfCgVx7l4/Rrm_QFym__I/AAAAAAAAAV4/THWUtLvmJxk/s320/VNC02.JPG](http://2.bp.blogspot.com/_IucfCgVx7l4/Rrm_QFym__I/AAAAAAAAAV4/THWUtLvmJxk/s320/VNC02.JPG)
Note that you need to install a vnc server on windows and a client on linux. To be secure you need to tunnel it through ssh: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by cmnorton on 2009-02-18
Sure you can. Use terminal server client, located under Applications --> Internet .

---

### Post by Solorflare on 2009-02-18
> **whoop said:**
> vnc : [http://2.bp.blogspot.com/_IucfCgVx7l4/Rrm_QFym__I/AAAAAAAAAV4/THWUtLvmJxk/s320/VNC02.JPG](http://2.bp.blogspot.com/_IucfCgVx7l4/Rrm_QFym__I/AAAAAAAAAV4/THWUtLvmJxk/s320/VNC02.JPG)
Note that you need to install a vnc server on windows and a client on linux. To be secure you need to tunnel it through ssh: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

Cant do that. the computer that I have to connect to is too far away for me to go and install it and the owner doesnt know much about computers and is scared to install programs on the computer themselves.

---

### Post by Solorflare on 2009-02-18
> **cmnorton said:**
> Sure you can. Use terminal server client, located under Applications --> Internet .

Thank you, will try that, I just have to get them to send me an email with a remote assistance request right?

---

### Post by cmnorton on 2009-02-19
> **Solorflare said:**
> Cant do that. the computer that I have to connect to is too far away for me to go and install it and the owner doesnt know much about computers and is scared to install programs on the computer themselves.

You turn on a service on the XP/Windows side. Without that, I believe there is no other way you can help them, because services like Telnet are turned off by default. You may have to walk someone through turning the services on.

---


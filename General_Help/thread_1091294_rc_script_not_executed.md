---
title: "rc script not executed"
date: 2009-03-09
forum: General Help
---

### Post by Tex-Twil on 2009-03-09
Hi,
I want to run a simple script which basically sets some iptables rules at boot time. I've put the script in /etc/init.d/myiptable and created run levels scripts:

```

/etc/rc3.d/S21myip -> /etc/init.d/myiptables
/etc/rc4.d/S21myip -> /etc/init.d/myiptables
/etc/rc5.d/S21myip -> /etc/init.d/myiptables

```

but the script is just not executed.

what am I doing wrong ?

Thanks,
Tex

---

### Post by Tex-Twil on 2009-03-09
hmm nevermind. I put my script in /etc/network/interfaces in the "post-up" section.


Tex

---


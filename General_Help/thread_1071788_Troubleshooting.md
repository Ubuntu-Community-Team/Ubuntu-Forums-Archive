---
title: "Troubleshooting"
date: 2009-02-16
forum: General Help
---

### Post by ForMar on 2009-02-16
I have recently started using ubuntu and not to long ago I started experience numerous program hangs and extremely slow boot times. I have no idea what is wrong and unfortunately I'm not even sure where to start. So I was wondering if someone could either point me in the right direction or tell me how to troubleshoot in ubuntu. More specifically tell me what logs have what, and what I should be looking for. I am familiar to the windows style where they have all the logs together and I can see exactly what crashed and why. I already know that most logs are in the /var/logs. But when looking at the all the logs I'm just not sure where to begin.

 Thanks for your time and help!

---

### Post by sumguy231 on 2009-02-16
The logs most relevant to your problem are probably /var/log/syslog, /var/log/messages, and /var/log/kern.log

You can then search the logs for 'error', 'warning', and the like. Good luck.

---

### Post by ForMar on 2009-02-16
Thanks then my last questions is what exactly is the command to pipe through them to find a certain text and show you said line. I know its possible but I forget the exact command. Thanks for any help

---

### Post by sumguy231 on 2009-02-16
Well, you can just use the log viewer in System -> Administration -> System Log and hit Ctrl+F to filter/find, but if you want to use the terminal use 
```
less <name of logfile>
``` and then hit '/' to search within it.

---

### Post by oldos2er on 2009-02-16
You can also start reading
```
dmesg
```
from the bottom up.
 Other than that, I'd run fsck and memtest too.

---

### Post by Phlee on 2009-02-16
man grep;)

---

### Post by linux_tech on 2009-02-16
any errors in ```
cat /var/log/messages
```

---


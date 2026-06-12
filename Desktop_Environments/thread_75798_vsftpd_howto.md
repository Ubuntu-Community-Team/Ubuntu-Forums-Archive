---
title: "vsftpd howto?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by sickdude on 2005-10-14
i only used proftp and that was easy to configure. but i wanted to switch to vsftp but i really dont have a idea to configure this one.
 
so is there somebody that can help me out on this little request?

---

### Post by sickdude on 2005-10-14
crap didnt see this thread

sorry

[http://ubuntuforums.org/showthread.php?t=1371&highlight=vsftp](http://ubuntuforums.org/showthread.php?t=1371&highlight=vsftp)

:$

---

### Post by sickdude on 2005-10-14
ok i looked in the how to's but these are all crappy

i cant seem to get vsftpd working right

is there anybody who has some tips or maybe some conf files i can use?

---

### Post by hil on 2005-11-21
I followed the instructions from [http://www.siliconvalleyccie.com/lin...ftp-server.htm]("http://www.siliconvalleyccie.com/lin...ftp-server.htm")
I modified /etc/vsftpd.conf and removed the comment symbol (#) before the local_enable instruction. I sudo /etc/init.d/vsftpd restart. Then I could login as a normal user.

---


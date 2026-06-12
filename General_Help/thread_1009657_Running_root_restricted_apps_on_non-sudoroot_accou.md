---
title: "Running root restricted apps on non-sudo/root account."
date: 2008-12-12
forum: General Help
---

### Post by aNaRcHiSt on 2008-12-12
Hi there.

Was wondering if anyone could advise how I can allow users to run root specific applications without adding them as a sudoer.

I'm curious as to whether this is possible in general however in specific I'm trying to allow tcptraceroute to be used by normal users on my box.

```

josh@punisher:~$ tcptraceroute google.com
The specified type of tracerouting is allowed for superuser only

```

Thanks in advance.

---

### Post by ToddAndMargo on 2008-12-12
kdesudo -n -u root -c Your_command_here

su root -c Your_command here

"Your_command_here" can be enclosed in quotes and contain
a series of commands separated by semicolons ";".

HTH,
-T

---

### Post by aNaRcHiSt on 2008-12-15
ToddAndMargo. Thanks for your reply, but doing it like that would still require my users to be sudoers, or know the root password.

Is there any way I can allow a non-root/su user to run applications that usually require root privilidges in order to perform correctly (eg, tcptraceroute and certain nmap modes) without adding them as a sudoer?

---

### Post by ToddAndMargo on 2008-12-15
> **aNaRcHiSt said:**
> ToddAndMargo. Thanks for your reply, but doing it like that would still require my users to be sudoers, or know the root password.

Is there any way I can allow a non-root/su user to run applications that usually require root privilidges in order to perform correctly (eg, tcptraceroute and certain nmap modes) without adding them as a sudoer?

Sorry for the misunderstanding.  The answer to your question is "yes".
I am not in Ubunto so I can not verify the following, but in CentOS 5.2,
you would do it by making an entry in your "/etc/sudoers" file.  Do
this with "visudo" (other text editors work too, you can ignore the
warnings in the manual page).   What to do is covered in your 
"man sudoers" manual page.  Here are some examples from 
my /etc/sudoers:

```

%users  ALL=NOPASSWD:/sbin/shutdown
%users  ALL=NOPASSWD:/sbin/halt
%users  ALL=NOPASSWD:/sbin/reboot
%users  ALL=NOPASSWD:/sbin/poweroff
%users  ALL=NOPASSWD:/sbin/ifup eth1
%users  ALL=NOPASSWD:/sbin/ifdown eth1
%users  ALL=NOPASSWD:/usr/bin/system-config-printer
%users  ALL=NOPASSWD:/usr/bin/xterm -T BlueXTerm -n BlueXTerm -fn 12x24\
-bg white -fg darkblue -e /root/megamgr

```

HTH,
-T

---

### Post by aNaRcHiSt on 2008-12-16
That's exactly what I was after!

Thank you very much.
Happy Holidays.

---


---
title: "WPA_supplicant error message"
date: 2006-06-01
forum: Desktop Environments
---

### Post by Vinze on 2006-06-01
I get this error message: > ~$ sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dhostap -w
ioctl[SIOCSIWPMKSA]: Operation not supported
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to initiate AP scan.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to initiate AP scan.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to initiate AP scan.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to initiate AP scan.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to initiate AP scan.
<!-- Stopped with Ctrl+C -->
$

Any ideas what the problem might be? Please, I want internet so badly ;) 

Thanks in advance.

---

### Post by Vinze on 2006-06-05
Really, can't anyone who's online now help me? I'm really, reallly desparate, you don't know what it is not to have internet :cry:

---

### Post by codypumper on 2006-06-05
I wish I could help. If you use wireless you can try this: [http://ubuntuforums.org/showthread.php?t=31418&highlight=wpa]("http://ubuntuforums.org/showthread.php?t=31418&highlight=wpa")
Otherwise, I would look into updating your drivers if possible.

---

### Post by wrobaman on 2006-09-15
Hello!

I had the same problem some days before, and I got the same messages.

Please make sure that you have entered correctly the interface after the -i operator.

I had to set eth0 instead of eth1, and the problem was fixed.

I hope you get connection to Internet now.

Best regards!

---


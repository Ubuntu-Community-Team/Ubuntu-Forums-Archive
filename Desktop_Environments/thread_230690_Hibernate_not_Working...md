---
title: "Hibernate not Working.."
date: 2006-08-06
forum: Desktop Environments
---

### Post by avender on 2006-08-06
Hi..

Recently I upgraded the Ram from 256 Mb to 768 Mb. I also changed my Swap space from 512 mb to 940 mb.

Since then the hibernation is not working at all. When I click on that button my computer monitor turns black after few seconds every thing is restored.

Here are the command line output of hibernate.sh

```

 free
             total       used       free     shared    buffers     cached
Mem:        766016     387084     378932          0      12364     141856
-/+ buffers/cache:     232864     533152
Swap:       939792     142400     797392
raghu@ubuntu:~$ sudo -s
root@ubuntu:~# cat /sys/power/image_size
524288000
root@ubuntu:~# echo 939792 > /sys/power/image_size
root@ubuntu:~# exit
exit
raghu@ubuntu:~$ sudo /etc/acpi/hibernate.sh
 * Shutting down ALSA...                                                 [ ok ]
/etc/acpi/hibernate.sh: line 28: echo: write error: No such device
disabled, not active [unchanged].
/etc/acpi/resume.d/17-video-restore.sh: line 5: /var/lib/acpi-support/vbestate: No such file or directory
ifup: interface eth0 already configured
 * Setting up ALSA...                                                    [ ok ]
grep: /proc/acpi/fan/*/state: No such file or directory

```

Please help me...

---

### Post by kmi on 2006-08-24
Well, old post but... : your SWAP space has to be 1.5 to 2x bigger than your actual RAM.

I would bet you just have to make it bigger and everything shoul be ok.

---


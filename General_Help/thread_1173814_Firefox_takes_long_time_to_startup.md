---
title: "Firefox takes long time to startup"
date: 2009-05-30
forum: General Help
---

### Post by cupabj on 2009-05-30
I have installed Ubuntu (Linux 2.6.24-23) on my HP dv6000 laptop and I am using Firefox ver. 3.0.9. On many occasions, Firefox takes very long to startup. I checked that the Firefox process is running, however it never opens any window. After a random interval that lasts from 1 to 15 minutes, the initial Firefox window is displayed on the screen. Once the initial window is displayed, Firefox functions normally. Killing and restarting Firefox doesn't help as the new Firefox process too enters the "wait mode". Starting multiple instances of Firefox doesn't help either. I used strace to check what the Firefox process is up to. Output from starce is provided at the end of this email. I have also noticed that disconnecting from my wireless internet router sometimes helps Firefox to display the startup window. I would greatly appreciate any help in solving this problem. Output from strace:

strace -p 6196
Process 6196 attached - interrupt to quit
restart_syscall(<... resuming interrupted call ...>) = 1
read(18, "\372", 1)                     = 1
gettimeofday({1243399155, 44988}, NULL) = 0
select(4, [3], [3], NULL, NULL)         = 1 (out [3])
writev(3, [{"\205\1\2\0\246\1\0\0", 8}], 1) = 8
select(4, [3], [], NULL, NULL)          = 1 (in [3])
read(3, "\1\3\n\5\0\0\0\0\245\1\0\0\0\0\0\0009\0\0\0\0\0\0\0\0\236"..., 4096) = 32
read(3, 0x8074b54, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1243399155, 46292}, NULL) = 0
gettimeofday({1243399155, 46437}, NULL) = 0
gettimeofday({1243399155, 46598}, NULL) = 0
read(3, 0x8074b54, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=23, events=POLLIN}, {fd=18, events=POLLIN}], 10, 0) = 0
gettimeofday({1243399155, 47215}, NULL) = 0
read(3, 0x8074b54, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=23, events=POLLIN}, {fd=18, events=POLLIN, revents=POLLIN}], 10, -1) = 1
read(18, "\372", 1)                     = 1
gettimeofday({1243399155, 238160}, NULL) = 0
gettimeofday({1243399155, 238423}, NULL) = 0
gettimeofday({1243399155, 238565}, NULL) = 0
gettimeofday({1243399155, 238722}, NULL) = 0
read(3, 0x8074b54, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=23, events=POLLIN}, {fd=18, events=POLLIN}], 10, 0) = 0
gettimeofday({1243399155, 239257}, NULL) = 0
read(3, 0x8074b54, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=23, events=POLLIN}, {fd=18, events=POLLIN, revents=POLLIN}], 10, -1) = 1
read(18, "\372", 1)                     = 1
gettimeofday({1243399156, 77027}, NULL) = 0
write(16, "8", 1)                       = 1
futex(0x8108be8, 0x81 /* FUTEX_??? */, 1) = 1
gettimeofday({1243399156, 77309}, NULL) = 0
gettimeofday({1243399156, 77363}, NULL) = 0
gettimeofday({1243399156, 77421}, NULL) = 0
read(3, 0x8074b54, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=23, events=POLLIN}, {fd=18, events=POLLIN}], 10, 0) = 0
gettimeofday({1243399156, 77704}, NULL) = 0
read(3, 0x8074b54, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=23, events=POLLIN}, {fd=18, events=POLLIN, revents=POLLIN}], 10, -1) = 1
read(18, "\372", 1)                     = 1
gettimeofday({1243399160, 47130}, NULL) = 0
select(4, [3], [3], NULL, NULL)         = 1 (out [3])
writev(3, [{"\205\1\2\0\246\1\0\0", 8}], 1) = 8
select(4, [3], [], NULL, NULL)          = 1 (in [3])
read(3, "\1\3\v\5\0\0\0\0\245\1\0\0\0\0\0\0\22\23\0\0\0\0\0\0\0"..., 4096) = 32
read(3, 0x8074b54, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1243399160, 47825}, NULL) = 0
gettimeofday({1243399160, 47879}, NULL) = 0
gettimeofday({1243399160, 47947}, NULL) = 0
read(3, 0x8074b54, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=23, events=POLLIN}, {fd=18, events=POLLIN}], 10, 0) = 0
gettimeofday({1243399160, 48277}, NULL) = 0
read(3, 0x8074b54, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=23, events=POLLIN}, {fd=18, events=POLLIN, revents=POLLIN}], 10, -1) = 1
read(18, "\372", 1)                     = 1
gettimeofday({1243399160, 239423}, NULL) = 0
gettimeofday({1243399160, 239686}, NULL) = 0
gettimeofday({1243399160, 239785}, NULL) = 0
gettimeofday({1243399160, 239898}, NULL) = 0
read(3, 0x8074b54, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=23, events=POLLIN}, {fd=18, events=POLLIN}], 10, 0) = 0
gettimeofday({1243399160, 240408}, NULL) = 0
read(3, 0x8074b54, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=23, events=POLLIN}, {fd=18, events=POLLIN, revents=POLLIN}], 10, -1) = 1
read(18, "\372", 1)                     = 1
gettimeofday({1243399165, 47297}, NULL) = 0
select(4, [3], [3], NULL, NULL)         = 1 (out [3])
writev(3, [{"\205\1\2\0\246\1\0\0", 8}], 1) = 8
select(4, [3], [], NULL, NULL)          = 1 (in [3])
read(3, "\1\3\f\5\0\0\0\0\245\1\0\0\0\0\0\0\225\16\0\0\0\0\0\0\0"..., 4096) = 32
read(3, 0x8074b54, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1243399165, 48026}, NULL) = 0
gettimeofday({1243399165, 48080}, NULL) = 0
gettimeofday({1243399165, 48149}, NULL) = 0
read(3, 0x8074b54, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=23, events=POLLIN}, {fd=18, events=POLLIN}], 10, 0) = 0
gettimeofday({1243399165, 48600}, NULL) = 0
read(3, 0x8074b54, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=23, events=POLLIN}, {fd=18, events=POLLIN, revents=POLLIN}], 10, -1) = 1
read(18, "\372", 1)                     = 1
gettimeofday({1243399165, 239630}, NULL) = 0
gettimeofday({1243399165, 239893}, NULL) = 0
gettimeofday({1243399165, 240043}, NULL) = 0
gettimeofday({1243399165, 240201}, NULL) = 0
read(3, 0x8074b54, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=23, events=POLLIN}, {fd=18, events=POLLIN}], 10, 0) = 0
gettimeofday({1243399165, 240799}, NULL) = 0
read(3, 0x8074b54, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll( <unfinished ...>
Process 6196 detached

---

### Post by lovinglinux on 2009-05-30
When you need to paste large amount of text in a post, like the output from strace, use the code tags.

Some extension could be the culprit. Try running firefox in safe mode.

```
firefox -safe-mode
```

This will load firefox without extensions and plugins. If it works, then you might want to disable all extensions and enable one by one to find the culprit.

If that doesn't help, then creating a new profile might solve the problem.

```
firefox -P
```

You could also [disable ipv6](http://www.google.com/search?q=disable+ipv6+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0).

---

### Post by JohnB-nbr on 2009-05-30
I would also suggest you to disable the extensions first.

---

### Post by cupabj on 2009-05-31
I tried a few experiments to notice that this problem is not related to either the extensions or profiles for Firefox. The problem is reproduced when "something" is wrong with network configuration. I noticed that IPv6 was enabled by default on my system. Also, due to an unrelated problem, DHCP was not negotiated correctly on either the ethernet or the wireless interface. This led to existance of phantom network interfaces (eg. eth0:avahi).I disabled IPv6 and used a workaround to get the phantom network interfaces deleted. Firefox always starts correctly once this initial cleanup is done.

Thanks,
-Aniruddha

---

### Post by excalibas on 2011-12-10
Thank you, I had the same problem and 

firefox -safe-mode 
worked for me with Ubuntu maverick and firefox 8.0.

---

### Post by oldtimer7777 on 2011-12-10
When I have issues with Firefox like this I usually run Bleachbit to throughly clean out the caches and everything else:

sudo apt-get install bleachbit
gksu bleachbit

Make sure to not accidentally delete your bookmarks or passwords.

---

### Post by CharlesA on 2011-12-10
Back to sleep you go...

---


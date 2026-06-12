---
title: "appz close without warning"
date: 2009-04-06
forum: General Help
---

### Post by didi32 on 2009-04-06
Hi,

Many of my applications on Ubuntu 8.10 seem to quit unexpectedly and without prior warning. Some applications such as Pidgin and BMPx just quit 90% of the time I use them, and some other applications seem to quit less than that but still do. It looks like the problems of these appz are related, but I can't seem to find what it is. A lot of Java appz also quit unexpectedly.

I'm not talking of appz becoming unresponsive and getting the "Force Quit" message, my main problem is that the appz just close without warning.

Thanks for your help, 

Didi

---

### Post by ryanhaigh on 2009-04-07
Have you checked for any problems in your system logs. You are probably looking for segfaults in these apps which should show up in /var/log/syslog. To check your logs easily you can go to System>Administration and there is an entry in there for system logs.

Alternately you can open a terminal (applications>accessories>terminal) and enter the following command to check syslog for segfaults.
```

grep segfault /var/log/syslog

```

---

### Post by didi32 on 2009-04-07
thanks ryanhaigh,

I'm taking a look at this. I actually upgraded to Jaunty thinking might problem may be fixed with it. I am today using Jaunty and the problem is still present.

Here are some errors in the log:
Apr  6 09:14:34 ljd kernel: [ 3934.428906] filezilla[7320]: segfault at 0 ip 00000000 sp bfd2515c error 4 in filezilla[8048000+1fa000]
Apr  6 11:14:31 ljd kernel: [11131.737186] cyclone[12530]: segfault at 9cfea08 ip 0804bccf sp bfb05510 error 4 in cyclone[8048000+7000]
Apr  6 16:42:40 ljd kernel: [30819.337305] pidgin[21147]: segfault at 554 ip b7d49e40 sp bfe1dd20 error 4 in libX11.so.6.2.0[b7d08000+eb000]
Apr  6 16:42:40 ljd kernel: [30819.987481] gnome-screensav[6590]: segfault at b6bb6490 ip b6bb6490 sp bfc9e32c error 4 in LC_CTYPE[b6bbb000+3f000]
Apr  6 23:12:40 ljd kernel: [ 7461.476748] cyclone[9658]: segfault at 9443cb0 ip 0804bccf sp bf933b40 error 4 in cyclone[8048000+7000]
Apr  6 23:16:21 ljd kernel: [ 7682.525339] cyclone[9657]: segfault at 93e4f24 ip 0804bccf sp bf9d4be0 error 4 in cyclone[8048000+7000]
Apr  6 23:18:16 ljd kernel: [ 7797.478468] cyclone[9925]: segfault at 965acdc ip 0804bccf sp bfbddde0 error 4 in cyclone[8048000+7000]
Apr  7 07:38:35 ljd kernel: [37816.068293] gnome-screensav[6584]: segfault at b6c16490 ip b6c16490 sp bf8fda3c error 4 in LC_CTYPE (deleted)[b6c1b000+3f000]
Apr  7 07:38:35 ljd kernel: [37816.506230] seahorse-agent[6525]: segfault at b6762b50 ip b6762b50 sp bfc6c45c error 4 in libgailutil.so.18.0.1 (deleted)[b6805000+6000]
Apr  7 08:35:28 ljd kernel: [ 3382.730531] pidgin[6510]: segfault at 7d ip b5e6e74e sp bff0d7c0 error 4 in libmsn.so[b5e44000+41000]


The last one just happened, My pidgin just closed unexpectedly while I was chatting...

Thanks,

---

### Post by didi32 on 2009-04-07
I just installed SysV to see all the process currently running. I thought this kind of quits could be coming from another application creating problems and running in the process. So I took off everything that I didn't needed at all times, such as apache, mysql, bluetooth, all the laptop battery management processes etc... Since I rebooted, I didn't have pidgin or other appz closing, but well, I can't tell for sure the problem is fixed since sometimes everything can be fine for a while and then problems arise again...

---


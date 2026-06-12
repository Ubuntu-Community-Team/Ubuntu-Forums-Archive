---
title: "Problem installing Brother 5140 Laser Printer"
date: 2006-07-17
forum: Desktop Environments
---

### Post by SamZor on 2006-07-17
My attempt to install the drivers was based on this guide:

[http://www.ubuntuforums.org/showthread.php?t=123539&highlight=brother+printer+drivers](http://www.ubuntuforums.org/showthread.php?t=123539&highlight=brother+printer+drivers)

i downloaded the drivers from brother here:
[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)
I used the debian packages:
hl5140lpr-1.1.2-1.i386.deb [color=red]the lpr driver[/color]
cupswrapperHL5140-1.0.2-1.i386.deb [color=red]CUPS package[/color]

When i attempt to install the hl5140lpr-1.1.2-1.i386.deb package 

[color]dpkg -i hl5140lpr-1.1.2-1.i386.deb[/color]

i get this error:

```

dpkg -i /home/sam/Desktop/hl5140lpr-1.1.2-1.i386.deb
(Reading database ... 90354 files and directories currently installed.)
Preparing to replace hl5140lpr 1.1.2-1 (using .../hl5140lpr-1.1.2-1.i386.deb) ...
Unpacking replacement hl5140lpr ...
/var/lib/dpkg/info/hl5140lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing /home/sam/Desktop/hl5140lpr-1.1.2-1.i386.deb (--install): subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 /home/sam/Desktop/hl5140lpr-1.1.2-1.i386.deb


```

now the real problem is that this problem has affected my main line of work and now i cannot install java SDK

```

root@samzor:/etc/init.d# apt-get install sun-j2sdk1.5
Reading package lists... Done
Building dependency tree... Done
E: The package hl5140lpr needs to be reinstalled, but I can't find an archive for it.

```

And i cannot use apt-get for anything...
```

E: The package hl5140lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

```

root@samzor:~# apt-get install cupswrapperhl5140
Reading package lists... Done
Building dependency tree... Done
E: The package hl5140lpr needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by krazykirk on 2006-07-17
Hmm... well first i would suggest trying to remove that hl5140lpr package, by going apt-get remove hl5140lpr, or something in that effect to remove it. That should make the package managers work again.

Also to get that printer working, go to Administration>Printers, and try to install it there. It doesn't matter that your printer isn't listed, as lots of them use the same driver. One of those printer drivers are bound to work with your printer, it would just take a bit of testing,

Hope that helps! =)

---

### Post by SamZor on 2006-07-18
Thankyou for the suggestions

I have attempted to use the GUI  "System -> Administration -> Printing"
and i get a message:
[color=green]"The CUPS server could not be contacted"[/color]

Moreover apt-get remove does not function, its like it cant build the dependency tree for this package or something. I wish i knew which files to look at.

```

root@samzor:~# apt-get remove hl5140lpr
Reading package lists... Done
Building dependency tree... Done
E: The package hl5140lpr needs to be reinstalled, but I can't find an archive for it.

```

You can see the irony in the situation... it has not yet completely installed, yet cannot be removed unless completely installed , which would fix my problem anyway ](*,)

This thread seems to highlight my problem. Obviously there is something wrong with my half installed packages on the DPKG tree

[http://www.ubuntuforums.org/archive/index.php/t-177538.html](http://www.ubuntuforums.org/archive/index.php/t-177538.html)

looking in [color=red]/var/log/dpkg.log[/color] confirms this...

```
2006-07-18 01:45:07 status half-installed cupsys 1.2.0-0ubuntu5
2006-07-18 01:45:08 status half-installed cupsys 1.2.0-0ubuntu5
```

```

2006-07-13 12:06:25 install hl5140lpr <none> 1.1.2-1
2006-07-13 12:06:25 status half-installed hl5140lpr 1.1.2-1
2006-07-13 12:06:25 status unpacked hl5140lpr 1.1.2-1
2006-07-13 12:06:25 status unpacked hl5140lpr 1.1.2-1
2006-07-13 12:06:25 status unpacked hl5140lpr 1.1.2-1
2006-07-13 12:06:25 status half-configured hl5140lpr 1.1.2-1
2006-07-14 23:44:00 install ntp <none> 1:4.2.0a+stable-8.1ubuntu6
2006-07-14 23:44:00 status half-installed ntp 1:4.2.0a+stable-8.1ubuntu6
2006-07-14 23:44:00 status unpacked ntp 1:4.2.0a+stable-8.1ubuntu6

```

now i try to unpack the package...

```

root@samzor:~# dpkg --unpack /home/sam/Desktop/hl5140lpr-1.1.2-1.i386.deb
(Reading database ... 90354 files and directories currently installed.)
Preparing to replace hl5140lpr 1.1.2-1 (using .../hl5140lpr-1.1.2-1.i386.deb) ...
Unpacking replacement hl5140lpr ...
/var/lib/dpkg/info/hl5140lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing /home/sam/Desktop/hl5140lpr-1.1.2-1.i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 /home/sam/Desktop/hl5140lpr-1.1.2-1.i386.deb

```

and now an even more powerful option

```

root@samzor:~# dpkg --purge --force-remove-reinstreq hl5140lpr
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 90353 files and directories currently installed.)
Removing hl5140lpr ...
/var/lib/dpkg/info/hl5140lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing hl5140lpr (--purge):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl5140lpr

```

For now i have solved the problem using what i consider a very dirty approach:
editing the [color=red]/var/lib/dpkg/status[/color].
However i am in a lot of trouble when i need to print something, and as for printers... well there does not appear to be a CUPS server now... 
Might need some help rebuilding it all since apt-get and synaptic etc all seem to work now.

---

### Post by cyberia81 on 2007-11-03
I'm having this issue as well and it seems that this post was abandoned. I just want to remove this printer altogether. I removed it through System-Administration-Printing, but it still remains in /var/lib/dpkg and I can't figure out how to get rid of it. I'm stuck because I have things to install but I can't... Any ideas? Thank you!

---


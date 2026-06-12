---
title: "Intel Corporation 82845G/GL[Brookdale-G] and Ubuntu 10-10 Compiz issues."
date: 2010-11-19
forum: Desktop Environments
---

### Post by uncle-c on 2010-11-19
Hi,
Apologies for this old chestnut but I did manage to get compiz working well on Ubuntu 8.10 and wanted to know if anyone has got it to work on Ubuntu 10.10 with the above intel graphics ? I've used several methods to skip the blacklist check including making a compiz-manager config file with a skip_check=yes line and also editing the compiz file with a hex editor :

[http://art.ubuntuforums.org/showthread.php?t=1467202](http://art.ubuntuforums.org/showthread.php?t=1467202)

Unfortunately none of these methods work.
I've run the compiz-check script and it suggests that compiz should work.
```

unclec@ubuntu-home:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

All the intel drivers are up to date.Should I make specific changes to my xorg.conf file ?

Thanks.

---

### Post by scubasteve657 on 2011-12-15
Hello,

I can't answer your question, so sorry if this is a waste of your time.

I've had difficulties with this chipset using Ubuntu 10.04, so I've upgraded to 10.10 and so far so good.

Has this chipset been working well for you using Ubuntu 10.10 (except for the compiz problem)?  It would be very helpful to get a quick answer on this before I return the machine to it's owner, and I'd like to return it as soon as possible.

You're input would be greatly appreciated :)

Peace,
Steve

---

### Post by mrdragon333 on 2011-12-17
[FONT=Book Antiqua][SIZE=3]how do i install driver for this board?
i am really puzzled... i have searched many sites but haven'e found the solution ,
if you could help install graphics drivers for this mother board .
[/SIZE][/FONT]

---


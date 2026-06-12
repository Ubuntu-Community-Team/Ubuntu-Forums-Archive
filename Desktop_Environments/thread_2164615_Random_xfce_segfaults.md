---
title: "Random xfce segfaults"
date: 2013-08-01
forum: Desktop Environments
---

### Post by Anthony_Clays on 2013-08-01
I've been getting xfce crashes ever since I installed xubuntu. After looking through past threads for a few minutes, I can't seem to find anyone experiencing *exactly* the same problem, so I'll be posting all the information I believe can be valuable.

First of all: The segfaults don't happen truly randomly - it only occurs when I open a new window.

The last few lines of dmesg:
```

dmesg | tail
[ 3428.603200] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5139.277058] show_signal_msg: 48 callbacks suppressed
**[ 5139.277069] xfce4-session[1994]: segfault at ffffffff00000000 ip 00007f26cbee0f7f sp 00007fff61789d60 error 5 in libglib-2.0.so.0.3600.0[7f26cbe7d000+f9000]**
[ 5139.621277] bbswitch: disabling discrete graphics
[ 5139.633680] pci 0000:01:00.0: Refused to change power state, currently in D0
[ 5139.837855] pci 0000:01:00.0: power state changed by ACPI to D3cold
[ 5144.583520] bbswitch: enabling discrete graphics
[ 5144.941619] pci 0000:01:00.0: power state changed by ACPI to D0
[ 5144.967483] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=none,decodes=none:owns=none
[ 5144.972101] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.88  Wed Mar 27 14:26:46 PDT 2013

```

The last six lines are output of bumblebee (a FOS / Linux alternative to nvidia's Optimus software, which automagically assigns GPU-intensive applications to either the CPU's integrated graphics, or the more powerful dedicated graphics card) and they have nothing to do with the segfaults - as those have been happening well before I installed bumblebee.

The third line is what's important here - and it's always in this format:
[LIST]
[*]xfce4-session[<PID>]: segfault at ffffffff00000000 ip 0000xxxxxxxxxxxx sp 0000xxxxxxxxxxxx error 5 in libglib-2.0.so.0.3600.0[xxxxxxxxxxxx+f9000]
[/LIST]
I have no idea what
[LIST]
[*]show_signal_msg: 48 callbacks suppressed
[/LIST]
is supposed to mean, but considering the fact that it happens microseconds before the segfault makes me believe it's of importance here.
I'm using xubuntu 13.04, with xfce 4.10.0 (nothing special here).
I've changed my window manager from standard xfwm4 to **compiz**, and my window decorator from gtk-window-decorator to **emerald** - and it's very probable that the problem has something to do with this.

I've been learning myself a lot about Linux the last few months, but I'm far from a guru, so if you want me to post some additional information I'll be glad to help :)
Thank you for your time.

---

### Post by carbonfreeze on 2013-08-01
This is a known issue, see the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1104435](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1104435)

I've been using the proposed PPA fix, I'm not sure if the update has been pushed to the repositories yet.

---

### Post by Bashing-om on 2013-08-01
et all :
cuurently:
> 
sysop@1304mini:~$ dpkg -l xfce4-session
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  xfce4-session  4.10.0-2ubun amd64        Xfce4 Session Manager
sysop@1304mini:~$ apt-cache policy xfce4-session
xfce4-session:
  Installed: 4.10.0-2ubuntu1
  Candidate: 4.10.0-2ubuntu1
  Version table:
 *** 4.10.0-2ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/universe amd64 Packages
        100 /var/lib/dpkg/status
sysop@1304mini:~$ 


sysop@1304mini:~$ apt-cache show xfce4-session
<snip>
Architecture: amd64
Version: 4.10.0-2ubuntu1
Replaces: xfce4-utils
Provides: x-session-manager
<snip>



I too am considering the PPA to upgrade "xfce4-session"

[INDENT][INDENT]just my little bit to help[/INDENT][/INDENT]

---

### Post by Anthony_Clays on 2013-08-02
Thank you very much for your help, installing the package from the ppa fixed the problem!
Marked this thread as solved.

---


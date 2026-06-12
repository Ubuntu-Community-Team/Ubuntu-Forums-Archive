---
title: "Minecraft crashes on world create."
date: 2011-11-09
forum: Gaming &amp; Leisure
---

### Post by litttleman199211 on 2011-11-09
So when I got to play minecraft everything looks fine but it keeps crashing when I go to create a new world...I have a bug report.

System: Linux 2.6.38-12-generic #51-Ubuntu SMP Wed Sep 28 14:25:20 UTC 2011 i686
X Vendor: The X.Org Foundation
X Vendor Release: 11001000
Selinux: No
Accessibility: Disabled
GTK+ Theme: Ambiance
Icon Theme: ubuntu-mono-dark
GTK+ Modules: gnomesegvhandler, canberra-gtk-module

Memory status: size: 1531207680 vsize: 1531207680 resident: 449343488 share: 35950592 rss: 449343488 rss_rlim: 18446744073709551615
CPU usage: start_time: 1320878811 rtime: 1913 utime: 1811 stime: 102 cutime:0 cstime: 1 timeout: 0 it_real_value: 0 frequency: 100



----------- .xsession-errors ---------------------
** (gnome-session:1497): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1497): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1497): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
OMP: Error #15: Initializing libiomp5.a, but found libiomp5.a already initialized.
OMP: Hint: This may cause performance degradation and correctness issues. Set environment variable KMP_DUPLICATE_LIB_OK=TRUE to ignore this problem and force the program to continue anyway. Please not
Multiple segmentation faults occurred; can't display error dialog
** (gnome-session:1497): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1497): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1497): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.
/home/shamus/9143: No such file or directory.
No stack.
--------------------------------------------------

---

### Post by Rubykuby on 2011-11-11
Do you have an AMD graphics card/driver? If yes, that may be part of the problem.

---


---
title: "NEW install , compiz not accepting selected plugins"
date: 2007-07-15
forum: Desktop Effects &amp; Customization
---

### Post by codemills on 2007-07-15
Hello,

I really struggled my way to get this running in first place. I wanted to get Compiz fusion (which seems bleeding edge now). Compiz is running now, But when i go >> System >> Preferences >> CompizConfig SettingsManager, and apply "window preview" or "rotate" (and all nice options not selected before) its just not applying when i click close...

I cant get rotate or any new plugins at all.. Where am i going wrong? what to do?

Below is necessary specs of my machine. Its HP Pavilion 6114 tx Laptop Centrino duo process 1.5gb ram etc.
=====================================================================
[[kyro@localhost ~]$ rpm -qa | grep compiz
compiz-fusion-plugins-main-0.0.1-0.5.20070708git.fc7
libcompizconfig-0.0.1-0.5.20070708git.fc7
compiz-fusion-plugins-extra-0.0.1-0.5.20070708git.fc7
compizconfig-python-0.0.1-0.5.20070708git.fc7
compiz-gnome-0.5.1-0.7.20070708git.fc7
compiz-0.5.1-0.7.20070708git.fc7
compizconfig-settings-manager-0.0.1-0.5.20070708git.fc7


[kyro@localhost ~]$ rpm -qa | grep emerald
emerald-themes-0.3.0-0.1.20070625git.fc7
emerald-0.3.0-0.3.20070630git.fc7


[kyro@localhost ~]$ cat /etc/yum.repos.d/kagesenshi.repo
[kagesenshi-compiz]
name=KageSenshi's Compiz Fusion repository
baseurl=http://devel.foss.org.my/~kagesenshi/repo/pub/$basearch/
enabled=1
gpgcheck=0

[kyro@localhost ~]$ uname -r
2.6.21-1.3228.fc7


[kyro@localhost ~]$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module 100.14.11 Wed Jun 13 18:21:22 PDT 2007
GCC version: gcc version 4.1.2 20070502 (Red Hat 4.1.2-12)

[kyro@localhost ~]$ glxinfo | grep direct
direct rendering: Yes
[kyro@localhost ~]$

[kyro@localhost ~]$ cat /var/log/Xorg.0.log | grep "EE"
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
[kyro@localhost ~]$
=====================================================================

---


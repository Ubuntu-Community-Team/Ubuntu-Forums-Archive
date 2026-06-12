---
title: "Problem w pulse-rt"
date: 2009-05-28
forum: General Help
---

### Post by terryleon on 2009-05-28
sound gone after upgrade to 9.04
here's what i've tried so far (and TIA)

terryleon@hannah-the-dog:~$ pulseaudio -k ; pulseaudio -D --log-target=syslog
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
terryleon@hannah-the-dog:~$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio
[sudo] password for terryleon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libasound2-plugins is already the newest version.
padevchooser is already the newest version.
libsdl1.2debian-pulseaudio is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
terryleon@hannah-the-dog:~$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflashsupport is not installed, so not removed
Package flashplugin-nonfree-extrasound is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
terryleon@hannah-the-dog:~$ pavucontrol
terryleon@hannah-the-dog:~$ sudo useradd -G pulse-rt terryleon
useradd: user terryleon exists
terryleon@hannah-the-dog:~$ pulseaudio --start -vvv
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: PolicyKit refuses acquire-high-priority privilege.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: main.c: Can realtime: no, can high-priority: no
D: main.c: Can realtime: no, can high-priority: no
I: main.c: Daemon startup successful.
terryleon@hannah-the-dog:~$ sudo usermod -G pulse-rt terryleon
terryleon@hannah-the-dog:~$ pulseaudio --start -vvv
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: PolicyKit refuses acquire-high-priority privilege.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: main.c: Can realtime: no, can high-priority: no
D: main.c: Can realtime: no, can high-priority: no
I: main.c: Daemon startup successful.
terryleon@hannah-the-dog:~$ groups
terryleon adm dialout cdrom plugdev lpadmin admin sambashare
terryleon@hannah-the-dog:~$ usermod -a -G pulse-rt terryleon
usermod: unable to lock password file
terryleon@hannah-the-dog:~$ id
uid=1000(terryleon) gid=1000(terryleon) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(terryleon)
terryleon@hannah-the-dog:~$ sudo usermod -a -G pulse-rt terryleon
[sudo] password for terryleon: 
terryleon@hannah-the-dog:~$ groups
terryleon adm dialout cdrom plugdev lpadmin admin sambashare
terryleon@hannah-the-dog:~$

---

### Post by dmizer on 2009-05-28
Have a look at the 7th link in my sig :)

---

### Post by terryleon on 2009-05-28
At least something has changed!

terryleon@hannah-the-dog:~$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
mkdir: cannot create directory `/home/terryleon/pulse-backup': File exists
terryleon@hannah-the-dog:~$ sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf
[sudo] password for terryleon: 
terryleon is not in the sudoers file.  This incident will be reported.
terryleon@hannah-the-dog:~$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio
[sudo] password for terryleon: 
terryleon is not in the sudoers file.  This incident will be reported.
terryleon@hannah-the-dog:~$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
[sudo] password for terryleon: 
terryleon is not in the sudoers file.  This incident will be reported.
terryleon@hannah-the-dog:~$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
[sudo] password for terryleon: 
terryleon is not in the sudoers file.  This incident will be reported.
terryleon@hannah-the-dog:~$

---

### Post by dmizer on 2009-05-28
The user you are logged in with does not have sudo privileges. Do you have more than one account on that computer?

Edit:
Here's how to fix the "terryleon is not in the sudoers file. This incident will be reported." problem: [http://ubuntuforums.org/showpost.php?p=4489807&postcount=3](http://ubuntuforums.org/showpost.php?p=4489807&postcount=3)

---

### Post by terryleon on 2009-05-28
There is only one user on the sys, me. As you can see from the two logs, it took my p/w at first, then started rejecting it. 
domo arigatou

---

### Post by dmizer on 2009-05-28
See my edit above for the fix then. :)

---


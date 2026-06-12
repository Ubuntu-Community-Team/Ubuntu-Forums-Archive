---
title: "Ubuntu 8.04 hangs up several times within hours after upgrading kernel to 2.6.24.x!"
date: 2008-10-28
forum: Desktop Environments
---

### Post by forrestxm on 2008-10-28
After auto-upgrade kernel to 2.6.24 level, I experienced system overall hangs up several time within hours. Can anyone help me out? I just moved from windows to Ubuntu, and would like to use it instead of Windows. I don't want to back to Windows cause of unstable Ubuntu performance. So pls help me out! Thanks!

What kind of information I should provide here for analysis? Please kindly advise and let me know what commands used to collect those info. thanks a lot!

---

### Post by eder.apt-get on 2008-10-28
That´s why I don´t like to upgrade the kernel. I´d rather reinstall a new version of the whole system. 
Maybe you should post what your system logs says. Some examples:
=> /var/log/messages : General log messages

=> /var/log/boot : System boot log

=> /var/log/debug : Debugging log messages

=> /var/log/auth.log : User login and authentication logs

=> /var/log/daemon.log : Running services such as squid, ntpd and others log message to this file

=> /var/log/dmesg : Linux kernel ring buffer log

=> /var/log/dpkg.log : All binary package log includes package installation and other information

=> /var/log/faillog : User failed login log file

=> /var/log/kern.log : Kernel log file

=> /var/log/lpr.log : Printer log file

=> /var/log/mail.* : All mail server message log files

=> /var/log/mysql.* : MySQL server log file

=> /var/log/user.log : All userlevel logs

=> /var/log/xorg.0.log : X.org log file

=> /var/log/apache2/* : Apache web server log files directory

=> /var/log/lighttpd/* : Lighttpd web server log files directory

=> /var/log/fsck/* : fsck command log

=> /var/log/apport.log : Application crash report / log file

To view log files at shell prompt:
tail -f /var/log/apport.log
more /var/log/xorg.0.log
cat /var/log/mysql.err
less /var/log/messages
grep -i fail /var/log/boot

---

### Post by forrestxm on 2008-10-30
Found pattern of hanging up. Every time it hangs up, along with using TightVNC to connect to remote machine.

Is there any unspeak problem between tightvnc and ubuntu?

I checked those logs, beside ACPI error(I think it's unrelated to my hangs, since every boot, that error appears), no other obvious findings.

---

### Post by hictio on 2008-10-30
I couldn't even use the new kernel, installed fine and everything, but after compiling the Mad WiFi driver for my Atheros card, it throws a [kernel panic upon booting](http://oesediez.blogspot.com/2008/10/kernel-dance-got-sour.html), and it didn't fixed the [problems with USB after hibernate/ suspend either](http://oesediez.blogspot.com/2008/09/ubuntu-on-compaq-presario-f700-4.html), so I'm still running with '2.6.24-19-generic'.

---


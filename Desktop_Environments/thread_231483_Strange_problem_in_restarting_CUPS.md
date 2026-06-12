---
title: "Strange problem in restarting CUPS"
date: 2006-08-07
forum: Desktop Environments
---

### Post by gborzi on 2006-08-07
Hello,
I have a strange problem when restarting or stop/starting cupsys, i.e. if I give the command
> sudo /etc/init.d/cupsys restart or
> sudo /etc/init.d/cupsys stop
sudo /etc/init.d/cupsys start
the start and restart commands hang, and I have to give a Ctrl+C to terminate the command. While cupsys is hanged there are two running instances of cupsd, as if the cupsys script launchs a cupsd in background (the process with the lowest PID stored in /var/run/cups/cupsd.pid) and another one in forground with the -f option. When I give the Ctrl+C the "foreground" cupsd is killed and printing works fine. I have noticed that this problem doesn't happen in single user mode. I have this problem in my home desktop and laptop, both running the i386 flavor of ubuntu. On my amd64 office desktop it works fine, and the configurations are the same, besides the different printers. It's the first time I have noticed a bug in the i386 and not on amd64 !
I know this is only a minor annoyance, expecially when updating or installing some cups related package (I noticed it for the first time when I installed cups-pdf and recently with the cups update), anyway I would like to know if other people have had the same problem and eventually how they solved it.

---


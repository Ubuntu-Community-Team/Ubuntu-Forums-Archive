---
title: "amule process sleeps after 20 minutes left idle"
date: 2011-11-16
forum: Desktop Environments
---

### Post by davidmb on 2011-11-16
Hi,

Since I installed Kubuntu 11.10, I've noticed amule "goes to sleep" after the computer is left idle for 20 minutes.
Upon returning to the computer, the amule window takes some time to respond to mouse clicks and the "Statistics" pane clearly shows it has been doing nothing but sleeping.

This didn't happen in Kubuntu 11.04 and other long running applications (like JDownloader) and services (SSH) don't show this behavior in 11.10.
I also tried leaving amule maximized, minimized and minimized to the systray with no difference at all (I don't think it has anything to do with the window manager).
The screensaver is activated after 5 minutes of inactivity and the screen is put to sleep after 10 (it doesn't seem to be power-saving related either).

To see what's going on, I've opened an SSH console and run 'top' as well as this little script:
```
c=0; while true; do echo $c `ps -C amule -o %cpu,cputime`; sleep 10; let c=c+10; done
```Exactly after 20 minutes, CPU usage goes to 0 in 'top' and the script shows no increment in 'cputime'.

Does anyone know what's going on here? Has this happened to anyone else?

Thanks!

---

### Post by davidmb on 2011-11-16
Anyone?

---

### Post by kasper22 on 2012-04-10
I have the same problem, but is just any application that is running from the desktop.  It's like anything on the desktop is going to sleep after 20 minutes of the computer being idle.  If I run a script in a 'screen' session it will run fine, but if I run that same script from a desktop terminal it will pause after 20 minutes and resume once I come back to the computer.

I checked the power settings and the only thing it shows is that I have the monitor shutting off after 15 minutes.

-Bryan

---

### Post by davidmb on 2012-05-22
Hi,

It's been some time but anyway, I think it's important to note the issue is gone in Kubuntu 12.04.
Definitely there was something wrong with 11.10 kernel.
Not only amule, but sometimes the whole Plasma desktop was completely  suspended and/or swapped to disk despite having more than enough RAM.

Weird but thankfully fixed :-)

---


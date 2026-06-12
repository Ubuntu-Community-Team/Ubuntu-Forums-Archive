---
title: "&quot;GUI&quot; stopped running after upgrade"
date: 2013-08-03
forum: Desktop Environments
---

### Post by Jacob_Butcher on 2013-08-03
I'm running Ubuntu 12.04 on my server.

A few days ago I ran "apt-get upgrade".  Everything seemed fine.
Today my server rebooted.  (I don't know why, but it's usually a power outage that outlasts my UPS.)

Now the server doesn't run the GUI at startup.  Nor does it run a shell.
It just lists out a series of services it's starting (apache, ssh, etc) and stops.
I can ssh into the server and all the external services seem fine.
But no GUI, no shell.

I believe I was running gdm.  I reinstalled it, but that didn't help.

I don't really understand all the moving parts needed to get a GUI running, though there seem to be a lot of them.  I'd be happy to answer any questions that might help narrow down the problem.

(I'm a software engineer, if that makes any difference.  Not the sysadmin kind, obviously.)

Thanks!
  Jacob

---

### Post by jmccarron on 2013-08-12
I am also running 12.04 server on my laptop (Lenovo T61), and I had the same experience of losing the GUI I had installed after the most recent update/upgrade. I had also admittedly used Ubuntu Tweak to clean up old files as well as kernels and their support files, but I do not recall if that was before or after the update, and I am not sure if there had been a reboot after the cleanup (it is tough getting old). The GUI I was running usually was Unity 2D (though to get some memory back I sometimes ran FVWM), and I have installed/re-installed ubuntu-desktop, lubuntu-desktop, xubuntu-desktop, and kubuntu-desktop but still do not boot into the GUI. It seems that  lightdm can be started (no, it is/was not started on boot) but no GUI is subsequently found on Ctrl-Alt-F7, just a number of text lines from bootup. The bootup messages indicate the vesafb is in use. lspci gives the video subsystem as "01:00.0 VGA compatible controller: NVIDIA Corporation G86 [Quadro NVS 140M]" and /var/log/syslog shows it loading and no errors reported.  I ran failsafe mode from grub and ran first the dpkg repair option, then tried the failsafeX but that produced this error:
"gdm: unrecognized service
stop: unknown instance
xinit /usr/share/xdiagnose/failsafeXinit /etc/X11/xorg.conf.failsafe with- -- /usr/bin/X -br -once -config  /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log 

X: cannot stat /etc/X11/X (no such file or directory) aborting."

Resuming boot from the failsafe menu still gives me no GUI, but all the virtual terminals 1-6 are present. 

I cannot connect to a vnc session anymore, and this is my primary system. Luckily my data is saved off, but not the OS.  

I know that the Ubuntu Tweak clean up may have muddied the waters on this issue, but I also need help with this getting resolved.

Thanks,
John

---

### Post by Jacob_Butcher on 2013-08-13
I tried ctrl-alt-F8, and found an X login screen.  (Actually, I think it started just after I pressed ctrl-alt-F8.)

I don't know why the display defaulted to displaying boot log messages instead of the X login screen as it did previously.

I don't boot that often, so I can live with it.  But it would be nice to be able to upgrade without mysterious changes.

---


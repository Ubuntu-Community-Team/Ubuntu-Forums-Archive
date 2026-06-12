---
title: "Desktop not loading after login (.02 BTC bounty for assistance)"
date: 2014-03-13
forum: Desktop Environments
---

### Post by hmsimha on 2014-03-13
EDIT: Bounty has been claimed. I'm going to post a synopsis of what worked soon.

I'm willing to offer a .02 BTC bounty to whoever is able to assist me with the resolution of this problem (or if you don't use bitcoin, I'd also be willing to donate it to a charity of your choice that is set up to accept bitcoin).


Yesterday when I was using google chrome, one of the tabs seemed like it became attached to my cursor for pretty much no reason (as if I was trying to drag a tab into a separate window), and I couldn't get it detached. Left clicking, right clicking, and using keyboard shortcuts didn't do anything to remove the miniature tab representation from the cursor icon. I pulled up a terminal and killed all chrome processes and it seemed to work, but I decided to restart the laptop since I had installed updates that were waiting on a restart anyway.


Since restarting, I haven't been able to use my laptop. At first, when I would boot up I would be taken to the login screen, and upon logging in the cursor would be visible, but the background black. The same thing would happen if I tried to log in as guest. After trying several things, it seems like when I start up now and try to log into my user account, a message about apache ('could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'Servername' directive globally to suppress this message') not being able to start flashes on a black screen very briefly and I am taken back to the login screen.


I can still Alt+f1 into the system terminals, and was able to back up all my important documents, but I would hate to have to completely reinstall and set up everything from scratch again.


I've included the contents of several logs, as well as dmesg, in [this gist]("https://gist.github.com/anonymous/1a920001498d85df952d"). Files in order are Xorg.0.log, Xorg.1.log, Xorg.2.log, Xorg.failsafe.log, boot.log, bootstrap.log, dmesg, dpkg.log, and kern.log.

EDIT: I uploaded my syslog as well to [this gist]("https://gist.github.com/hmsimha/54d108d47ccb6b6ef104"). Some of the recent messages will be from trying to email out some of my log files (which didn't work).

Also, if I try running `lightdm` I get a GUI message that I am running in low graphics mode. Once I accept that (the mouse doesn't work on this screen even though it is using a GUI), I get taken to the blank screen with the apache2 message above again.

Output of `lspci -v | grep VGA`:
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])

output of `lsmod | grep i915`:
[COLOR=#000000][FONT=Consolas]i915[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]         66139[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] 2
i2c_algo_bit[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] 13413[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] 1[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] i915
drm_kms_helper[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]5270[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]  1[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] i915
drm[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]          297056[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] 3[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] i915,drm_kms_helper
video[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]        19318[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] 1[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] i915

[FONT=verdana]more edit:
at IRC user arrith's recommendation, I looked at [/FONT][/FONT][/COLOR]http://community.linuxmint.com/tutorial/view/842, restarted and added the 'nomodeset' command to the end of the line starting with 'linux' in my grub settings, then tried booting again. This time, instead of going to the login screen I was taken straight to tty1. [These ]("https://gist.github.com/hmsimha/937bb4fbefd783935d55")are my new syslog, Xorg.0.log, and Xorg.0.log.old files (the xorg.0.log.old is surprisingly not the same as the previous xorg.0.log). On alt+f7 (which would normally take me to the login screen if open), I instead had the following lines:
> [COLOR=#000000][FONT=Consolas]starting lightdm display manager[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
stopping send an event to indicate plymouth is up[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
[/FONT][/COLOR][FONT=Consolas]AH0058: apache2: could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'Servername' directive globally to suppress this message[/FONT][COLOR=#000000][FONT=Consolas]
skipping profile [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]in /etc/apparmor.d/disable: usr.bin.firefox[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting systemd[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting starpar[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]stopping startpar[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting apparmor profiles[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
setting up x socket directories[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
stopping system v initialisation compatibility[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting system v runlevel compat[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting openssh server[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting restore sound card state[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting acpi daemon[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting anac(h)ronistic cron[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
startging configure network device security[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting mDNS/DNS-SD daemon[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting automatic crash report generation[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]starting reload cups, upon starting avahi-daemon to make sure remote queues are populated[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting cups-browsed[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]- bonjour remote printer browsing daemon[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting configure virtual network devices[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting startpar bridge for notification of upstart job start/stop[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]sopping startpar bridge for notification of upstart job start/stop[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]starting reload cups, upon starting avahi-daemon to make sure remote queues are populated [fail][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]stopping restore sound card state[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting cpu interrupts balancing daemon[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
stopping[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
stopping anac(h)ronistic cron[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
starting regular background program processing daemon[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
stopping save kernel messages[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]starting startpar again twice[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]starting startpar bridge for notification of upstart job start/stop[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [OK][/FONT][/COLOR][COLOR=#000000][FONT=Consolas]
[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]starting startpar bridge for notification of upstart job start/stop [OK]

[/FONT][/COLOR][FONT=verdana][COLOR=#000000]So all of those say they're [ok] except the *second* line that says starting reload cups, which says [fail] on the right[/COLOR][/FONT]

---

### Post by hmsimha on 2014-03-14
Just wanted to post that the problem has been resolved and bounty claimed. I'm going to go through my IRC logs to post what worked tomorrow in case anyone has a similar issue

---


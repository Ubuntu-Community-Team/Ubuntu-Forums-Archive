---
title: "Ubuntu 5.10 on IBM T43 Random Hangs"
date: 2005-12-07
forum: General Help
---

### Post by mossman84 on 2005-12-07
Hi,
I have installed Ubuntu 5.10 on my IBM T43. It took a while, but I managed to get all the drivers working including suspend/hibernate and 3D acceleration for the onboard X300.

I am however, experiencing a very strange problem. The entire system will hang randomly, about once every 3 days without warning. The mouse and keyboard will stop responding, Ctrl-Backspace will not kill X, Ctrl-Alt-F# will not switch to another console.

Searching around the syslog does not provide any useful information. Here are the last few entries. The system hung somewhere inbetween 00:15 and 02:21. 02:21:54 is the restart.
 
Dec  7 00:15:17 mossman kernel: [4491801.078000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Dec  7 00:15:17 mossman kernel: [4491801.078000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Dec  7 00:15:17 mossman kernel: [4491801.183000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Dec  7 00:15:17 mossman kernel: [4491801.183000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Dec  7 00:17:01 mossman /USR/SBIN/CRON[13452]: (root) CMD (   run-parts --report /etc/cron.hourly)
Dec  7 00:37:49 mossman -- MARK --
Dec  7 00:39:01 mossman /USR/SBIN/CRON[14068]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Dec  7 00:57:49 mossman -- MARK --
Dec  7 01:09:01 mossman /USR/SBIN/CRON[14799]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Dec  7 02:21:54 mossman syslogd 1.4.1#17ubuntu3: restart.
Dec  7 02:21:54 mossman kernel: Inspecting /boot/System.map-2.6.12-9-686

I get these "atkbd.c: Unknown key pressed/released" alot so I don't think it is the problem.

Is there anyway to increase the kernel log verbosity so that I can track down the problem? Or is there anyone who is facing the same problem and found a solution? This is troublesome as I cannot reproduce the hang. Once it hung while I was using vim in gterm (!!).

Thanks

---


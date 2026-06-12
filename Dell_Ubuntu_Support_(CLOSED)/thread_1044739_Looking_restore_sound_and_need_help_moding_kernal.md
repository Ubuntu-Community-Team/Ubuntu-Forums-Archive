---
title: "Looking restore sound and need help moding kernal"
date: 2009-01-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Anditsu on 2009-01-19
For the lonest time I have been using an older kernal instead of replacing the driver and using the current driver. So I decided to take a shot at it so that I can use virtual box to watch netflix. I began working on the advise presented here.

 [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade).

After completing step one my history is as follows.

-desktop:~$ sudo dpkg -r hsfmodem
[sudo] password for anditsu: 
(Reading database ... 228186 files and directories currently installed.)
Removing hsfmodem ...

Removing hsf driver from /lib/modules/2.6.24-19-generic/
Warning: Module snd_hda_intel is in use
Sending TERM signal to processes still using the driver:
  PID USER     COMMAND
 6457 anditsu  /usr/bin/pulseaudio --log-target=syslog
 6727 anditsu  /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=25
 6927 anditsu  /usr/lib/firefox-3.0.5/firefox
anditsu@dell-desktop:~$ $ sudo dpkg -r linux-backports-modules-2.6.22-14-generic
bash: $: command not found
anditsu@dell-desktop:~$ 
anditsu@dell-desktop:~$ $ sudo dpkg -r linux-backports-modules-2.6.22-14-generic
bash: $: command not found
@dell-desktop:~$ $ sudo dpkg -i hsfmodem_7.68.00.09oem_i386.deb
bash: $: command not found
anditsu@dell-desktop:~$ man dpkg

It's odd with no sound please help

---

### Post by Anditsu on 2009-01-20
As it turns out All I needed to do was remove the old driver and restart the computer. The current kernal had a driver that was picked up. Problem solved.

---


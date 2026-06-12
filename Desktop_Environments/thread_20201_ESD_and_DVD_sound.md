---
title: "ESD and DVD sound"
date: 2005-03-15
forum: Desktop Environments
---

### Post by clb137 on 2005-03-15
Hi,

Can someone please tell me why i have to 'kill esd' to get sound to work with my DVD player, which is gxine, 

I am using the latest preview release with all the up date, i have worked out that i have to enable dma support using the command line 'hdparm -d 1 /dev/hdc, (is there anyway to automate this? I have tried /etc/hdconf file and when i reboot i get /dev/hdc does not exsit, same if i put 'cdrom'.

I have created a small .sh file to action the above and start gxine, and my dvd's play lovely sound in sync and lovely frame rate, however then i have no system sounds, until i reboot.

This is my first go at ubuntu, as i have changed from mepis, i have been playing with linux for a while and i think this is the best i have seen and used please keep up the good work.

thanks 

Clinton

---

### Post by wmcbrine on 2005-03-15
I've never had much luck with esd in previous distros. Now, after installing Ubuntu, one of the first things I ran into was trouble with esd. So I just disabled it (I don't really need sounds on events), and set /etc/libao.conf to "default_driver=alsa". (Oh, and before that, I replaced totem-gstreamer with totem-xine.) But there's probably a better solution.

---


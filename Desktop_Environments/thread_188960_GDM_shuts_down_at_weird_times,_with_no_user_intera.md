---
title: "GDM shuts down at weird times, with no user interaction (using XGl/compiz)"
date: 2006-06-04
forum: Desktop Environments
---

### Post by kwaanens on 2006-06-04
I have been running Dapper for about 2 months now. I recently set up XGl/ Compiz and it works without a hitch. Except...
I have now four or five time times experienced that the system logs out, shutting down all applications. This behaviour has no apparent regularity, but it has only shut down, when I don't use the computer. It's maybe worth mentioning that the computer has sometimes been running overnight and I have not had the problem then.

This is an excerpt from /var/log/messages, just before the last crash:
```
Jun  4 22:05:21 inspiron kernel: [4305354.358000] Inbound IN=eth0 OUT= MAC=[blanked] SRC=[blanked] DST=[blanked] LEN=60 TOS=0x00 PREC=0x00 TTL=114 ID=7304 PROTO=UDP SPT=6346 DPT=53548 LEN=40
Jun  4 22:08:07 inspiron gconfd (root-9962): GConf-tjeneren er ikke i bruk, stenger ned.
Jun  4 22:08:07 inspiron gconfd (root-9962): Avslutter
Jun  4 22:08:10 inspiron kernel: [4305522.476000] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
Jun  4 22:08:10 inspiron kernel: [4305522.481000] [fglrx] total      GART = 67108864
Jun  4 22:08:10 inspiron kernel: [4305522.482000] [fglrx] free       GART = 51118080
Jun  4 22:08:10 inspiron kernel: [4305522.482000] [fglrx] max single GART = 51118080
Jun  4 22:08:10 inspiron kernel: [4305522.482000] [fglrx] total      LFB  = 122834944
Jun  4 22:08:10 inspiron kernel: [4305522.482000] [fglrx] free       LFB  = 104280064
Jun  4 22:08:10 inspiron kernel: [4305522.482000] [fglrx] max single LFB  = 104280064
Jun  4 22:08:10 inspiron kernel: [4305522.482000] [fglrx] total      Inv  = 0
Jun  4 22:08:10 inspiron kernel: [4305522.482000] [fglrx] free       Inv  = 0
Jun  4 22:08:10 inspiron kernel: [4305522.482000] [fglrx] max single Inv  = 0
Jun  4 22:08:10 inspiron kernel: [4305522.482000] [fglrx] total      TIM  = 0
Jun  4 22:08:24 inspiron gconfd (ketil-9654): GConf-tjeneren er ikke i bruk, stenger ned.
Jun  4 22:08:24 inspiron gconfd (ketil-9654): Avslutter
Jun  4 22:36:15 inspiron -- MARK --
Jun  4 22:40:07 inspiron gconfd (ketil-30021): starter (versjon 2.14.0), pid 30021 bruker «ketil»
```

"GConf-tjeneren er ikke i bruk, stenger ned." means "GConf-server is not in use, shutting down"

I have an ATI x300, and have used the howtos found [here]("http://ubuntuforums.org/showthread.php?t=148351") and [here]("http://www.compiz.net/viewtopic.php?id=389").

Does anyone have an idea of what's going on?

- Ketil

---

### Post by pear on 2006-06-27
I am also experiencing this problem with the same video card. This has only happened since Saturday when I installed google earth and within a minute my computer had crashed. Since then when I leave the computer either downloading torrents or just doing nothing for 10 minutes and I come back its crashed. On the last crash my keyboard didn't work but I could still move my mouse although I couldn't click on anything except kwallet. Its all a bit too Windows for me :( 

In the system log get a message saying GConfd is exiting and then another one saying its shutting down.

---

### Post by warsawpact on 2007-01-24
I'm having the same issue although I have a different graphics card an ATI 9700 pro.

Everything was working fine until yesterday although I've only been using Ubuntu for four days.

---

### Post by scarabaeus on 2007-05-08
same here, same graphic card. btw: if your computer crashes after 10 minutes doing nothing, it's the screen saver...

cheers

---


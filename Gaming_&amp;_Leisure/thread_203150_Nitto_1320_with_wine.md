---
title: "Nitto 1320 with wine"
date: 2006-06-24
forum: Gaming &amp; Leisure
---

### Post by CameronCalver on 2006-06-24
Hello when i used to use windows i played a game called Nitto 1320 it is a drag simulator java or shockwave but i still liked it i have got aloto f money and i am on of the richest rivers but this is what happens when i run it in wine 

cameron@ubuntu:~$ cd /home/cameron/Desktop
cameron@ubuntu:~/Desktop$ wine 1320v152s.exe
err:wave: DSDB_MapBuffer Could not map sound device for direct access (Input/outp ut error)
err:wave: DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:wave: DSDB_MapBuffer Could not map sound device for direct access (Input/outp ut error)
err:wave: DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:systray:delete_icon invalid tray icon ID specified: 32517d
fixme:win:SetLayeredWindowAttributes (0x10028,0x00000000,255,2): stub!
err:seh:raise_exception Exception frame is not in stack limits => unable to disp atch exception.
cameron@ubuntu:~/Desktop$

So i run cfg to change it to Emulation and ever time i go to audio it crashes look at the output

cameron@ubuntu:~/Desktop$ winecfg
ALSA lib seq_hw.c:456: (snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/cameron/.kde/socket-ubuntu.
can't create mcop directory
cameron@ubuntu:~/Desktop$


can someone help me because my account will be deleted soon

---


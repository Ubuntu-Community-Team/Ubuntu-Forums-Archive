---
title: "Sound quit working"
date: 2005-10-15
forum: Desktop Environments
---

### Post by mrmcctt on 2005-10-15
Ok I goofed and now I don't know how to fix this.  Sound was working fine but I just had to try to install "Banshee" off the recommendation of a post I saw.  So I did a ```
sudo apt-get install banshee
```

This installed with no errors.  When I tried to start Banshee, it would put a button in the task bar saying it was starting and then just disappear. So I went to synaptic and removed it.  Still no errors.  I used amarok to play some music for a while.

I rebooted my computer a while later and no sound.  I didn't see any errors i the boot up.  I tried to double click on the volume control in the task bar (which has an "x" through it) and got this message ```
No volume control elements and/or devices found.
```

I wen to the sound troubleshooting pages and did an lspci and here's the output: ```
rlodge@ubuntu:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5831 (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5838
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4347 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4348 (rev 01)
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4345 (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4349
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 434d (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5835
0000:02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

```

According to the troubleshooting guide, I can see the manufacturer name for the card so the card is recognized.

The next step was to run alsamixer in a consol.  Here's what I got: ```
rlodge@ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
rlodge@ubuntu:~$

```

Same message whether I ran it with sudo or not.

Any suggestions?  I know this has to be something simple but something I can't find.

Edit:  I tried to restart the alsa-utils like this ```
rlodge@ubuntu:~$ sudo /etc/init.d/alsa-utils restart
```

Here's the message I got:  ```
 * Shutting down ALSA...  * /etc/init.d/alsa-utils: Warning: 'alsactl store' failed with error message 'alsactl: save_state:1163: No soundcards found...'.
                                                                         [fail]
 * Setting up ALSA...  * /etc/init.d/alsa-utils: Warning: 'alsactl restore' failed with error message 'alsactl: load_state:1236: No soundcards found...'.
                                                                         [ ok ]

```

So I guess it isn't seeing the sound card all of a sudden.  The sound device was listed as an atiixp if that helps.

---

### Post by pago on 2005-11-18
hello I've got the same audio controller and have the same problem....no sound, i mean sometimes it works sometimes it doesn't....don't know why....
when I try the volume control I got:


```

No volume control elements and/or devices found. 

```

then if I try 
```

andrea@ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```


and the other command 
```

andrea@ubuntu:~$ sudo /etc/init.d/alsa-utils restart
sudo: /etc/init.d/alsa-utils: command not found

```


If you solved your problem please let me know!
thanks

---

### Post by dev3n on 2005-11-20
i have the same problem as you two guys...i am a totally newbie on linux..so i have no idea how to configure such stuff :D

when i first installed Ubuntu the sound was ok, almost...i could only use my sound card for one program, i could not play a game while listening to music etc...so i was goofing around with settings, and now i have no sound at all.. :\

---

### Post by heimo on 2005-11-21
What happens if you run
```
modprobe -v snd_atiixp
```
and then:
```
lsmod | grep -i snd
```
This should only work if the sound card / chip is "audio part of ATI IXP controller".

---

### Post by SectionThree on 2005-11-21
I get the same problem sometimes, maybe we should report it as a bug...

Anyway, I use the Volume control app (in "Sound and Video" and unmute the headphones.  That always works (until it stops working and then I do it again)

---


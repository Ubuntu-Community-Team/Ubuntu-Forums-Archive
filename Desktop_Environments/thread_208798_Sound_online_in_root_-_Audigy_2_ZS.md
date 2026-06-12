---
title: "Sound online in root - Audigy 2 ZS"
date: 2006-07-04
forum: Desktop Environments
---

### Post by PandorsBox on 2006-07-04
System Specs: AMD64 3000+ with linux-k7 kernel
Sound Card (only one): Creative Audigy 2 ZS
Dual Boot Dapper/Windows XP w/FakeRaid VIA

Problem:  Sound only in root

So far everything else works, just not the sound.  Overall, quite pleased with Ubuntu, but since I can't login as root, I'm forced to have no sound.  Here's some more info:

pan@ubuntu:~$ aplay -l
aplay: device_list:222: no soundcards found...

pan@ubuntu:~$ lspci -v

[edited]

0000:00:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs SB Audigy 2 ZS (SB0350)
        Flags: bus master, medium devsel, latency 32, IRQ 169
        I/O ports at e700 [size=64]
        Capabilities: <available only to root>

[edited]

pan@ubuntu:~$ sudo su
Password:
root@ubuntu:/home/pan# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

root@ubuntu:/home/pan# alsaplayer

(I can play mp3 files, and hear them)

Exactly what file files do I need to chmod to get sound for other users (like, accounts I can actually login with).

Thanks in advance

EDIT: Title should read: Sound only in root.  Guess I'm tired.

---

### Post by mlind on 2006-07-04
is your user on **audio** group?

---

### Post by PandorsBox on 2006-07-04
OMG that works! Haha... didn't even think of that.  

Only thing is, I don't get streaming audio (like from Pandora's website [http://www.pandora.com/)](http://www.pandora.com/)).  Any ideas?

EDIT: I installed Easy Ubuntu so that should handle the codecs right?

---

### Post by mlind on 2006-07-04
[QUOTE=PandorsBox]OMG that works! Haha... didn't even think of that.  

Only thing is, I don't get streaming audio (like from Pandora's website [http://www.pandora.com/)](http://www.pandora.com/)).  Any ideas?

EDIT: I installed Easy Ubuntu so that should handle the codecs right?[/QUOTE]

btw. make sure your user are on these groups too
```

adm dialout fax cdrom floppy tape audio dip video plugdev lpadmin scanner admin

```

plugdev group may or may not exist. You can see your the groups you belong by typing **groups** on terminal.


As for playing streaming web content, see this thread posted earlier [http://www.ubuntuforums.org/showthread.php?t=208251](http://www.ubuntuforums.org/showthread.php?t=208251)
I have no experiences about EasyUbuntu, sorry.

---

### Post by PandorsBox on 2006-07-04
I'm all set with the user groups.  Thanks for your help.  Still no streaming audo from Pandora's website, though.

I tried to reinstall easy ubuntu, but the python script seems to not work anymore.

pan@ubuntu:~/easyubuntu$ sudo python easyubuntu.in

[Nothing happens here, so I CTRL-C]

Traceback (most recent call last):
  File "easyubuntu.in", line 51, in ?
    main()
  File "easyubuntu.in", line 30, in main
    succeeded = detect.system_sanity_check()
  File "/home/pan/easyubuntu/EasyUbuntu/detect.py", line 100, in system_sanity_check
    apt.wait()
  File "/usr/lib/python2.4/subprocess.py", line 1007, in wait
    pid, sts = os.waitpid(self.pid, 0)
KeyboardInterrupt

pan@ubuntu:~/easyubuntu$

---

### Post by mlind on 2006-07-04
[QUOTE=PandorsBox]I'm all set with the user groups.  Thanks for your help.  Still no streaming audo from Pandora's website, though.

I tried to reinstall easy ubuntu, but the python script seems to not work anymore.

pan@ubuntu:~/easyubuntu$ sudo python easyubuntu.in

[Nothing happens here, so I CTRL-C]

Traceback (most recent call last):
  File "easyubuntu.in", line 51, in ?
    main()
  File "easyubuntu.in", line 30, in main
    succeeded = detect.system_sanity_check()
  File "/home/pan/easyubuntu/EasyUbuntu/detect.py", line 100, in system_sanity_check
    apt.wait()
  File "/usr/lib/python2.4/subprocess.py", line 1007, in wait
    pid, sts = os.waitpid(self.pid, 0)
KeyboardInterrupt

pan@ubuntu:~/easyubuntu$[/QUOTE]

I don't know about that. I suggest to remove EasyUbuntu and follow the instructions on that another thread.
I can stream music from that website without problems.

---


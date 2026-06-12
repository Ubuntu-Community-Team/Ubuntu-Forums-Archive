---
title: "Noteedit refuses to start with SIGABRT"
date: 2006-06-27
forum: Desktop Environments
---

### Post by tomane on 2006-06-27
I'm using kubuntu 6.06 and installed noteedit through synaptic. When i try to start noteedit if fails after showing the splash screen; I get a KDE error message telling that noteedit crashed and caused a SIGABRT.
 I don't have gdb installed right now, so I can't provide any backtrace information but I'll try to install it and post some aditional info.

If anyone already had this problem, please share so that I can find what I might be missing here.

--to

---

### Post by tomane on 2006-06-27
Took less than I thought...
Here's the backtrace output:

[FONT=Courier New] > (no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
[this line repeated +/-n30 times]
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1236772000 (LWP 6758 )]
(no debugging symbols found)
[about 15 more times the same message]
(no debugging symbols found)
[KCrash handler]
#6  0xffffe410 in __kernel_vsyscall ()
#7  0xb7bb69a1 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb7bb82b9 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7d94c84 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#10 0xb7d92915 in __gxx_personality_v0 () from /usr/lib/libstdc++.so.6
#11 0xb7d9294a in std::terminate () from /usr/lib/libstdc++.so.6
#12 0xb7d92a7e in __cxa_throw () from /usr/lib/libstdc++.so.6
#13 0xb6b4e2e7 in TSE3::MidiSchedulerFactory::createScheduler ()
   from /usr/lib/libtse3-0.3.1.so
#14 0xb7eb3ce1 in NMidiMapper::NMidiMapper ()
   from /usr/lib/noteedit/libnoteedit.so.1
#15 0x0804a399 in ?? ()
#16 0x0812b818 in ?? ()
#17 0x0804ac9e in vtable for QGList ()
#18 0x00000001 in ?? ()
#19 0xb769fd70 in QColor::color_init () from /usr/lib/libqt-mt.so.3
#20 0x00000000 in ?? ()
[/FONT]

---

### Post by hanspb on 2006-07-04
Same thing happens to me. I'm using Gnome (Ubuntu 6.06), but I have some KDE stuff installed from before, and I would assume Synaptic would take care of missing bits and pieces, but when I start Noteedit from console I get messages about KDE things missing. It worked in Breezy, though.:confused:

---

### Post by Oreo on 2006-08-08
Has anyone figured out this problem?
I have the same experience: Just a splash screen.
I've never used Noteedit before.
Is it worth trying to overcome this problem?
Should I go with one of the other notation editors out there?

Thanks,
Oreo

---

### Post by Oreo on 2006-08-19
Someone help please!
Oreo

---

### Post by gms4175 on 2006-10-03
I have had the same problem and would love to get to the bottom of this.

I have Ubuntu 6.06 and have, on a test system installed KDE over the top so I can start in KDE or Gnome, but I get the same thing.  Starting from the terminal with "sudo noteedit" gives the folling messages:

cczgms@GARY1:~$ sudo noteedit
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Creating link /root/socket-GARY1.
Created link from "/root/socket-GARY1" to "/tmp/ksocket-root"
/usr/bin/iceauth:  creating new authority file /root/.ICEauthority
Creating link /root/tmp-GARY1.
Created link from "/root/tmp-GARY1" to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Creating link /root/cache-GARY1.
Created link from "/root/cache-GARY1" to "/var/tmp/kdecache-root"
kio (KSycoca): ERROR: No database available!
LilyPond check: found version: 2.6.3
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
TSE3: Alsa scheduler error. Couldn't open sequencer
      (No such file or directory)
terminate called after throwing an instance of 'TSE3::MidiSchedulerError'
  what():  Failed to create the MIDI scheduler
KCrash: Application 'noteedit' crashing...
Warning: connect() failed: : No such file or directory
KCrash cannot reach kdeinit, launching directly.

Any help would be greatly appreciated as I am fairly new to Linux and this means bugger all to me, but I'm willing to learn . . . . . 

I am only really interested in the notation side and don't want to use midi stuff at all just compose and print.

Thanks,

Gary

---

### Post by Belohin on 2006-10-09
Hello, folks!

I had the same error message.
The problem is that the sequencer device is missing (some leak in installation scripts).

My solve:

in the /etc/modprobe.d/alsa-base file there is a section

# Cause optional modules to be loaded above sound card driver modules

Here I have made such a row:
install snd_ens1371 modprobe --ignore-install snd_ens1371 $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

The snd_ens1371 is the module for MY SOUNDCARD! Everyone has to find the adequate one to her/his soundcard.

Such way the noteedit starts successfully.

---

### Post by rpm13 on 2006-10-15
Tried the above (in my case the sound card found from lspci was snd_intel8x0)

It did not work

Then found rosegarden was also complaining and came to the conclusion that its something to do with the sequencer

By doing 
modprobe snd-seq

both (rosegarden and noteedit) now are at least starting.

[Whether they are woking and will do what I want. Well thats another matter ;) ]

---

### Post by dnccnd on 2007-03-01
It is a bit late to join this thread but I am having the same problem now. What you write
> **rpm13 said:**
> By doing 
modprobe snd-seq

both (rosegarden and noteedit) now are at least starting.

do you mean to write that command line in Terminal? I tried that but it didn't work!

---


---
title: "Sound and MIDI problems"
date: 2006-06-04
forum: Desktop Environments
---

### Post by Matthew Bartram on 2006-06-04
I have had problems trying to make the sound work properly on my computer.

My sound card is a Trident Microsystems 4DWave DX according to device manager.

Dapper seems to have fixed some problems, and midi seems to be my problem now.

Wine appears to work now, but if I run winecfg, and select the audio tab, wine config exits.

"NoteWorthy Composer", under wine, tells me that:
        "The following play devices failed to open properly: wine midi mapper"
and does not give me any other midi options

The default sound setup for midi in "GNU Solfege" (a music program) is to use device /dev/sequencer2, and gives this error message:
[INDENT]The sound init failed: 
    [Errno 2] No such file or directory: '/dev/sequencer2'
You should configure sound from the 'Sound' page of the preferences window.

It is also possible that the OS sound setup is incorrect.[/INDENT]

Selecting "Use external midi player", and clicking "apply changes and play test sound" yields a very coarse sound, which continues until I use the system monitor to close timidity

from terminal, "lsmod |grep midi" gives
[INDENT]snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  2 snd_trident,snd_rawmidi
snd                    55268  14 snd_trident,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device[/INDENT]

Nautilus does not know what program to use for midi, but I installed playmidi
The following ensued:
[INDENT]~$ playmidi /Windows/E/Matthew/Like.mid
Playmidi 2.4 Copyright (C) 1994-1997 Nathan I. Laredo, AWE32 by Takashi Iwai
This is free software with ABSOLUTELY NO WARRANTY.
For details please see the file COPYING.
open /dev/sequencer: No such file or directory[/INDENT]

NoteEdit, a music composition program for kde, crashed. So I ran from terminal, giving this output:
[INDENT]X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Creating link /home/mpbartram/.kde/socket-Dell.
Created link from "/home/mpbartram/.kde/socket-Dell" to "/tmp/ksocket-mpbartram"Link points to "/tmp/kde-mpbartram"
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
kbuildsycoca running...
Reusing existing ksycoca
LilyPond check: not available.
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
TSE3: Alsa scheduler error. Couldn't open sequencer
      (No such file or directory)
terminate called after throwing an instance of 'TSE3::MidiSchedulerError'
  what():  Failed to create the MIDI scheduler
KCrash: Application 'noteedit' crashing...
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device[/INDENT]

I'm not sure what to do next. /dev/sequencer (and /dev/sequencer2) seem to be part of the problem, but presumably simply creating the directory will not fix the problem.

---

### Post by Coomkeen on 2006-10-10
I have the same problem with Wine and Noteworthy Composer,
Anyone got any ideas?

---

### Post by LeslieL on 2006-11-01
I have been sweating blood trying to get Noteworthy Composer to play. I had it working under Dapper and forgot what I'd done when I installed Edgy. Today I've got it working again.
[URL="https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo"]
This HOWTO[/URL] gives you everything you need. But even after I'd done all that I couldn't make it work - not until I went into NWC and made sure  Timidity port 0 and Timidity port 1 were listed as the devices used by playback (Tools > Options > Midi) and also that one of these ports was specified as the playback device for each staff (Staff > Staff properties, or F2). 

[This thread]("http://my.noteworthysoftware.com/?topic=4606.0") on the Noteworthy Composer forum might help.

---

### Post by LeslieL on 2006-12-02
Update: I went to Edgy and then downgraded back to Dapper (problems with OpenOffice.org). I hadn't done a good enough backup before going to Edgy so had to set up my midi again, and what I thought I'd done before didn't work. But this howto did it for me: [http://www.ubuntuforums.org/showthread.php?t=58859&highlight=midi](http://www.ubuntuforums.org/showthread.php?t=58859&highlight=midi)

These forums are great.

---


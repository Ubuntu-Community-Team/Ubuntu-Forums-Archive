---
title: "Guitart Pro 4 / wine"
date: 2005-12-11
forum: General Help
---

### Post by almostlinux on 2005-12-11
I tried running Guitar Pro 4 with wine (the latest version 0.9.3)
```

wine GP4.exe

```

Everything works fine but the sound ... I'm not able to hear anything

I don't have any problems with the sound though (in the main OS)

Just wondering what the problem could be ... :confused: 

do i have to use extra switches? as in wine GP4.exe --<something> ?

my sound card is Intel HD onboard audio

---

### Post by Bachstelze on 2005-12-11
GP4 uses MIDI. Make sure you installed Timidity.

---

### Post by almostlinux on 2005-12-17
i got timidity installed...

this might sound stupid .. but how do i play a midi file with it?

i did timidity <midifile> and i get this output and i hear no sound 

```

pradeep@home:~/OperaDownloads$ timidity the_x_files.mid
/etc/sounds/Unison.sf2: No such file or directory
Can't open soundfont file /etc/sounds/Unison.sf2
Playing the_x_files.mid
MIDI file: the_x_files.mid
Format: 1  Tracks: 24  Divisions: 120
Track name: Eerie sound
Track name: Eerie sound echo #1
Track name: Eerie sound echo #2
Track name: Eerie sound echo #3
Track name: Piano
Track name: Piano #1
Track name: Piano #2
Track name: Piano #3
Track name: Whistle
Track name: Background hum
Track name: Click sound
Track name: Click sound echo #1
Track name: Click sound echo #2
Track name: Drum boom
Track name: Noise
Track name: Big drum
Track name: 2nd Whistle
Track name: 2nd background hum
Track name: "X-Files" TV Theme Song
Track name: Frank Perreault
Track name: frankp@mv.mv.com
Track name: modified: andy@osea.demon.co.uk
No instrument mapped to tone bank 0, program 0 - this instrument will not be heard
No instrument mapped to tone bank 0, program 47 - this instrument will not be heard
No instrument mapped to tone bank 0, program 51 - this instrument will not be heard
No instrument mapped to tone bank 0, program 54 - this instrument will not be heard
No instrument mapped to tone bank 0, program 78 - this instrument will not be heard
No instrument mapped to tone bank 0, program 122 - this instrument will not be heard
No instrument mapped to drum set 0, program 32 - this instrument will not be heard
No instrument mapped to drum set 0, program 36 - this instrument will not be heard
No instrument mapped to drum set 0, program 41 - this instrument will not be heard
No instrument mapped to drum set 0, program 43 - this instrument will not be heard
No instrument mapped to drum set 0, program 45 - this instrument will not be heard
No pre-resampling cache hit
Last 11 MIDI events are ignored
Playing time: ~45 seconds
Notes cut: 0
Notes lost totally: 0


```

---

### Post by fdimmling on 2005-12-17
Do you have installed freepats too? You need a patch set for timidity to play and it must be configured in something like /etc/timidity/timidity.cfg. If you install freepats from the repositories configuration is done automatically.
I would be interested in reports on Guitar Pro running in wine (or Band In A Box in wine).

Friedrich

---


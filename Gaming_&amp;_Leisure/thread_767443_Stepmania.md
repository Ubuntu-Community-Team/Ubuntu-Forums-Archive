---
title: "Stepmania"
date: 2008-04-25
forum: Gaming &amp; Leisure
---

### Post by moribalkin on 2008-04-25
Hey, how's it going. I installed Stepmania 3.9 on wine for windows, and everything is fine except for the sound on the music. When ever i enter music selection I can't hear the music basically. Any libs I need to get for audio?

```
00:00.008: StepMania 3.9
00:00.008: Compiled Thu Oct 27 20:13:46 2005 (build 30756)
00:00.010: Log starting 2008-04-25 20:14:35
00:00.010:  
00:00.012: Reading 'Data/Defaults.ini' failed: No such file or directory
00:00.014: Reading 'Data/Static.ini' failed: No such file or directory
00:00.086: Loading window: win32
00:00.112: Windows 5.0 (Win2000) build 2195 [Service Pack 4]
00:00.112: Memory: 1001mb total, 2047mb swap (1556mb swap avail)
/////////////////////////////////////////
00:00.118: WARNING: RegOpenKeyEx(-2147483646,SYSTEM\CurrentControlSet\Control\Class\{4D36E968-E325-11CE-BFC1-08002BE10318}) error (File not found)
/////////////////////////////////////////
/////////////////////////////////////////
00:00.118: WARNING: GetVideoDriverInfo error: no cards found!
/////////////////////////////////////////
00:00.118: Primary display driver: X11 Windowing System
/////////////////////////////////////////
00:00.118: WARNING: Couldn't find primary display driver; logging all drivers
/////////////////////////////////////////
00:00.119: Drive: "TSSTcorpCD/DVDW TS-H552BGA0" Driver: WINE SCS DMA: N/A
00:00.119: Drive: "LITE-ON CD-ROM LTN-4891SNGS" Driver: WINE SCS DMA: N/A
00:00.119: Drive: "ATA     ST3250823AS     3.0" Driver: WINE SCS DMA: N/A
00:00.122: Drive: "Generic USB SD Reader   1.0" Driver: WINE SCS DMA: N/A
00:00.122: Drive: "Generic USB CF Reader   1.0" Driver: WINE SCS DMA: N/A
00:00.122: Drive: "Generic USB SM Reader   1.0" Driver: WINE SCS DMA: N/A
00:00.122: Drive: "Generic USB MS Reader   1.0" Driver: WINE SCS DMA: N/A
00:00.123: AnnouncerManager::AnnouncerManager()
00:00.123: Reading 'Data/Static.ini' failed: No such file or directory
00:00.125: ThemeManager::SwitchThemeAndLanguage: "Trance Machina - Zen Rebirth", ""
00:00.204: Initializing driver: DirectSound
00:00.204: Couldn't load driver DirectSound: DirectSoundCreate (DSERR_NODRIVER)
00:00.204: Initializing driver: DirectSound-sw
00:00.206: Mixing 0.000000 ahead in 0 Mix() calls
00:00.206: Couldn't load driver DirectSound-sw: DirectSoundCreate (DSERR_NODRIVER)
00:00.206: Initializing driver: WaveOut
00:00.206: Mixing 0.000000 ahead in 0 Mix() calls
00:00.206: Couldn't load driver WaveOut: waveOutOpen failed(The specified format is not supported or cannot be translated. Use the Capabilities function to determine the supported formats)
00:00.206: 
00:00.206: //////////////////////////////////////////////////////
00:00.206: Exception: Couldn't find a sound driver that works
00:00.206: //////////////////////////////////////////////////////
00:00.206: 
00:00.206: Language: english
00:00.206: Theme: Trance Machina - Zen Rebirth

```
Now an error

---

### Post by bazzawill on 2008-04-26
did you install the window version under wine because there is a linux version that works great

---

### Post by n00d1ek1ng on 2008-04-29
> **bazzawill said:**
> did you install the window version under wine because there is a linux version that works great

can u post a tutorial? i can't get it to work....

---

### Post by bazzawill on 2008-04-30
1. Download the linux binary from [here]("http://www.stepmania.com/download.php?file=downloads/StepMania-3.9a-linux.tar.gz")
2. Extract to an appropriate directory in your home directory
3. Download songs from[here]("http://www.stepmania.com/wiki/Download_Songs")
4. Extract into stepmania/songs
5. Double click on stepmania executable in directory
5. You can create a desktop launcher or menu launcher pointing to stepmania executable

---

### Post by tyeo098 on 2010-01-24
> **bazzawill said:**
> 1. Download the linux binary from [here]("http://www.stepmania.com/download.php?file=downloads/StepMania-3.9a-linux.tar.gz")
2. Extract to an appropriate directory in your home directory
3. Download songs from[here]("http://www.stepmania.com/wiki/Download_Songs")
4. Extract into stepmania/songs
5. Double click on stepmania executable in directory
5. You can create a desktop launcher or menu launcher pointing to stepmania executable

I have the orignial problem as OP, and the Linux ver. crashes X, i know this is an old post, but i need help ><

---

### Post by s0cket93 on 2010-08-31
what if it doesn't crash?it doesn't run at all! I've downloaded binaries from official website and when I try to run executable it just doesn't do ANYTHING...

EDIT: and the only way to run it so far is to run windows version.but again,native version would be better...

---

### Post by tyeo098 on 2010-08-31
I found a way to make it work.
In ubuntu software center, install the wine BETA.
Ive done this on like 30 computers and it works each time.

EDIT: To run the windows version in ubuntu.
Works flawlessly

---

### Post by s0cket93 on 2010-08-31
It would work for me,but I have no sound when I run it in Wine.So when it starts a song it just stays idle :( (not frozen)

---

### Post by tyeo098 on 2010-08-31
The beta fixes that

---

### Post by s0cket93 on 2010-09-01
No worries,I've fixed the sound issue(selected sound hardware acceleration to 'emulation' in wine settings).

---


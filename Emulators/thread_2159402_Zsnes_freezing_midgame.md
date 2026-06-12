---
title: "Zsnes freezing midgame"
date: 2013-07-03
forum: Emulators
---

### Post by Stafngrimr on 2013-07-03
Having this odd problem and I can't really locate the problem. Zsnes will freeze after having a game open for a certain amount of time... this usually lasts a little while. Perhaps half an hour, though I've not timed it. It happens whatever game I'm playing and there isn't really a single point in any game where it reoccurs. Just seems to be more about having the game open for a certain amount of time. I've tried a few games, as I said, but I've also worked a couple of workarounds of the issue that although make games playable isn't really making the experience enjoyable. Basically I just save the games and then close and restart Zsnes which stops it from happening.

Not really sure what else to include, except that I'm running the most recent version of Zsnes on raring. I do use a PS3 controller with it, using jstest which all works fine and havn't really encountered any of the sound issues like some others have.

Anyone else encountering the same problems, or have any ideas on where else I should look?

---

### Post by neoxone on 2013-07-19
I've got the same issue as you. It freezes midgame and then I have to kill the process.

I'm using nvidia experimental binary xorg driver 319 from and an Xbox controller type S (replaced with USB connector). I don't know if it could be related. What about you?

zsnes config dump

```
; PSR-produced config file (stock default in CAPS)

; Note, if you're worried you messed up a setting, removing the line will have
; ZSNES use the default settings for that option.
; The next time ZSNES is run, the line will reappear with the default settings.

;  ----
; -- Input --
;  ----

; For other input settings see zinput.cfg

; Enable Game-Specific Key Combos (0 = NO, 1 = Yes)
GUIComboGameSpec=0

; Enable Game-Specific Key Input (0 = NO, 1 = Yes)
GameSpecificInput=0

;  ----
; -- Options --
;  ----

; Allow MMX Support (0 = No, 1 = YES)
; Disable this only if you actually do NOT have a processor that supports MMX.
; Disabling this option will prevent you from using some of the more advanced
; video/sound filters.
AllowMMX=1

; Enable New Graphics Engine (0 = No, 1 = YES)
; Toggle off when there are graphical problems in the new graphics engine
newengen=1

; Enable Older Graphics Engine Tweak for Mode 2 (0 = NO, 1 = Yes)
; Enable this to see if it helps with rendering problems
; Only works with old graphic engine
bgfixer=0

; Snapshot Format (0 = BMP, 1 = PNG)
ScreenShotFormat=1

; Auto-Patch ROM with IPS (0 = No, 1 = YES)
AutoPatch=1

; Display ROM Info on Load (0 = No, 1 = YES)
DisplayInfo=1

; Log Info About the Last ROM Loaded to rominfo.txt (0 = No, 1 = YES)
RomInfo=1

; Enable FPS Counter when ZSNES is Started (0 = NO, 1 = Yes)
; This option is disabled when manual frameskip is in use.
FPSAtStart=0

; Display Clock (0 = NO, 1 = Yes)
TimerEnable=0

; Change Clock Mode (0 = 24 HOUR, 1 = 12 Hour)
TwelveHourClock=0

; Display Black Box Around Clock (0 = No, 1 = YES)
ClockBox=0

; Use Small Font for Messages (0 = NO, 1 = Yes)
SmallMsgText=0

; Transparent Messages - doesn't work with small font (0 = NO, 1 = Yes)
GUIEnableTransp=0

;  ----
; -- Video --
;  ----

; Video Mode [0..22]
;   0 = 256x224      R WIN     1 = 256x224      R FULL
;   2 = 512x448     DR WIN     3 = 512x448     DR FULL
;   4 = 640x480     DR FULL
;   5 = 256x224    O R WIN     6 = 512x448    ODR WIN
;   7 = 640x480    ODS FULL    8 = 640x480    ODS WIN
;   9 = 640x560    ODR WIN    10 = 768x672    ODR WIN
;  11 = 800x600    ODS FULL   12 = 800x600    ODS WIN
;  13 = 896x784    ODR WIN    14 = 1024x768   ODS FULL
;  15 = 1024x768   ODS WIN    16 = 1024x896   ODR WIN
;  17 = 1280x960   ODS FULL   18 = 1280x1024  ODS FULL
;  19 = 1600x1200  ODS FULL   20 = VARIABLE   ODR WIN
;  21 = VARIABLE   ODS WIN    22 = CUSTOM     OD  FULL
; You need to select the custom video mode and modify CustomResX/Y to properly
; use custom res support.
cvidmode=16
; Last windowed & fullscreen modes (used when alt-tabbing)
PrevWinMode=16
PrevFSMode=18

; Custom Resolution X and Y for Custom Video Modes [256x224..2048x1536]
CustomResX=640
CustomResY=480

; Enable Video Interpolation, Bilinear Filtering (0 = NO, 1 = Yes)
; Bilinear Filtering is compatible with all filters except NTSC.
; Bilinear Filtering replaces Interpolation and is OpenGL only.
; Video Interpolation is compatible with scanlines.
; Blends the neighboring pixels on the screen to eliminate pixelation.
antienab=0
BilinearFilter=0

; Enable NTSC Filter (0 = NO, 1 = Yes)
; Enable Blargg's wonderful NTSC filter which simulates the artifacts of an
; NTSC TV set - it is probably not a good idea to use with TV-out
; Recommended to use a minimum res of 602x448
NTSCFilter=0
; Blend Frames, Refresh Screen (0 = OFF, 1 = On)
; Blend Frames allows smoother transitions between frames for non-60Hz refresh rates.
; Refresh Screen allows the screen to be updated while changing the filter's parameters.
NTSCBlend=0
NTSCRef=0
; NTSC TV Attributes [-100..100]
NTSCHue=0
NTSCSat=0
NTSCCont=0
NTSCBright=0
NTSCSharp=0
NTSCGamma=0
NTSCRes=0
NTSCArt=0
NTSCFringe=0
NTSCBleed=0
NTSCWarp=0

; Enable Kreed's 2x Filters (0 = NONE, 1 = 2xSaI, 2 = Super Eagle, 3 = Super 2xSaI)
; These are Kreed's various 2x filters. They do not exhibit the same level of
; blurring than interpolation/bilinear. MMX support is required.
; This is disabled when other filters are used.
En2xSaI=0

; Use HQ*x Filter (0 = NO, 1 = Yes)
; This is a filter MaxSt has created. These are very CPU intensive filters that
; do very awesome blending to remove the pixelation.
; This is disabled when other filters are used. MMX support is required.
hqFilter=1
; Set HQ*x level [2..4]
; Recommended min resolutions
; HQ2x = 512x448
; HQ3x = 768x672
; HQ4x = 1024x896
hqFilterlevel=2

; Enable Scanlines (0 = NONE, 1 = Full, 2 = 25%, 3 = 50%) - simulate TV scanlines
; This is compatible with interpolation.
scanlines=0

; Enable Grayscale Mode (0 = NO, 1 = Yes) - don't enable this for other than nostalgia
; The whole screen is displayed in monochrome color.
GrayscaleMode=0

; Enable High-Res Mode 7 (0 = NO, 1 = Yes)
; Doubles the internal resolution of the image when Mode 7 is in use
; However this disables most filters, except for interpolation.
; This is only useful in certain games and is not useful in general.
; Requires a minimum res of 512x448
Mode7HiRes16b=1

; Keep 4:3 Ratio (0 = No, 1 = YES)
; This is particularly handy for those that use laptops/LCDs+non 4:3 resolutions.
; This can be used for Variable ODS Windowed and Custom Res OD Fullscreen.
; It is not recommended to enable this while under 298x224.
; Disable this if you want to use the non-standard ratio instead.
Keep4_3Ratio=1

; Set Gamma Level [0..15]
gammalevel=0

;  ----
; -- Sound --
;  ----

; libAO driver to use. Use zsnes --help to see valid list.
; However "auto" (to automatically pick best one), and "sdl" should
; always be available.
libAoDriver="auto"

; Disable SPC Emulation (0 = NO, 1 = Yes)
; Disabling SPC emulation can improve performance, but at the expense of
; emulation accuracy. There will be no sound output and games might crash.
SPCDisable=0

; Enable Sound Emulation (0 = Off, 1 = ON) - disable if you need the performance
; If SPC emulation is disabled, there will be no sound output.
soundon=1

; Enable Stereo Sound (0 = Off, 1 = ON) - disable if you need the performance
StereoSound=1

; Swap Left Audio Channel w/Right (0 = NO, 1 = Yes)
RevStereo=0

; Simulate Surround Sound (0 = NO, 1 = Yes)
; Enable a simulated 2 speaker surround sound effect.
; Do not enable if playing a game that has its own surround sound effects.
; Stereo Sound must be enabled for this to work.
Surround=0

; Sampling Rate: (0 = 8000Hz, 1 = 11025Hz, 2 = 22050Hz, 3 = 44100Hz,
;                            4 = 16000Hz, 5 = 32000Hz, 6 = 48000Hz)
; Using any other sound frequencies other than the default 32000Hz
; is COMPLETELY UNACCEPTABLE in use for sound bug reports.
SoundQuality=5

; Sound Volume Level [0..100]
MusicRelVol=100

; Enable Sound Interpolation (0 = None, 1 = GAUSSIAN, 2 = Cubic, 3 = 8-point)
; Sound interpolation smooths out the waveform of lower frequency sounds.
; Using any other setting other than the default Gaussian interpolation is
; COMPLETELY UNACCEPTABLE in sound bug reports.
SoundInterpType=1

; Enable Low-Pass Filter (0 = NONE, 1 = Simple, 2 = Dynamic, 3 = Hi-quality)
; A low-pass filter improves the bass in the sounds.
; This is useful if you have a Subwoofer.
LowPassFilterType=0

; Disable Echo (0 = NO, 1 = Yes)
; Disables the echo effect in the sound.
EchoDis=0

;  ----
; -- Saves --
;  ----

; Number of Rewind States [0..99]
RewindStates=8
; Delay between rewinds [1..99] - (1 = 200ms, 5 = 1s, 10 = 2s)
RewindFrames=15

; Don't Save SRAM (0 = NO, 1 = Yes)
; Only enable this if you don't want to Save SRAM at any given time.
; This option will make Update SRAM in Real-Time useless.
nosaveSRAM=0

; Update SRAM in Real-Time (0 = NO, 1 = Yes)
; This is useful if you fear something will prevent ZSNES from exiting normally.
; It is required to play games that store important values directly to SRAM.
; ZSNES normally updates SRAM on exit.
; If Don't Save SRAM is enabled, this option is useless.
SRAMSave5Sec=0

; Load SRAM w/Savestates (0 = No, 1 = YES)
; Enable this when you want to use the SRM that is stored within the savestate.
; Warning: You will overwrite the existing SRM that you are currently using.
; It is required to properly use states with games storing important values
; directly in SRM.
SRAMState=1

; Select Latest Save State Slot on Game Load (0 = NO, 1 = Yes)
; Enable this if you want to load the last saved savestate quickly
; (via the load savestate button/GUI option) after loading the game.
LatestSave=0

; Auto Increment State Slot First, then Save State (0 = NO, 1 = Yes)
; Enable this if you have a tendency in saving accidentally to an existing
; savestate.
AutoIncSaveSlot=0

; Save in 10 save block (0 = NO, 1 = Yes)
; This may be handy if you want to save within a block (0-9, 10-19, etc.)
AutoIncSaveSlotBlock=0

; Auto State Save/Load (0 = NO, 1 = Yes) - uses a special state
; Enable this if you wish a special state to be saved on a visit to the GUI.
; This state will automatically be loaded when you load a game.
AutoState=0

; Pause Emulation After Loading a Save State (0 = NO, 1 = Yes)
PauseLoad=0
; Pause Emulation After Using Rewind (0 = NO, 1 = Yes)
PauseRewind=0

;  ----
; -- Emulation --
;  ----

; Percent to Execute [50..150] - only modify if you know what you are doing
; Changing this value may help certain games run.
per2exec=100

; Disable Hacks (0 = NO, 1 = Yes)
; Set this to 1 if you want to disable game specific hacks
HacksDisable=0

; Frameskip: [0..10] (0 = AUTO, 1-10 = Manual 0-9)
frameskip=0

; Max Frameskip Allowed for Auto Frameskip [0..9]
maxskip=9

; Fastforward/Slowdown Keys Behaviour (0 = HELD, 1 = Toggle)
FastFwdToggle=0
; Fastforward/Slowdown Factors [0..28] (0 = factor 2, 28 = factor 30)
FFRatio=18
SDRatio=0

; Emulation Speed Throttle [0..58] (0 = speed/30, 29 = 1x, 58 = 30x)
; Fast-forward multiplicator is currently inaccurate
EmuSpeed=29

;  ----
; -- Paths --
;  ----
; It is suggested to go to GUI->Paths and modify the paths from there.
; ROMs directory
ROMPath="/home/bruno/SNES"
; Save states & SRAMs, snapshots, SPCs
SRAMPath=""
SnapPath=""
SPCPath=""
; BIOS/base carts (BS-X, Sufami Turbo, Same Game & SD Gundam G-Next)
BSXPath=""
STPath=""
SGPath=""
GNextPath=""
; SPC7110 graphic packs
FEOEZPath=""
SJNSPath=""
MDHPath=""
SPL4Path=""

;  ----
; -- GUI --
;  ----

; Disable GUI (0 = NO, 1 = Yes)
guioff=0

; Show All Files in 'Load Game' Menu (0 = NO, 1 = Yes)
showallext=0

; Filename Display Mode (0 = LONG FILENAME, 1 = Internal header name)
GUIloadfntype=0

; Recent games played, you shouldn't edit this manually (8.3 / Paths / LFN)
prevloadiname="Seiken Densetsu 3.smc"\0"g\"   "
prevloaddnamel=0"!    "\"/home/bruno/SNES/"\0":V   "
prevloadfnamel="Seiken Densetsu 3.smc"\0"7V   "

; Freeze Recent Games List (0 = NO, 1 = Yes)
prevlfreeze=0

; Right Mouse Click Enters/Exits GUI (0 = NO, 1 = Yes)
GUIRClick=0

; Left Handed Mouse Behavior for GUI (0 = NO SWAP, 1 = Swap)
; (swap left and right buttons)
lhguimouse=0

; Show Mouse Cursor Shadow (0 = No, 1 = YES)
; Displays a shadow under the mouse cursor.
mouseshad=1

; Wrap Mouse Cursor (0 = NO, 1 = Yes)
; If enabled, the cursor will wrap around to the other side.
; Only useful for Fullscreen modes.
mousewrap=0

; ESC to Game Menu (0 = No, 1 = YES)
; If yes, visiting the GUI will have the Game Menu automatically selected.
; It will also enable the main menu keyboard shortcuts.
esctomenu=1

; Control the GUI Using Gamepad 1 (0 = NO, 1 = Yes)
JoyPad1Move=0

; Filter GUI Display (0 = No, 1 = YES)
; If enabled, the current filter you are using will also filter the GUI.
FilteredGUI=1

; Use Custom Font (0 = NO, 1 = Yes)
; The font currently reads off a format as defined by zfile.txt
newfont=0

; Save GUI Window Positions (0 = NO, 1 = Yes)
savewinpos=0

; GUI windows X/Y coordinates - GUI setup showing windows #

;    Game          Config        Cheat      Netplay       Misc
; -------------------------------------------------------------------
;  1:Load         3:Input      7:Add Code  [Internet]   9:Misc Keys
;    Run          -------      7:Browse                10:GUI Opts
; 12:Reset       17:Devices   13:Search                15:Movie Opt
;  -------       18:Chip Cfg                           16:Key Comb.
; 14:Save State   -------                                 Save Cfg
;  2:Open State   4:Options                             -------
; 14:Pick State   5:Video                              11:About
;  -------        6:Sound
;    Quit        19:Paths
;                20:Saves
;                21:Speed

; X positions [-233..254] (windows #0 to #22)
GUIwinposx=0,6,65,33,42,5,34,6,64,8,5,33,56,64,56,5,3,28,48,6,28,53,0
; Y positions [8..221] (windows #0 to #22)
GUIwinposy=0,20,70,20,20,20,20,20,30,30,20,20,60,30,60,20,20,60,60,20,30,20,0

; GUI Background Effect
; (0 = NONE, 1 = Snow, 2 = Water A, 3 = Water B, 4 = Burn, 5 = Smoke)
GUIEffect=2

; GUI Palette Mods:
; Background RGB Tint [0..31]
GUIRAdd=15
GUIGAdd=10
GUIBAdd=31
; Titlebar RGB Tint [0..31]
GUITRAdd=0
GUITGAdd=10
GUITBAdd=31
; Windows RGB Tint [0..31]
GUIWRAdd=8
GUIWGAdd=8
GUIWBAdd=25

;  ----
; -- Cheats --
;  ----

; Autoload .CHT files (0 = NO, 1 = Yes)
; Enable the use of stored cheat files on load.
AutoLoadCht=0

; Selected Size Search (0 = 1 BYTE, 1 = 2B, 2 = 3B, 3 = 4B)
CheatSrcByteSize=0

; Selected Numerical Base (0 = DECIMAL, 1 = Hexadecimal)
CheatSrcByteBase=0

; Search Type (0 = EXACT VALUE, 1 = Comparative)
CheatSrcSearchType=0

; Add Code for Most Significant Byte Only (0 = NO, 1 = Yes)
CheatUpperByteOnly=0

;  ----
; -- Movies --
;  ----

; For other input settings see zmovie.cfg

; Display Movie Frame # During Record/Replay (0 = NO, 1 = Yes)
MovieDisplayFrame=0

; Movie Default Start Method (0 = NOW, 1 = Power-On,
;                             2 = Reset, 3 = Power-On without SRAM)
MovieStartMethod=0

; Switch Modes when Loading a Movie State (0 = NO, 1 = Switch to Record, 2 = Switch to Playback)
MZTForceRTR=0

; ZMV -> AVI Conversion Mode: (0 = No Video, 1 = Raw Video, 2 = Ffv1, 3 = x264,
;                              4 = XVID, 5 = Custom)
; The compression codecs can only be used if you provide them yourself.
; See zmovie.cfg for details.
MovieVideoMode=4

; Dump Audio Along w/Video (0 = No, 1 = YES)
MovieAudio=1

; Compress Audio Stream On-The-Fly (0 = No, 1 = YES)
; The compression codecs can only be used if you provide them yourself.
; See zmovie.cfg for details.
MovieAudioCompress=1

; Merge Audio and Video Streams Upon Conversion End (0 = No, 1 = YES)
MovieVideoAudio=1

;  ----
; -- Keyboard Hotkeys --
;  ----
; (you shouldn't edit these directly unless you know what you're doing)

; Super Scope Keys:
; Extra Device in Port 1/2 Cycle
KeyExtraEnab1=0
KeyExtraEnab2=0

; State Keys:
; Save State / Select Slot Menu / Load State
KeySaveState=276
KeyStateSelct=61
KeyLoadState=277
; Increase / Decrease Slot # / Direct Slot # Select
KeyIncStateSlot=0
KeyDecStateSlot=0
KeyStateSlc0=0
KeyStateSlc1=0
KeyStateSlc2=0
KeyStateSlc3=0
KeyStateSlc4=0
KeyStateSlc5=0
KeyStateSlc6=0
KeyStateSlc7=0
KeyStateSlc8=0
KeyStateSlc9=0
; Rewind
KeyRewind=0

; Speed Keys:
; Fast-Forward, Slow-Motion
KeyFastFrwrd=53
KeySlowDown=0
; Frame Rate Up/Down (Manual Frameskip)
KeyFRateUp=0
KeyFRateDown=0
; Speed Throttle Up/Down/Reset to Normal (Auto Frameskip)
KeyEmuSpeedUp=0
KeyEmuSpeedDown=0
KeyResetSpeed=0

; Pause Emulation, Frame Advance Keys
EMUPauseKey=25
INCRFrameKey=0

; Shortcuts:
; BG 0-3, Sprite Layer Display Toggles
KeyBGDisble0=2
KeyBGDisble1=3
KeyBGDisble2=4
KeyBGDisble3=5
KeySprDisble=6

; Sound Channel 0-7 Output Toggles
KeyDisableSC0=63
KeyDisableSC1=64
KeyDisableSC2=65
KeyDisableSC3=66
KeyDisableSC4=67
KeyDisableSC5=68
KeyDisableSC6=87
KeyDisableSC7=88

; Sound Volume Up/Down
KeyVolUp=0
KeyVolDown=0

; Quit ZSNES / Load Menu / Reset Game / Panic Key
KeyQuickExit=0
KeyQuickLoad=0
KeyQuickRst=0
KeyResetAll=7

; Clock Display Toggle
KeyQuickClock=0

; Netplay In-Game Chat
KeyQuickChat=20

; Screenshot Hotkey
KeyQuickSnapShot=0

; Capture SPC Hotkey
KeyQuickSaveSPC=0

; Use Player 3/4 Input as Player 1/2's Toggle
KeyUsePlayer1234=0

; FPS Display Toggle
KeyDisplayFPS=0

; Laptop Battery Display Toggle
KeyDisplayBatt=0

; Video Engine: Old/New Graphic Engine | Windowing | Offset Effects Toggles
KeyNewGfxSwt=9
KeyWinDisble=10
KeyOffsetMSw=11

; Gamma Correction Up/Down
KeyIncreaseGamma=0
KeyDecreaseGamma=0

; Movie Chapters: Insert / Go to Previous / Go to Next
KeyInsrtChap=0
KeyPrevChap=0
KeyNextChap=0

; Movie state load mode cycle
KeyRTRCycle=0

;  ----
; -- Misc --
;  ----

; Calculated Checksum & Hash: Don't Edit by Hand !
TimeChecker=180
PrevBuildNum=0

; Display First-Time Use Reminder (0 = YES, 1 = No)
FirstTimeData=1

; Enable Debugger (0 = NO, 1 = Yes)
debuggeron=0

; Prevent ZSNES from Saving the Configuration on Exit (0 = NO, 1 = Yes)
cfgdontsave=0

; - EOF -
```

---

### Post by joemoe1984 on 2013-11-13
Yup I am getting the same effect. I will try it again today to see if it freezes on me. I only play Super Metroid with the PS3 controller using xboxdrv.

Game Froze at the 35:58 minute mark on first test.
Game Froze at the 35:36 minute mark on the second test.

---

### Post by joemoe1984 on 2013-11-14
I just did a third test while playing Super Metroid and got 35:44 minute mark again.

---

### Post by caecus314 on 2013-11-14
I have the same problem.  I'm running ZSNES on 13.10 on an Intel NUC with Haswell using stock Intel drivers, so it doesn't seem to be related to the graphics hardware.  ZNES has frozen on me many times now.  It usually takes about 18 minutes of having the app open.  It doesn't matter whether I've opened a ROM yet or not; the program will freeze just sitting on the menu.  It doesn't seem to matter what resolution or graphics mode I'm running.  There's no helpful output when I run it from the terminal.

Does anybody know what's going on here?  I'm at a loss.

---

### Post by joemoe1984 on 2013-11-15
> **caecus314 said:**
> I have the same problem.  I'm running ZSNES on 13.10 on an Intel NUC with Haswell using stock Intel drivers, so it doesn't seem to be related to the graphics hardware.  ZNES has frozen on me many times now.  It usually takes about 18 minutes of having the app open.  It doesn't matter whether I've opened a ROM yet or not; the program will freeze just sitting on the menu.  It doesn't seem to matter what resolution or graphics mode I'm running.  There's no helpful output when I run it from the terminal.

Does anybody know what's going on here?  I'm at a loss.

I just tested it as well with no game running and it froze as well.

I should also mention that the version I am running is 1.51.

---

### Post by joemoe1984 on 2013-11-17
Out of curiosity what version of Ubuntu is everyone using? I have 13.10 and I tested this on Linux Mint 13 Maya and it works fine. No issues with freezing after a certain mark. Caecus314 pointed out that there are also using 13.10.

---

### Post by MMN-o on 2013-12-04
AMD drivers (free version) and Ubuntu 13.10 here, experiencing a fatal freeze at around 35 minutes.

As it doesn't seem to be graphics (driver) related, maybe audio libs?

The freezing have started appearing since upgrade to 13.10 from 13.04 - no doubt about it.

---

### Post by broadcd on 2014-02-07
I experienced the same issue the other day playing SMB2:Yoshi's Island, froze up after approx half hour.  Has anyone figured out how to fix this bug?  Im running 13.10 Lubuntu with the opensource drivers that came with lubuntu (i think called xorg?), using a PS to USB controller.  Im using an older computer, and znes seems to be the only SNES emulator that doesn't lag heavy for me (snes9x and Bsnes are unusable), so i'd like to get this working properly.

edit: forgot to mention that last night I downloaded the 12.04 package and installed it, it runs fine im not sure if it will make a difference in any way.  I'll post an update once I get around to playing for more than 1/2 hour.

---

### Post by broadcd on 2014-02-10
Update:  yesterday I played yoshi's island for a little over a half hour, then I left it paused in game (emulation still running) for a couple hours and it didn't freeze up.  I was able to unpause and keep playing.  I found that the sound was slightly distorted but my speakers are a bit funky so it could have been them.

I had to lock my version of znes in synaptic package manager so that I wouldn't keep getting bugged to update.  My limited knowledge of linux keeps me from being able to tell what downgrading my znes package from the 13.10 one to the 12.04 changed, the version of Znes seems to be the same since it hasn't been updated since 2007.

---

### Post by paulkilgo on 2014-02-23
I'm running into this problem too. I ran strace on the hung process; looks like it's hung up in some sort of deadlock:

```
futex(0x9851848, FUTEX_WAKE_PRIVATE, 1) = 0
futex(0x9851848, FUTEX_WAKE_PRIVATE, 1) = 0
futex(0x9851848, FUTEX_WAIT_PRIVATE, 2, NULL) = -1 EAGAIN (Resource temporarily unavailable)
futex(0x9851848, FUTEX_WAKE_PRIVATE, 1) = 0
futex(0x9851848, FUTEX_WAKE_PRIVATE, 1) = 0
futex(0x9851848, FUTEX_WAIT_PRIVATE, 2, NULL) = -1 EAGAIN (Resource temporarily unavailable)
...
```

I'm not really familiar with that system call nor how ZSNES uses it but hopefully a package maintainer can help.

---

### Post by paulkilgo on 2014-02-24
I've kept this hung process alive for a while to do a little more  testing. In case you're coming in from a search engine, there's a bug  report for this on LaunchPad at:

[https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/1214241](https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/1214241)

I  don't know that they provide a zsnes package with debug symbols in it, and I didn't have debug symbols for SDL at the time of execution,  but nonetheless through GDB I can see that zsnes is hung up in a call to SDL_SemPost():

```
(gdb) bt
#0  0xf76daec4 in SDL_ThreadID () from /usr/lib/i386-linux-gnu/libSDL-1.2.so.0
#1  0xf7696290 in ?? () from /usr/lib/i386-linux-gnu/libSDL-1.2.so.0
#2  0xf768d46b in SDL_SetError () from /usr/lib/i386-linux-gnu/libSDL-1.2.so.0
#3  0xf76db26a in SDL_SemPost () from /usr/lib/i386-linux-gnu/libSDL-1.2.so.0
#4  0x08303862 in ?? ()
#5  0x08303ae6 in ?? ()
#6  0x083006d1 in ?? ()
```

I checked out the zsnes source code from that project on SourceForge, and there's only two entry points in that code for SDL_SemPost() in `src/linux/sdllink.c`. I don't know if that helps anyone working on the problem, but maybe it will. That code hasn't changed in years officially (maybe 2007? --  I can't remember), so I wonder if it's changes in the sdl1.2 packages or if Debian/Ubuntu introduced a patch for zsnes since 12.04 -- by the responses on this post between 2.2ubuntu5 and bz2-5ubuntu2. I couldn't find Ubuntu's patches for this so I can't elaborate much.

I think SDL is zsnes's preferred method of software rendering so I wonder if switching to alternate means of rendering will avoid the problem.

EDIT:

Well, at least according to ZSNES's video config I was using OpenGL. I guess maybe they are still using SDL's thread management for cross-compatibility.

---

### Post by osirisgothra on 2014-09-01
This has got to be the ???th time I've seen this bug reported. I've worked with this and other versions (up to 14.04 LTS) and they ALL have this bug unresolved. I think the testers and the bug handlers either think 1) Everything is fine because they don't see the problem because they don't spend enough time testing it (needs to be running for 30min+ on the average, idle or not) and/or (this is the one I believe) 2) The problem is too insignifigant and too subtle to fix, and zsnes appears to work 'just fine' on the surface or for any demo of the product. It's like having a cheeseburger with flies in the middle, and only showcasing the outside of the burger... MMMM!!!

PS: Almost forgot this part, yes you are right it IS sdl's fault, in fact it's a library in sdl that got switched out in the 12.10->13.04 cycle, and since then, if you didn't have the foresight to 'freeze' it, you will suffer this problem. They did manage stop it from crashing but now it just freezes up later... not really a fix.

---

### Post by adec2 on 2014-09-02
Why dont you use snes9x-gtk or retroarch? I havent had your problem on Kubuntu 14.04 with zsnes

---

### Post by kanteock on 2014-09-26
i tried higan/bsnes at first, but there were problems with the sound of the games using this emulator, especially in fullscreen-mode (slow and stuttering sound).

zsnes works perfectly for me, except that it crashes during playing a rom after a while. in fullscreen mode, the screen freezes and there's a annoying sound (infinite loop of a short audio sample). there's nothing i can do except from rebooting.

i did a little test today: i wasn't loading any roms at all and the emulator crashed in the main menu in window mode after 36 minutes!

btw, i'm on Linux Mint Debian Edition. i'm using the latest zsnes version (1.51).

**Edit: **i switched to snes9x and it seems to work quite well :p i found a gui for that emulator called snes9x-gtk, my gamepad was recognized, and it runs in fullscreen without any sound problems so far. at first it complained about the missing library libpng14.so.14, and i found a file libpng14-14-1.4.11-2.5.1.i586.rpm in the internet, and then after a simple 

> sudo alien -i libpng14-14-1.4.11-2.5.1.i586.rpm

it worked fine :p so finally everythings ok ;)

---

### Post by sergio-bobillier on 2015-01-01
The bug is still present in Ubuntu 14.04.1 LTS Trusty. zsnes will randomly freeze in mid-game. To avoid loosing saved data I suggest to enable Check SRAM+Save in the Config -> Saves menu. This will make the emulator write the data as soon as the game modify it and not when you exit the emulator (which will never happen if it freezes).

From zsnes docs at SourceForge:
> **SRAM Check+Save**
Normally, ZSNES will write SRAM data to disk when you exit the emulator or exit to the GUI. When this option is enabled, ZSNES will instead write SRAM data shortly after a game modifies it. If you have problems with in-game saves not working correctly, or if you fear something may prevent ZSNES from exiting normally (i.e. crashing), turn this on. The reason this is not enabled by default is because some games use SRAM as working memory instead of for persistent saved games. Since these games constantly modify SRAM, ZSNES would write to the disk every few seconds (if this option is enabled).

---

### Post by michael-piziak on 2015-01-04
> **adec2 said:**
> Why dont you use snes9x-gtk or retroarch? I havent had your problem on Kubuntu 14.04 with zsnes

I've been running Snes9x on my Ubuntu 12.04 box for some time now and it works perfectly.
However, I did try to install and run it on my sisters Ubuntu 14.04 box and it froze.  It also wouldn't work when I upgraded my system to 14.04 lts.
This is one of a few reasons why I went back to and why I'm sticking with 12.04 - have to have my Super Mario games - LOL.

---


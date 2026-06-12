---
title: "DOSBox + MDK = :/"
date: 2007-12-19
forum: Gaming &amp; Leisure
---

### Post by toupeiro on 2007-12-19
This is a plea to classic gamers out there.  MDK is officially [abandonware!]("http://www.abandonia.com/en/downloadgame/346").  Those of you who were into PC gaming back in the day surely must remember how epically cool this game was.  I've been trying to get it to work with DOSBox and the results have been not too pleasant.

The good:

With a little dosbox.conf tweaking, I got the game starting fast and sounding great.  I can get through the opening credits, and through the beginning "flight" down to the level.

The Bad:

DOSbox will crash (segmentation fault) on the loading of the first level every time! :-(

I've tried several different settings, and replacing the dos4gw.exe with the dos32a .exe extender but I get the same results.  I've read, on dosbox's site anyway, that this game should be well supported with the version of dosbox in the repos.  I even tried running a dosbox process as root wondering if it was trying to access something directly that my account didn't have rights to.  I got a segmentation fault at the same exact place (though it took a few seconds longer for some reason)

Here is my dosbox.conf file.  Anyone want to volunteer some time with me to get this great game working on linux through dosbox?

> # This is the configurationfile for DOSBox 0.71.
# Lines starting with a # are commentlines.
# They are used to (briefly) document the effect of each option.

[sdl]
# fullscreen -- Start dosbox directly in fullscreen.
# fulldouble -- Use double buffering in fullscreen.
# fullresolution -- What resolution to use for fullscreen: original or fixed size (e.g. 1024x768).
# windowresolution -- Scale the window to this size IF the output device supports hardware scaling.
# output -- What to use for output: surface,overlay,opengl,openglnb.
# autolock -- Mouse will automatically lock, if you click on the screen.
# sensitiviy -- Mouse sensitivity.
# waitonerror -- Wait before closing the console if dosbox has an error.
# priority -- Priority levels for dosbox: lowest,lower,normal,higher,highest,pause (when not focussed).
#             Second entry behind the comma is for when dosbox is not focused/minimized.
# mapperfile -- File used to load/save the key/event mappings from.
# usescancodes -- Avoid usage of symkeys, might not work on all operating systems.

fullscreen=false
fulldouble=false
fullresolution=1024x768
windowresolution=original
output=opengl
autolock=false
sensitivity=100
waitonerror=true
priority=higher,normal
mapperfile=mapper.txt
usescancodes=true

[dosbox]
# language -- Select another language file.
# memsize -- Amount of memory dosbox has in megabytes.
# machine -- The type of machine tries to emulate:hercules,cga,tandy,pcjr,vga.
# captures -- Directory where things like wave,midi,screenshot get captured.

language=
machine=vga
captures=capture
memsize=32

[render]
# frameskip -- How many frames dosbox skips before drawing one.
# aspect -- Do aspect correction, if your output method doesn't support scaling this can slow things down!.
# scaler -- Scaler used to enlarge/enhance low resolution modes.
#           Supported are none,normal2x,normal3x,advmame2x,advmame3x,hq2x,hq3x,
#                         2xsai,super2xsai,supereagle,advinterp2x,advinterp3x,
#                         tv2x,tv3x,rgb2x,rgb3x,scan2x,scan3x.
#           If forced is appended (like scaler=hq2x forced), the scaler will be used
#           even if the result might not be desired.

frameskip=0
aspect=false
scaler=normal2x

[cpu]
# core -- CPU Core used in emulation: normal,simple.
# cycles -- Amount of instructions dosbox tries to emulate each millisecond.
#           Setting this value too high results in sound dropouts and lags.
#           You can also let DOSBox guess the correct value by setting it to max.
#           The default setting (auto) switches to max if appropriate.
# cycleup   -- Amount of cycles to increase/decrease with keycombo.
# cycledown    Setting it lower than 100 will be a percentage.

core=dynamic
cycles=50000
cycleup=500
cycledown=20

[mixer]
# nosound -- Enable silent mode, sound is still emulated though.
# rate -- Mixer sample rate, setting any devices higher than this will
#         probably lower their sound quality.
# blocksize -- Mixer block size, larger blocks might help sound stuttering
#              but sound will also be more lagged.
# prebuffer -- How many milliseconds of data to keep on top of the blocksize.

nosound=false
rate=22050
blocksize=2048
prebuffer=10

[midi]
# mpu401      -- Type of MPU-401 to emulate: none, uart or intelligent.
# device      -- Device that will receive the MIDI data from MPU-401.
#                This can be default,alsa,oss,win32,coreaudio,none.
# config      -- Special configuration options for the device. In Windows put
#                the id of the device you want to use. See README for details.

mpu401=intelligent
device=default
config=

[sblaster]
# sbtype -- Type of sblaster to emulate:none,sb1,sb2,sbpro1,sbpro2,sb16.
# sbbase,irq,dma,hdma -- The IO/IRQ/DMA/High DMA address of the soundblaster.
# mixer -- Allow the soundblaster mixer to modify the dosbox mixer.
# oplmode -- Type of OPL emulation: auto,cms,opl2,dualopl2,opl3.
#            On auto the mode is determined by sblaster type.
#            All OPL modes are 'Adlib', except for CMS.
# oplrate -- Sample rate of OPL music emulation.

sbtype=sb16
sbbase=220
irq=7
dma=1
hdma=5
mixer=true
oplmode=auto
oplrate=22050

[gus]
# gus -- Enable the Gravis Ultrasound emulation.
# gusbase,irq1,irq2,dma1,dma2 -- The IO/IRQ/DMA addresses of the 
#            Gravis Ultrasound. (Same IRQ's and DMA's are OK.)
# gusrate -- Sample rate of Ultrasound emulation.
# ultradir -- Path to Ultrasound directory.  In this directory
#             there should be a MIDI directory that contains
#             the patch files for GUS playback.  Patch sets used
#             with Timidity should work fine.

gus=true
gusrate=22050
gusbase=240
irq1=5
irq2=5
dma1=3
dma2=3
ultradir=C:\ULTRASND

[speaker]
# pcspeaker -- Enable PC-Speaker emulation.
# pcrate -- Sample rate of the PC-Speaker sound generation.
# tandy -- Enable Tandy Sound System emulation (off,on,auto).
#          For auto Tandysound emulation is present only if machine is set to tandy.
# tandyrate -- Sample rate of the Tandy 3-Voice generation.
# disney -- Enable Disney Sound Source emulation. Covox Voice Master and Speech Thing compatible.

pcspeaker=true
pcrate=22050
tandy=auto
tandyrate=22050
disney=true

[joystick]
# joysticktype -- Type of joystick to emulate: auto (default), none,
#                 2axis (supports two joysticks), 4axis,
#                 fcs (Thrustmaster), ch (CH Flightstick).
#                 none disables joystick emulation.
#                 auto chooses emulation depending on real joystick(s).
# timed -- enable timed intervals for axis. (false is old style behaviour).
# autofire -- continuously fires as long as you keep the button pressed.
# swap34 -- swap the 3rd and the 4th axis. can be useful for certain joysticks.
# buttonwrap -- enable button wrapping at the number of emulated buttons.

joysticktype=auto
timed=true
autofire=false
swap34=false
buttonwrap=true

[serial]
# serial1-4 -- set type of device connected to com port.
#              Can be disabled, dummy, modem, nullmodem, directserial.
#              Additional parameters must be in the same line in the form of
#              parameter:value. Parameter for all types is irq.
#              for directserial: realport (required), rxdelay (optional).
#              for modem: listenport (optional).
#              for nullmodem: server, rxdelay, txdelay, telnet, usedtr,
#                             transparent, port, inhsocket (all optional).
#              Example: serial1=modem listenport:5000

serial1=dummy
serial2=dummy
serial3=disabled
serial4=disabled

[dos]
# xms -- Enable XMS support.
# ems -- Enable EMS support.
# umb -- Enable UMB support.
# keyboardlayout -- Language code of the keyboard layout (or none).

xms=true
ems=true
umb=true
keyboardlayout=none

[ipx]
# ipx -- Enable ipx over UDP/IP emulation.

ipx=false

[autoexec]
# Lines in this section will be run at startup.



---

### Post by Perfect Storm on 2007-12-19
Try with the latest version of dosbox: [http://sourceforge.net/project/downloading.php?groupname=dosbox&filename=dosbox-0.72.tar.gz&use_mirror=dfn](http://sourceforge.net/project/downloading.php?groupname=dosbox&filename=dosbox-0.72.tar.gz&use_mirror=dfn)

guide: [http://gaming.gwos.org/doku.php/guides:dosbox](http://gaming.gwos.org/doku.php/guides:dosbox)

---

### Post by toupeiro on 2007-12-19
> **Artificial Intelligence said:**
> Try with the latest version of dosbox: [http://sourceforge.net/project/downloading.php?groupname=dosbox&filename=dosbox-0.72.tar.gz&use_mirror=dfn](http://sourceforge.net/project/downloading.php?groupname=dosbox&filename=dosbox-0.72.tar.gz&use_mirror=dfn)

guide: [http://gaming.gwos.org/doku.php/guides:dosbox](http://gaming.gwos.org/doku.php/guides:dosbox)

Followed instructions verbatim, still getting the segmentation fault at the same place.  Although, the new version did raise my benchmark score a little. :)

---

### Post by toupeiro on 2007-12-19
Before I dive too much deeper into this, I am running 64-bit 7.10.  Even though "emulation" is sopposed to be transparent, the way these old DOS games wanted direct control of hardware and address space may be my problem.  16 bit protected mode and 64 bit may be too much of a gap even to pass emulation.  I'll continue to try a few more things, but will also pack this up and try it on my 32-bit 7.10 laptop.

---

### Post by zcal on 2007-12-19
> **toupeiro said:**
> MDK is officially [abandonware!]("http://www.abandonia.com/en/downloadgame/346").  

Shiny!

I'll definitely be trying to get it running, though on a 32 bit processor...

---

### Post by zcal on 2007-12-19
I've gotten the game running under DOSBox 0.65, but it's reaallly slow.  I had to CTRL+F12 quite a bit just to get it going, but it's still too slow to be playable.  I'll try with 0.72 next and see what kind of results it gives me.

I did run into some trouble and had to do some forum digging to find a fix.

You might get an error when trying to run the game that references the file MISC\MDKFONT.FTI.  Open up MDK.CFG and find
cddata = c:\mdk
hddata = c:\mdk
You'll want to change these options to MDK's directory.  So, if you did "mount c /home/YOU/mdk" in DOSBox, then just use "c:" for both, since you're technically running the game straight from that drive.

---

### Post by toupeiro on 2007-12-19
> **zcal said:**
> I've gotten the game running under DOSBox 0.65, but it's reaallly slow.  I had to CTRL+F12 quite a bit just to get it going, but it's still too slow to be playable.  I'll try with 0.72 next and see what kind of results it gives me.

I did run into some trouble and had to do some forum digging to find a fix.

You might get an error when trying to run the game that references the file MISC\MDKFONT.FTI.  Open up MDK.CFG and find
cddata = c:\mdk
hddata = c:\mdk
You'll want to change these options to MDK's directory.  So, if you did "mount c /home/YOU/mdk" in DOSBox, then just use "c:" for both, since you're technically running the game straight from that drive.

yeah, I had the config file set correctly.  The game will fail complaining about a .fti file or something if you don't have those set correctly.    Not sure about 0.65, but in 0.71 and 0.72 , I set the core setting from normal to dynamic, and saw a drastic improvement in performance.  --- until the segmentation fault happens that is :-D

---

### Post by zcal on 2007-12-19
I tried setting the core to "dynamic" and the cycles to "auto" (which the config file warns is still experimental, but oh well), and that seemed to work well enough.  The numbers scrolled through more quickly than before on the game's "checking..." screen, but then told me that my machine was running on a 486 or some other processor too weak to handle the game.  I could manually set a high number of cycles, but I'm not sure what my processor can handle...

We'll see what 0.72 does for me once I get it set up.

---

### Post by toupeiro on 2007-12-19
> **zcal said:**
> I tried setting the core to "dynamic" and the cycles to "auto" (which the config file warns is still experimental, but oh well), and that seemed to work well enough.  The numbers scrolled through more quickly than before on the game's "checking..." screen, but then told me that my machine was running on a 486 or some other processor too weak to handle the game.  I could manually set a high number of cycles, but I'm not sure what my processor can handle...

We'll see what 0.72 does for me once I get it set up.


I found the sweetspot on my system for the cycles were between 50,000 and 60,000.  100,000 made the audio glitch some.  Athlon 64 x2 3800 on this box.

---

### Post by zcal on 2007-12-19
> **toupeiro said:**
> Athlon 64 x2 3800 on this box.

Ha!  Mobile Celeron 1.8 ghz.  I suspect that's part of my problem... :-P

---

### Post by zcal on 2007-12-22
Okay, so I compiled DOSBox 0.72 and got the game to run under it.  It even does so without any extra configuration.  But, I experience a good bit of slow down when there's action going on.  This being MDK, that's certainly not a good thing!  It's playable, but not very enjoyably.  I suspect my system's to blame for it...

Any suggestions for speeding things up?  I tried switching the core to dynamic, but it didn't seem to make any difference.

---

### Post by zcal on 2007-12-23
New development...

So changing the core setting to "dynamic" does actually change things.  Apparently I have to restart X to get DOSBox to register with its edited .dosboxrc file.  The dynamic core speeds things up, but way too much.  Everything runs as if in fast forward.

---

### Post by toupeiro on 2007-12-24
You're still in better shape than I am.  While I have not tried it on a 32-bit box yet, I am still getting the same hell on my 64-bit box.  Ran an strace on dosbox, but didn't get anything comprehendable out of it.  at least not for me as far as a root cause.

> read(13, "\202\202\202\202\201\201\201\200\201\203\205\207\207\211"..., 4096) = 4096
read(13, "mpnu\200\207\212\207\202\204\215\232\243\236\223\226\233"..., 4096) = 4096
gettimeofday({1198496242, 645232}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "\201\204\207\207\206\200xsomkmlot{\202\207\207\205\177"..., 4096) = 4096
read(13, "\242\227\221\211\200ricb_UQMNTZ\\ZZYY`lrsohhjo{\210"..., 4096) = 4096
read(13, "\177\200~\177\200\200\203\205\204\200|z}\205\213\215\211"..., 4096) = 4096
read(13, "y{||\201\200|{wsolkloqtxyyxz}~\177~|}\201\203\177|"..., 4096) = 4096
gettimeofday({1198496242, 645929}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "\221\215\177nb^`]\\[TNQXY^ejpofeu\203\222\240\242\227\217"..., 4096) = 4096
read(13, "zyy{}\177\177\177\200\201\203\203\203\204\206\207\210\207"..., 4096) = 4096
read(13, "\232\221\213\210\202~}}tkklmpvyvtvz|{|\177x\177\204\207"..., 4096) = 4096
read(13, "v~\204\206\205\207\207\210\207\203\203\212\214\210}qif"..., 4096) = 4096
gettimeofday({1198496242, 646608}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "\266\263\256\246\231\211\203~ugWNSX[aaUSUVQJXccdflopm"..., 4096) = 4096
read(13, "Ycqsv\200\205\203\206\211\205\202\200\202\212\214\202t"..., 4096) = 4096
read(13, "tspprsssvz|}}|{~\201\200~}~\177\201\204\210\213\216\217"..., 4096) = 4096
read(13, "\226\230\227\217\215\215\217\205xpuy}~}zyzzyrfdcYWXZ`^"..., 4096) = 4096
read(13, "\\[\\gfcmy\211\221\217\212\212\224\244\255\252\246\237"..., 4096) = 4096
gettimeofday({1198496242, 647610}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "{|~\200\202\204\204\206\206\206\204\200\202\210\212\212"..., 4096) = 4096
read(13, "}}\200\205\213\220\221\217\215\220\222\214\206\204\201"..., 4096) = 4096
read(13, "jhgfghhhjnqtz|\200\206\210\211\214\213\211\207\205\207"..., 4096) = 4096
read(13, "mmpuw|\201\201\201\203\203\204\203\202\200~{tpu{\177}v"..., 4096) = 4096
read(13, "ugqzzuiaeegnpt}}~\201\200\203\212\216\216\212\204\207\204"..., 4096) = 4096
gettimeofday({1198496242, 648583}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "sjhmv\203\210\205zsrrxvqsuvyxtqqiflw|ytw|"..., 4096) = 4096
read(13, "\212\212\207\201{xxz|yuuvsv{\177~|{ywz\200\205\211\213"..., 4096) = 4096
read(13, "\233\233\233\225\216\207\201rflttqomlorwx\200\213\216\215"..., 4096) = 4096
read(13, "\234\251\234\234\247\234\224\213\202\221\225\206o\204\225"..., 4096) = 4096
gettimeofday({1198496242, 649245}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "\206\206\205\205\201\177\202\207\204~~}unnrqmknx\201\200"..., 4096) = 4096
read(13, "\216\225\235\225\206}yyy\206\224\223\215\213\220\211\214"..., 4096) = 4096
read(13, "\204\203\203\204\204\205\204\201\201\200\177\177~}}|zz"..., 4096) = 4096
read(13, "\200\200}x{\202\216\223\216\215\215\211\205\177zyz\177"..., 4096) = 4096
gettimeofday({1198496242, 649901}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "\213\204nnutrt{zo[YbgimsoeTVZYekw\202\205\215\227\256"..., 4096) = 4096
read(13, "\202\204\203\201\177\177\200\202\203\203~zwvttxxvvy|}\177"..., 4096) = 4096
read(13, "\233\235\230\220\206\203\201\200\200|qu\203\205\201\202"..., 4096) = 4096
read(13, "u|\212\222\222\215\213\215\222\226\230\231\230\233\236"..., 4096) = 4096
read(13, "w~\210\216\215\213\216\211{zzz\200\202\212\224\212\202"..., 4096) = 4096
gettimeofday({1198496242, 650986}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "\177uyxiesmz\216\223\200r}\201yz}{ndnoZGN[^_efp"..., 4096) = 4096
read(13, "\237\243\247\252\252\252\254\255\257\254\242\232\225\221"..., 4096) = 4096
read(13, "zxy{zzyvvz\202\210\215\222\222\221\221\221\220\220\221"..., 4096) = 4096
read(13, "\204\204\205\203\201\200\202~{\201\201\200\201\202\205"..., 4096) = 4096
read(13, "tswrkhioxxtolpuwpmqxzx~\207\216\224\233\231\221\217\215"..., 4096) = 4096
read(13, "\213\207\224\252\245\230\213\204\210}umpn\\_l~\205\206"..., 4096) = 4096
gettimeofday({1198496242, 652019}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "xz|z}ykcdkoou\177\204\206\204\177vu\177\201zqiffdcekt"..., 4096) = 4096
read(13, "\177\201\204\206\205\202\200}yz}\201\203\203}tpquwttwv"..., 4096) = 4096
read(13, "ty}~\200\205\206\207\211\214\216\216\215\215\215\214\216"..., 4096) = 4096
read(13, "\201\202\204\203}y{~\200\200\200\200}yx|}xtssporx|}\201"..., 4096) = 4096
gettimeofday({1198496242, 652680}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "\207\205{{y{yyuzzqvspw|tu\201\177\202\203\203}\201\211"..., 4096) = 4096
read(13, "\207\211\213\215\213\214\215\213\205\200\200\200|wuuwz"..., 4096) = 4096
read(13, "\202\210\212\207\204\202\177\177\202\202\177\177\200\200"..., 4096) = 4096
read(13, "tuvy|~\177\200~\202\205\205\204\205\207\210\211\211\207"..., 4096) = 4096
gettimeofday({1198496242, 653717}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "xsod^`][``_kw{xutv}\204\206\200yxx|\202\203\177\201}r"..., 4096) = 4096
read(13, "}\200\202\202\205\211\215\220\214\213\213\214\216\210\206"..., 4096) = 4096
read(13, "ouusy\200\203\210\213\217\225\222\212\212\215\206{rmhj"..., 4096) = 4096
read(13, "\212\214\223\221\212\212\205|vutroossvwy|{yy|\200\202~"..., 4096) = 4096
read(13, "dfgkptuttsntx{\200\203\203\201\201\203\204\204\201\200"..., 4096) = 4096
read(13, "\200\202\203\204\206\210\207\206\200xx}\202\207\205\210"..., 4096) = 4096
gettimeofday({1198496242, 663363}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
gettimeofday({1198496242, 663433}, NULL) = 0
gettimeofday({1198496242, 663452}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "vy}~\177\200\177}}zxww|\177\177|xwwxyyyz~\201\206\213\215"..., 4096) = 4096
read(13, "\225\225\227\227\217\216\220\217\205}vrnjelz}|\206\214"..., 4096) = 4096
read(13, "\213\220\221\220\216\213\217\214\200\201ztvrpikrt\201\203"..., 4096) = 4096
read(13, "\213\210\215\217\217\216\212\204\204\213\220\220\220\215"..., 4096) = 4096
gettimeofday({1198496242, 663902}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "\217\212\205\177~\201~wtpjhmu}\203\210\223\235\236\236"..., 4096) = 4096
read(13, "kmw\206\223\225\220\216\215\211\205\215\213\201\210\226"..., 4096) = 4096
read(13, "}z\177\200~unlmkqsrwz|~\202\207\217\227\237\240\240\233"..., 4096) = 4096
read(13, "\223\221\220\216\214\214\213\203}}\177\201}umku\177\205"..., 4096) = 4096
gettimeofday({1198496242, 664356}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "i\202\213|mx|\216\206y|mlz\204\223\250\255\237\234\254"..., 4096) = 4096
read(13, "\203\205\206\203ypnngaadfls{\204\220\230\235\234\230\222"..., 4096) = 4096
read(13, "\201yy{ys~\207\214\216\227\237\250\252\242\235\227\216"..., 4096) = 4096
read(13, "s_v\202}\202\200w|\224\233\230\244\252\231\206\212\212"..., 4096) = 4096
read(13, "\205\210\200\201\177\202\205\210\206~}\202}yy}\200\201"..., 4096) = 4096
gettimeofday({1198496242, 665234}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "\206}y{rwugmnjkkiacp~\203\205\216\226\225\221\214\206\225"..., 4096) = 4096
read(13, "\223\216\212\203}\177\201\202\204\207\205\200~\177\200"..., 4096) = 4096
read(13, "\202\204\206\207\205\200\201\207\214\222\221\207\177\202"..., 4096) = 4096
read(13, "ww~\211\201wpqnbZ^if]V[iy\177{{\203\206\202\206\215\215"..., 4096) = 4096
gettimeofday({1198496242, 665691}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "\202\214\215\211\213\214\227\231\215\212\215\220\217\220"..., 4096) = 4096
read(13, "|\215\232\237\225\225\260\236\212\213\220\230\205\203p"..., 4096) = 4096
read(13, "}\177\200\177xtutplkpsv~\203\204\206\207\203\200\201\201"..., 4096) = 4096
read(13, "hlmpvvw\177\203}wuxx\177\211\214\210\211\213\212\207\204"..., 4096) = 4096
gettimeofday({1198496242, 666222}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "q~oden\177\177x{jkxyx{~gm|\215\233\212\212\215\202zsri"..., 4096) = 4096
read(13, "\201\177\200\202\206\212\215\223\224\220\220\222\221\215"..., 4096) = 4096
read(13, "\215\214\211\207\177st\200\207\205{snt\200\200z{zqnpuy"..., 4096) = 4096
read(13, "\200}\177\200|xyz|\177\202\206\210\210\210\205\207\211"..., 4096) = 4096
read(13, "\212\202\200\210\220\222\225\223\207\203\206\204vthcpm"..., 4096) = 4096
read(13, "\200yswrrxwsos|\211\213\210{xy\200vy{\203\203\200\212\240"..., 4096) = 4096
gettimeofday({1198496242, 667049}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "\207\214\216\224\235\233\221\207\203\202\200zyyvjz\203"..., 4096) = 4096
read(13, "uux|\200\205\202\177~}}z{\200\201\201\177\203\207\205\205"..., 4096) = 4096
read(13, "\203\201\210\213\206\200{u|\201\203\202\206\213\204wsx"..., 4096) = 4096
read(13, "wsr{\201yrr{\201\211\215\217\211\204\200|wv|\201\203\200"..., 4096) = 4096
read(13, "\202\202\201\201\200\177~{wqnmnprv{~\201\202\203\203\204"..., 4096) = 4096
read(13, "vuspnquy~\200}}\202\202\200\177}|zz{|~\201\202\207\214"..., 4096) = 4096
gettimeofday({1198496242, 670436}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "\217\217\211\205\202\204\211\216\217\215\207\200\201\203"..., 4096) = 4096
read(13, "wvwvv{|~\200\202\203\204\201\201\201\203\203\202\200~\200"..., 4096) = 4096
read(13, "\204\207\203ywz\201\204\210\212\206\204\203\204\205\206"..., 4096) = 4096
read(13, "{~\177~{|~\200\201}}}z{~||\177\177\202\202\202\207\207"..., 4096) = 4096
gettimeofday({1198496242, 671109}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "\203\216\221\225\217\207\205\205\213\211\202{tsvxwtpke"..., 4096) = 4096
read(13, "\217\216\216\216\217\222\232\236\234\225\211\204\205\207"..., 4096) = 4096
read(13, "\202\201\200\205\201rnvxty{vtz\177~\200\214\216}w|~}|}"..., 4096) = 4096
gettimeofday({1198496242, 671754}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "\206\201\201\177\200\177yqromnt}\201\205\206\204\206\177"..., 4096) = 4096
read(13, "\207\202|xusnnopqvy{~\177{wussstx}\200~{ywuw"..., 4096) = 4096
read(13, "\212\206\201\213\226\222\220\231\244\245\243\225~x\203"..., 4096) = 4096
read(13, "\204\202\202zuvqu|}xxxropsqwvpv\177\206\220\226\217\210"..., 4096) = 4096
gettimeofday({1198496242, 672428}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "\206\210\204\203\177xpvy\205\216\224\231\230\221\212\211"..., 4096) = 4096
read(13, "{xvwyyvqlmtzzxxz|~\201\205\205\202\200\200\177|yy{\177"..., 4096) = 4096
read(13, "~\205\212\214\211\202wttopuv}\201\204\213\211\206\203\200"..., 4096) = 4096
read(13, "nprv{\200\204\203\201\204\206\206\206\207\213\211\203|"..., 4096) = 4096
gettimeofday({1198496242, 673234}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "w\204\211\210\207\207\207\212\213\210\204\201~|~\200\200"..., 4096) = 4096
read(13, "\247\246\234\224\231\233\213\210\203uqsihf`fjq}\201\213"..., 4096) = 4096
read(13, "\225\215\203yuspquyzxwvwx|~\202\207\215\221\223\224\227"..., 4096) = 4096
read(13, "\214\216\210~wrptty\177\203\204\205\177xsoms\200\213\216"..., 4096) = 4096
gettimeofday({1198496242, 673898}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "\203\206|ld_Zbs\200\204\213\217\211~|z|\210\214\213\215"..., 4096) = 4096
read(13, "mrx{}\200\200\177\201\200\200\203\207\217\226\227\221\220"..., 4096) = 4096
read(13, "\245\246\240\234\224\226\233\221\207\207\214\204~\201{"..., 4096) = 4096
read(13, "\204\205\206\205\204\203\201\201\201\201\202\202\203\203"..., 4096) = 4096
read(13, "\205\204\204\201~|~\177\200\200~}||||{z{|~\202\201\202"..., 4096) = 4096
read(13, "z\221\255\246\222\206\202\210\216yfSXUSYTQVV_^ci~\241\244"..., 4096) = 4096
gettimeofday({1198496242, 675252}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "onruwz}|}|yuw\177\203\201~xrnotx}~~\200\201~}\201\207"..., 4096) = 4096
read(13, "\207\212\217\215\222\220\205\216\216\201\211\200\205\210"..., 4096) = 4096
read(13, "\213\213\206\203\204\204\204\206\207\212\212\206\203\203"..., 4096) = 4096
read(13, "|}\201\203\202\202\177~~\177\200\201\201|ywwwuttx{yxvu"..., 4096) = 4096
read(13, "QWZ\\l|\212\220\222\221\237\245\240\231\226\227\203qgh"..., 4096) = 4096
read(13, "}~||{|\177\200\177}{{zzz{{{{|}\177\200\201\201\200\177"..., 4096) = 4096
gettimeofday({1198496242, 676514}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "uz\201\202\200\200\200\200\200\203\206\206\207\207\203"..., 4096) = 4096
read(13, "\203\205\204\205\207\210\210\206\205\212\216\213\210\210"..., 4096) = 4096
read(13, "MDKDLUX`jsz\202\201\200\214\230\234\242\244\231\223\207"..., 4096) = 4096
read(13, "\213\211\210\210\211\211\211\210\211\214\213\211\211\212"..., 4096) = 4096
gettimeofday({1198496242, 677196}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
read(13, "}z~\205\205\201wvztihfeilr|\204\200}}\215\231\243\263\260"..., 4096) = 4096
read(13, "\204\203\203\202\201\201\200\177\177\177\177~}}~\177\201"..., 4096) = 4096
read(13, "}~}~~~~~~~~~~~~~~~\177~\177~~~\177\200\177~~~~~"..., 4096) = 4096
gettimeofday({1198496242, 678662}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
brk(0x39b4000)                          = 0x39b4000
gettimeofday({1198496242, 681249}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
gettimeofday({1198496242, 682507}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
gettimeofday({1198496242, 693651}, NULL) = 0
select(4, [3], NULL, NULL, {0, 0})      = 0 (Timeout)
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV (core dumped) +++
Process 9818 detached


---

### Post by zcal on 2007-12-24
I'm tempted to try the game with Wine.  The AppDB page just doesn't look so promising...
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7416]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7416")

---


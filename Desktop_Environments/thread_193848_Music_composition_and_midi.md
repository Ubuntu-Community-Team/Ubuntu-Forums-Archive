---
title: "Music composition and midi"
date: 2006-06-10
forum: Desktop Environments
---

### Post by Matthew Bartram on 2006-06-10
In windows, I have used [NoteWorthy Composer]("http://www.noteworthysoftware.com/") for music composition. Now in ubuntu under wine, whilst the program works, the midi doesn't. NoteWorthy detects wine midi mapper as what's available, but then says it's not working.

I have installed NoteEdit as an alternarive, but after showing a splash screen, it crashes and tells me it "caused the signal 6 (SIGABRT) .... an application terminates with a SIGABRT signal when it detects an internal inconstency caused by a bug in the program."

Does anyone have any ideas? All I want is a music compositon & scorewriting program (like NoteWorthy or Sibelius). Although getting NoteWorthy to work (aswell) would be nice because I already have saved NoteWorthy files.

---

### Post by FizDev on 2006-06-10
You could try RoseGarden
```
sudo apt-get install rosegarden
```

---

### Post by Belathor on 2006-06-10
Or try denemo and lilypond. (Denemo is a GUI frontend for lilypond)

---

### Post by Matthew Bartram on 2006-06-10
Firstly: to anyone reading this post, rosegarden is the wrong package to install. I think "rosegarden 4" is the correct one; I just used synaptic (after I found that rosegarden gave me an old version)

Secondly, perhaps it can be sorted out, but rosegarden seems to start and run very slow.

I have had a quick look at rosegarden (I'll probably play around with it some more later) and it looks like it really is "the closest native equivalent to Cubase® for Linux" - so for me the thing to use if I haven't got any manuscript paper (which doesn't need OS compatability :-)). The problem is it's designed as a sequencer, so the scorewriting I find very counter-intuitive and frustrating.

Any other programs? Or suggestions for the first 2?

---

### Post by Matthew Bartram on 2006-06-10
I understood that lilypond is for creating scores only - so will not play back to me what I have written. Also it uses a text interface, so whilst you can get all the details and professional-lookingness, it wouldn't be easy to compose in.

Indeed noteworthy under wine is easier (and works) for typesetting scores, because it uses a manuscript-like interface. (although you can't get such extensive detail and the printed result doesn't look as nice)

Edit: Denemo looks like it might be suitable - I'll try it out

---

### Post by muhkayoh on 2006-06-11
Matthew,

Please post again when you find your best solution.  I'm interested in doing this as well. :D 

Thanks,

Matt Jordan

---

### Post by Matthew Bartram on 2006-06-12
So far I've found that denemo seems to be aimed more as a front end to lilypond than for WYSIWYG music composition, so perhaps not right for me (but might work, if nothing else will)

MuseScore looks like it might be the right sort of thing, but I'll have to compile it - which I'll do once I have more time.

"Brahms is a professional music editor and sequencer, it intends to be for Linux, what CuBase is for MacOS/Windows." So that probably won't do for me either.

But my midi still won't work, so nothing will play back at the moment

---

### Post by Matthew Bartram on 2006-06-30
can anyone tell me how to go about compiling MuseScore?

---

### Post by christhemonkey on 2006-06-30
Do you have midi working fully on your ubuntu box already?

It might be a starting point.


```
aplaymidi -o 
```
Should list all available midi ports.
Then you can do a:
```
aplaymidi -o port:0 file.mid 
```
Replacing port:0 with the output from the 1st command, and file.mid with a real midi file (if you have one!)

---

### Post by Matthew Bartram on 2006-07-02
"aplaymidi -o" returns
```
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Cannot open sequencer - No such file or directory
```

---

### Post by christhemonkey on 2006-07-02
Sounds like you need to do:
```
sudo su
modprobe snd-seq
if grep -q -x snd-seq /etc/modules; \
  then echo && echo "NOTE: snd-seq is already in /etc/modules, no changes needed"; \
  else cp /etc/modules /etc/modules_backup_`date +%Y%m%d%H%M` && echo snd-seq >> /etc/modules; \
fi
exit
```

(quote from [www.ubuntustudio.com](www.ubuntustudio.com) an excellent site for all musicians using ubuntu!)

---

### Post by Matthew Bartram on 2006-07-03
I get told that "NOTE: snd-seq is already in /etc/modules, no changes needed"

"$ aplaymidi -o" now returns:
```
aplaymidi: invalid option -- o
Usage: aplaymidi -p client:port[,...] [-d delay] midifile ...
-h, --help                  this help
-V, --version               print current version
-l, --list                  list all possible output ports
-p, --port=client:port,...  set port(s) to play to
-d, --delay=seconds         delay after song ends
```

---

### Post by Matthew Bartram on 2006-07-03
Thankyou, I think midi is working now :)

---

### Post by Matthew Bartram on 2006-07-03
No, it's not. Whilst GNU Solfege appears to work and use the midi properly, NoteEdit and Noteworthy now freeze the computer.

---

### Post by Matthew Bartram on 2006-07-03
By the way, when I said (3 posts ago) that my terminal returned "NOTE: snd-seq is already in /etc/modules, no changes needed", I think that was after doing it once and not getting a reply. (Or not getting a reply that I noticed)

---

### Post by christhemonkey on 2006-07-03
The first time you run it, that command does not produce any outup on the screen.

So does aplaymidi work if you use the right syntax?  ie;
```
aplaymidi -l 
aplaymidi -p=midi:port amidifile.mid 
```

---

### Post by Matthew Bartram on 2006-07-03
"aplaymidi -l" returns
```
 Port    Client name                      Port name
 62:0    Midi Through                     Midi Through Port-0
 64:0    Trident TRID4DWAVEDX MIDI        Trident TRID4DWAVEDX MIDI
 65:0    Trident 4DWave-DX                Trident 4DWave-DX port 0
 65:1    Trident 4DWave-DX                Trident 4DWave-DX port 1
 65:2    Trident 4DWave-DX                Trident 4DWave-DX port 2
 65:3    Trident 4DWave-DX                Trident 4DWave-DX port 3
```

but "aplaymidi -p 64:0 [midi file]" freezes the computer completely (including ctrl+alt+f1 and ctrl+shift+bksp do not work)

---

### Post by christhemonkey on 2006-07-03
Hmm that does not sound good.  As you can probably guess, it shouldnt be doing that!

From my quick googeling i cant find that listed as a bug anywhere, you may want to file a bugreport in the relevant places if noone else can think of a suggestion.

---

### Post by Matthew Bartram on 2006-07-05
Has any one else had this problem? (If anyone else reads this thread)

I have installed gscore, using the .package file. When I try to run it, it opens 2 windows and closes them before putting the stuff inside them. If I run from terminal I get this output:
```
`Error opening directory '/usr/local/lib/gscore': No such file or directory'

Gscore v 0.0.9, Copyright 2001-2005 Sebastien Y. Tricaud
Gscore comes with ABSOLUTELY NO WARRANTY and is provided AS IS;
This is free software, and you are welcome to redistribute it
under certain conditions;
Please read the file COPYING provided with the program for details.

*** glibc detected *** free(): invalid pointer: 0x0854d720 ***
Aborted
```

Anyone got any ideas?

And can anyone tell me how to go about compiling musescore?

Thanks.

---

### Post by christhemonkey on 2006-07-05
Well you need to install the Qt libraries, jack, fluidsynth, and a couple of other things.
```
sudo apt-get install fluidsynth build-essential qt4-qtconfig jackd qjackctl checkinstall 
```

Then get the source from [here]("http://prdownloads.sourceforge.net/mscore/mscore-0.2.tar.bz2?download"),

decompress it:
```
tar -zxvof mscore-0.2.tar.bz2 
```
change to the folder its in:
```
cd ~/mscore-0.2 
```
Compile it;
```
./configure --prefix=/usr
make 
```
install it:
```
sudo checkinstall 
```
Then enter a description for the package, and with any luck it should work!

Let us know if that does/doesnt work.
I will try following my own instructions tonight and see if it works.

---

### Post by Matthew Bartram on 2006-07-05
E: Couldn't find package jakd

---

### Post by christhemonkey on 2006-07-05
Should be jackd 
Note the 'k' in there.

```
sudo apt-get install jackd 
```

---

### Post by Matthew Bartram on 2006-07-05
Thanks; although I think you meant "Note the 'c' in there" :)

It now tells me, after typing ./configure --prefix=/usr, (a lot of things then ending with) "configure: error: need qt >= 4.0.1" even though I have qt4-qtconfig installed.
Also I wasn't sure whether I had to replace "--prefix=/usr"; I tried both as written, and replacing usr with my user.

---

### Post by christhemonkey on 2006-07-05
Hmm maybe you need to say where the core Qt libraries are installed to.
```
./configure --with-qt-prefix=/usr/lib/ --prefix=/usr 
```

Something like that.
That is assuming that the qt4-qtconfig installed the relevant qt dependencies...

---

### Post by Matthew Bartram on 2006-07-06
```
checking for QT environment variable QTDIR... no
checking for QT includes (/usr/lib//include)... no
checking for QT libraries (/usr/lib//lib)... no
checking for QT moc (/usr/lib//bin/moc)... no
checking for QT uic (/usr/lib//bin/uic)... no
configure: error: need qt >= 4.0.1
```
I tried changing to "--with-qt-prefix=/usr/lib" - without the slash at the end. That removed the double slash, but still the same problem

When compiling with just "./configure --prefix=/usr", the last few lines are
```
checking for QT environment variable QTDIR... no
checking for QT includes (/usr/qt4/include)... no
checking for QT libraries ()... no
checking for QT moc (moc)... no
checking for QT uic (uic)... no
configure: error: need qt >= 4.0.1
```

Also, does it matter that just before that it says ```
checking for X... no

```

---

### Post by christhemonkey on 2006-07-06
I think you need libqt4-dev installed, and then the configure command  set to;
```
sudo apt-get install libqt4-dev
./configure --with-qt-prefix=/usr --prefix=/usr

```

As for the failing to detect X, that is more worrying.
But if it isnt saying its a critical error and continues past it, then i guess it can be ignored for now.

---

### Post by Matthew Bartram on 2006-07-06
It now seems to find x - perhaps that was from telling qt it was in /usr rather than /usr/lib

Also, QT moc and uic are found. Only environment variable QTDIR, includes and libraries remain to be found.

I looked again in synaptic and installed qt4-designer, qt4-dev-tools and lsb-qt4, but these didn't help.

The only things left uninstalled with qt4 in the name are libqt4-debug, libqt4-debug-dev and qt4-doc

---

### Post by christhemonkey on 2006-07-07
Well it seems it is looking for the qt4 libraries in a folder /usr/qt4/include/ so maybe a link to the actual qt4 include directory (/usr/include/qt4)?
```
sudo mkdir /usr/qt4/include
sudo ln -s /usr/include/qt4/* /usr/qt4/include/ 
```

You need to export the QTDIR variable like this:
```
export QTDIR=/usr 
```


(something like that anyway!)

---

### Post by Matthew Bartram on 2006-07-07
No. Still same problem.

Although, the includes and libraries lines of code have changed at some point since my last post with code. Now they are
```
checking for QT includes (/usr/include)... no
checking for QT libraries (/usr/lib)... no
``` and "environment variable QTDIR" is there

So we're getting closer, bit by bit :)...

---

### Post by christhemonkey on 2006-07-07
```
./configure --with-qt-prefix=/usr --with-qt-includes=/usr/include --with-qt-libraries=/usr/lib --prefix=/usr 
```

Haha getting a bit lengthy looking now...

---

### Post by Matthew Bartram on 2006-07-08
No, now environment variable QTDIR has gone

I just tried it without any of the switches, and it worked :)

Now to try the rest...

---

### Post by Matthew Bartram on 2006-07-08
The compilation and install worked :) Now on running "mscore" I am told "The required score font "Emmentaler" cannot be found. Please install font first and then try again"

---

### Post by christhemonkey on 2006-07-08
Hahaha, ok.

To install the font required:
> 
- install font fonts/emmentaler_20.otf:
            The needed score font is not automatically installed. It must
            be done manually.

            (If upgrading from prev. versions of mscore make sure you
             have installed the latest font version)

            - Create the directory /usr/share/fonts/truetype
            - Copy emmentaler_20.otf to /usr/share/fonts/truetype
            - use ttmkfdir to create fonts.scale:
                  ttmkfdir > fonts.scale
            - use mkfontdir to create fonts.dir
                  mkfontdir .
            - tell the x11 server your new font
                  xset fp rehash
            - add "/usr/share/fonts/truetype" to the font search path
              of your X11 server (in /etc/X11/xorg.conf) so the x11 server
              knows about the font on next reboot



---

### Post by Matthew Bartram on 2006-07-08
Where do I get emmentaler_20.otf from in the first place?

And when it says                    "ttmkfdir > fonts.scale" does it mean literally type that in to a terminal?

Sorry, I'm still fairly new to all this, so I don't know how to interpret a lot of these things.

---

### Post by christhemonkey on 2006-07-08
Sorry i didnt explain any of that at all :P

The emmentaler font is included in the source.
```
cd mscore-0.2/fonts/ 
```
An yes i think you do need to type all the commands into a terminal.

---

### Post by Matthew Bartram on 2006-07-13
bash: ttmkfdir: command not found

After mkfontdir, I get output:
Invalid fonts.scale in ./.

---

### Post by christhemonkey on 2006-07-13
Very sorry, forgot to mention;
```
sudo apt-get install ttmkfdir 
```

And then do the:
```
ttmkfdir > fonts.scale
mkfontdir .
xset fp rehash

```

---

### Post by Matthew Bartram on 2006-07-16
Ok, that all seemed to work, but I still get the same error message from MuseScore :-(

---

### Post by christhemonkey on 2006-07-16
Oh. Well.
Did you :
> - add "/usr/share/fonts/truetype" to the font search path
              of your x11 server (in /etc/X11/Xorg.conf) so the x11 server
              knows about the font on next reboot

..?

```
gksudo gedit /etc/X11/xorg.conf 
```
And then add the line
```
/usr/share/fonts/truetype
```
To the section about fonts.

---

### Post by Matthew Bartram on 2006-07-16
Yes. My /etc/X11/xorg.conf now has this section:

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath    "/usr/share/fonts/truetype"
EndSection

Perhaps I need to reboot the whole computer? I'll try.

---

### Post by christhemonkey on 2006-07-16
Yes you do need to reboot.
Or at least restart your Xserver.
```
sudo /etc/init.d/gdm restart 
```

---

### Post by Matthew Bartram on 2006-07-16
I did restart the Xserver. Now I've rebooted. Still the same problem.

---

### Post by christhemonkey on 2006-07-16
What are the contents of the font directory?
```
ls -a /usr/share/fonts/truetype 
```

---

### Post by Matthew Bartram on 2006-07-16
.                  kochi               ttf-dejavu            ttf-mgopen
..                 msttcorefonts       ttf-devanagari-fonts  ttf-oriya-fonts
arphic             openoffice          ttf-gentium           ttf-punjabi-fonts
baekmuk            thai                ttf-gujarati-fonts    ttf-tamil-fonts
emmentaler_20.otf  ttf-arabeyes        ttf-kannada-fonts     ttf-telugu-fonts
fonts.cache-1      ttf-bengali-fonts   ttf-lao
freefont           ttf-bitstream-vera  ttf-malayalam-fonts

---

### Post by christhemonkey on 2006-07-16
Try:
```
cd /usr/share/fonts/truetype
sudo fc-cache -f

```
This updates your font cache, which hopefully will allow the emmentaler font to be used.
If this doesnt work, could you post the output of:
```
cat /var/log/Xorg.0.log 
```

Im sorry that im very hit and miss with the instructions, but i would have compiled and run this program along with you but have no internet on ubuntu at the moment and dont have the patience to download all of the qt libraries and their dependencies!

---

### Post by Matthew Bartram on 2006-07-16
Still didn't work.

I ran mscore from terminal this time. The output is ```
X Error: BadDevice, invalid or uninitialized input device 168
  Extension:    145 (XInputExtension)
  Minor opcode: 3 (X_OpenDevice)
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Extension:    145 (XInputExtension)
  Minor opcode: 3 (X_OpenDevice)
  Resource id:  0x0
Failed to open device
no locale <mscore_en_GB> in </usr/local/share/mscore/locale>
no JACK server found
no ALSA audio found
sequencer init failed
```The output of "cat /var/log/Xorg.0.log" is a bit long, but here it is, in two parts since otherwise the post is too long:```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux R-450 2.6.15-26-386 #1 PREEMPT Fri Jul 7 19:27:00 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 16 18:12:38 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "FUJITSU e178"
(**) |   |-->Device "ATI Technologies, Inc. Rage 128 RF/SG AGP"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/truetype".
        Entry deleted from font path.
        (Run 'mkfontdir' on "/usr/share/fonts/truetype").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.2
        X.Org Video Driver: 0.8
        X.Org XInput driver : 0.5
        X.Org Server Extension : 0.2
        X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,7190 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7191 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 8086,7110 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 8086,7111 card 0000,0000 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:07:2: chip 8086,7112 card 0000,0000 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 8086,7113 card 0000,0000 rev 02 class 06,80,00 hdr 00
(II) PCI: 00:0e:0: chip 1023,2000 card 1023,2000 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:10:0: chip 10ec,8029 card 10b8,2011 rev 00 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 1002,5246 card 1002,0004 rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x008c (VGA_EN is set)
(II) Bus 1 I/O range:
        [0] -1  0       0x00009000 - 0x000090ff (0x100) IX[B]
        [1] -1  0       0x00009400 - 0x000094ff (0x100) IX[B]
        [2] -1  0       0x00009800 - 0x000098ff (0x100) IX[B]
        [3] -1  0       0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xf0100000 - 0xf01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Rage 128 RF/SG AGP rev 0, Mem @ 0xf8000000/26, 0xf0100000/14, I/O @ 0x9000/8
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf4000000 from 0xf7ffffff to 0xf3ffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xf0000000 - 0xf0000fff (0x1000) MX[B]
        [1] -1  0       0xf4000000 - 0xf3ffffff (0x0) MX[B]O
        [2] -1  0       0xf0100000 - 0xf0103fff (0x4000) MX[B](B)
        [3] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [4] -1  0       0x00001040 - 0x0000105f (0x20) IX[B]
        [5] -1  0       0x00001400 - 0x000014ff (0x100) IX[B]
        [6] -1  0       0x00001020 - 0x0000103f (0x20) IX[B]
        [7] -1  0       0x00001000 - 0x0000100f (0x10) IX[B]
        [8] -1  0       0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xf0000000 - 0xf0000fff (0x1000) MX[B]
        [1] -1  0       0xf4000000 - 0xf3ffffff (0x0) MX[B]O
        [2] -1  0       0xf0100000 - 0xf0103fff (0x4000) MX[B](B)
        [3] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [4] -1  0       0x00001040 - 0x0000105f (0x20) IX[B]
        [5] -1  0       0x00001400 - 0x000014ff (0x100) IX[B]
        [6] -1  0       0x00001020 - 0x0000103f (0x20) IX[B]
        [7] -1  0       0x00001000 - 0x0000100f (0x10) IX[B]
        [8] -1  0       0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xf0000000 - 0xf0000fff (0x1000) MX[B]
        [5] -1  0       0xf4000000 - 0xf3ffffff (0x0) MX[B]O
        [6] -1  0       0xf0100000 - 0xf0103fff (0x4000) MX[B](B)
        [7] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [8] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [9] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
        [10] -1 0       0x00001040 - 0x0000105f (0x20) IX[B]
        [11] -1 0       0x00001400 - 0x000014ff (0x100) IX[B]
        [12] -1 0       0x00001020 - 0x0000103f (0x20) IX[B]
        [13] -1 0       0x00001000 - 0x0000100f (0x10) IX[B]
        [14] -1 0       0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.0.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 6.5.8
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) ATI: ATI driver (version 6.5.8) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
        ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
        ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
        ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
        ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
        ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
        ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
        ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
        ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
        ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
        ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
        ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
        ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
        ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
        ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
        ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
        ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
        ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
        ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
        ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
        ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
        ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
        ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
        ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
        ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
        ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
        ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
        ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
        ATI Radeon Mobility M7 LW (AGP),
        ATI Mobility FireGL 7800 M7 LX (AGP),
        ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
        ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
        ATI Radeon IGP330/340/350 (A4) 4137,
        ATI Radeon IGP330M/340M/350M (U2) 4337,
        ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
        ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
        ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
        ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
        ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
        ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
        ATI Radeon Mobility 9000 (M9) Lf (AGP),
        ATI Radeon Mobility 9000 (M9) Lg (AGP),
        ATI Radeon 9100 IGP (A5) 5834,
        ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
        ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
        ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
        ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
        ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
        ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
        ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
        ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
        ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
        ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
        ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
        ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
        ATI FireGL RV360 AV (AGP),
        ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
        ATI Radeon Mobility 9600 (M10) NQ (AGP),
        ATI Radeon Mobility 9600 (M11) NR (AGP),
        ATI Radeon Mobility 9600 (M10) NS (AGP),
        ATI FireGL Mobility T2 (M10) NT (AGP),
        ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
        ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
        ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
        ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
        ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
        ATI Radeon X600 (RV380) 3E50 (PCIE),
        ATI FireGL V3200 (RV380) 3E54 (PCIE),
        ATI Radeon Mobility X600 (M24) 3150 (PCIE),
        ATI Radeon Mobility X300 (M24) 3152 (PCIE),
        ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
        ATI Radeon X600 (RV370) 5B62 (PCIE),
        ATI Radeon X550 (RV370) 5B63 (PCIE),
        ATI FireGL V3100 (RV370) 5B64 (PCIE),
        ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
        ATI Radeon Mobility X300 (M22) 5460 (PCIE),
        ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
        ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
        ATI Radeon XPRESS 200M 5A42 (PCIE),
        ATI Radeon XPRESS 200 5A61 (PCIE),
        ATI Radeon XPRESS 200M 5A62 (PCIE),
        ATI Radeon XPRESS 200 5954 (PCIE),
        ATI Radeon XPRESS 200M 5955 (PCIE),
        ATI Radeon XPRESS 200 5974 (PCIE),
        ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
        ATI Mobility FireGL V5000 (M26) (PCIE),
        ATI Mobility FireGL V5000 (M26) (PCIE),
        ATI Mobility Radeon X700 XL (M26) (PCIE),
        ATI Mobility Radeon X700 (M26) (PCIE),
        ATI Mobility Radeon X700 (M26) (PCIE),
        ATI Radeon X700 PRO (RV410) (PCIE),
        ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
        ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
        ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
        ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
        ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
        ATI Radeon Mobility 9800 (M18) JN (AGP),
        ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
        ATI Radeon AIW X800 VE (R420) JT (AGP),
        ATI Radeon X800 (R423) UH (PCIE),
        ATI Radeon X800PRO (R423) UI (PCIE),
        ATI Radeon X800LE (R423) UJ (PCIE),
        ATI Radeon X800SE (R423) UK (PCIE),
        ATI FireGL V5100 (R423) UQ (PCIE),
        ATI FireGL unknown (R423) UR (PCIE),
        ATI FireGL unknown (R423) UT (PCIE),
        ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
        ATI Mobility FireGL V5100 (M28) (PCIE),
        ATI Mobility Radeon X800 (M28) (PCIE),
        ATI Mobility Radeon X800 XT (M28) (PCIE),
        ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
        ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
        ATI Radeon X850 5D4C (PCIE),
        ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
        ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
        ATI Radeon X850 XT (R480) (PCIE),
        ATI Radeon X850 XT PE (R480) (PCIE),
        ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
        ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Rage 128 RF/SG AGP".
(--) Chipset ATI Rage 128 GL RF (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xf0000000 - 0xf0000fff (0x1000) MX[B]
        [5] -1  0       0xf4000000 - 0xf3ffffff (0x0) MX[B]O
        [6] -1  0       0xf0100000 - 0xf0103fff (0x4000) MX[B](B)
        [7] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [8] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [9] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
        [10] -1 0       0x00001040 - 0x0000105f (0x20) IX[B]
        [11] -1 0       0x00001400 - 0x000014ff (0x100) IX[B]
        [12] -1 0       0x00001020 - 0x0000103f (0x20) IX[B]
        [13] -1 0       0x00001000 - 0x0000100f (0x10) IX[B]
        [14] -1 0       0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Loading sub module "r128"
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 4.0.4
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xf0000000 - 0xf0000fff (0x1000) MX[B]
        [5] -1  0       0xf4000000 - 0xf3ffffff (0x0) MX[B]O
        [6] -1  0       0xf0100000 - 0xf0103fff (0x4000) MX[B](B)
        [7] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [8] 0   0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [9] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [10] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [11] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [12] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [13] -1 0       0x00001040 - 0x0000105f (0x20) IX[B]
        [14] -1 0       0x00001400 - 0x000014ff (0x100) IX[B]
        [15] -1 0       0x00001020 - 0x0000103f (0x20) IX[B]
        [16] -1 0       0x00001000 - 0x0000100f (0x10) IX[B]
        [17] -1 0       0x00009000 - 0x000090ff (0x100) IX[B](B)
        [18] 0  0       0xf01203b0 - 0xf01203bb (0xc) IS[B]
        [19] 0  0       0xf01203c0 - 0xf01203df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) R128(0): PCI bus 1 card 0 func 0
(**) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8
(II) R128(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) R128(0): initializing int10
(II) R128(0): Primary V_BIOS segment is: 0xc000
(--) R128(0): Chipset: "ATI Rage 128 GL RF (AGP)" (ChipID = 0x5246)
(--) R128(0): Linear framebuffer at 0xf8000000
(--) R128(0): MMIO registers at 0xf0100000
(--) R128(0): VideoRAM: 16384 kByte (128-bit SDR SGRAM 1:1)
(**) R128(0): Using external CRT for display
(II) R128(0): Primary Display == Type 1
(WW) R128(0): Can't determine panel dimensions, and none specified.

```

---

### Post by Matthew Bartram on 2006-07-16
```
        Disabling programming of FP registers.
(II) R128(0): PLL parameters: rf=2950 rd=65 min=12500 max=25000; xclk=9000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) R128(0): VESA BIOS detected
(II) R128(0): VESA VBE Version 2.0
(II) R128(0): VESA VBE Total Mem: 16384 kB
(II) R128(0): VESA VBE OEM: ATI RAGE128
(II) R128(0): VESA VBE OEM Software Rev: 1.0
(II) R128(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) R128(0): VESA VBE OEM Product: R128
(II) R128(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) R128(0): VESA VBE DDC supported
(II) R128(0): VESA VBE DDC Level 2
(II) R128(0): VESA VBE DDC transfer in appr. 2 sec.
(II) R128(0): VESA VBE DDC read successfully
(II) R128(0): Manufacturer: FUJ  Model: 2518  Serial#: 1207959801
(II) R128(0): Year: 1999  Week: 37
(II) R128(0): EDID Version: 1.2
(II) R128(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) R128(0): Sync:  Separate  Composite
(II) R128(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) R128(0): Gamma: 2.00
(II) R128(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) R128(0): redX: 0.625 redY: 0.340   greenX: 0.285 greenY: 0.600
(II) R128(0): blueX: 0.150 blueY: 0.065   whiteX: 0.283 whiteY: 0.297
(II) R128(0): Supported VESA Video Modes:
(II) R128(0): 720x400@70Hz
(II) R128(0): 640x480@60Hz
(II) R128(0): 640x480@72Hz
(II) R128(0): 640x480@75Hz
(II) R128(0): 800x600@56Hz
(II) R128(0): 800x600@60Hz
(II) R128(0): 800x600@72Hz
(II) R128(0): 800x600@75Hz
(II) R128(0): 1024x768@87Hz (interlaced)
(II) R128(0): 1024x768@60Hz
(II) R128(0): 1024x768@70Hz
(II) R128(0): 1024x768@75Hz
(II) R128(0): Manufacturer's mask: 0
(II) R128(0): Supported Future Video Modes:
(II) R128(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) R128(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) R128(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) R128(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) R128(0): Supported additional Video Mode:
(II) R128(0): clock: 67.5 MHz   Image Size:  310 x 230 mm
(II) R128(0): h_active: 800  h_sync: 840  h_sync_end 920 h_blank_end 1064 h_border: 0
(II) R128(0): v_active: 600  v_sync: 601  v_sync_end 606 v_blanking: 634 v_border: 0
(II) R128(0): Serial No: H93700F9
(II) R128(0): Monitor name: FUJITSU e178
(II) R128(0): Ranges: V min: 50  V max: 150 Hz, H min: 30  H max: 70 kHz, PixClock max 1100 MHz
(==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
(II) R128(0): FUJITSU e178: Using hsync range of 30.00-70.00 kHz
(II) R128(0): FUJITSU e178: Using vrefresh range of 50.00-150.00 Hz
(II) R128(0): Clock range:  12.50 to 250.00 MHz
(II) R128(0): Not using default mode "1280x960" (hsync out of range)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (hsync out of range)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (hsync out of range)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (hsync out of range)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (hsync out of range)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1920x1200" (hsync out of range)
(II) R128(0): Not using default mode "960x600" (hsync out of range)
(II) R128(0): Not using default mode "1920x1200" (hsync out of range)
(II) R128(0): Not using default mode "960x600" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1440x900" (width too large for virtual size)
(--) R128(0): Virtual size is 1280x1024 (pitch 1280)
(**) R128(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) R128(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) R128(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) R128(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) R128(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) R128(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) R128(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) R128(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) R128(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) R128(0):  Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) R128(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) R128(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) R128(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) R128(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) R128(0):  Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) R128(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) R128(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) R128(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) R128(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) R128(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) R128(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) R128(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) R128(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) R128(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) R128(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) R128(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) R128(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) R128(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) R128(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) R128(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) R128(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) R128(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) R128(0):  Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "840x525"   73.57  840 892 984 1128  525 525 527 543 doublescan
(**) R128(0):  Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "840x525"   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync
(**) R128(0):  Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "700x525"   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync
(**) R128(0):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) R128(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) R128(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) R128(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) R128(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) R128(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) R128(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) R128(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) R128(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) R128(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) R128(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) R128(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) R128(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) R128(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) R128(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) R128(0):  Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "576x432"   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync
(**) R128(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) R128(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) R128(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) R128(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) R128(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) R128(0):  Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) R128(0): Modeline "512x384"   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync
(**) R128(0):  Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(II) R128(0): Modeline "512x384"   39.40  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) R128(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) R128(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) R128(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) R128(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) R128(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) R128(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) R128(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) R128(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) R128(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) R128(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) R128(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) R128(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) R128(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) R128(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) R128(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) R128(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) R128(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) R128(0):  Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) R128(0): Modeline "320x240"   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync
(**) R128(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) R128(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) R128(0): Modeline "320x240"   15.75  320 332 352 416  240 244 245 260 doublescan -hsync -vsync
(**) R128(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "320x240"   12.60  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) R128(0):  Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) R128(0): Modeline "360x200"   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync
(**) R128(0):  Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) R128(0): Modeline "320x200"   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync
(**) R128(0):  Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) R128(0): Modeline "320x175"   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync
(--) R128(0): Display dimensions: (320, 240) mm
(--) R128(0): DPI set to (101, 108)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.8
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(II) R128(0): Page flipping disabled
(!!) R128(0): For information on using the multimedia capabilities
        of this adapter, please see http://gatos.sf.net.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xf0100000 - 0xf0103fff (0x4000) MS[B]
        [1] 0   0       0xf8000000 - 0xfbffffff (0x4000000) MS[B]
        [2] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [6] -1  0       0xf0000000 - 0xf0000fff (0x1000) MX[B]
        [7] -1  0       0xf4000000 - 0xf3ffffff (0x0) MX[B]O
        [8] -1  0       0xf0100000 - 0xf0103fff (0x4000) MX[B](B)
        [9] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [10] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
        [11] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
        [12] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
        [13] 0  0       0x00009000 - 0x000090ff (0x100) IS[B]
        [14] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [15] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [16] -1 0       0x00001040 - 0x0000105f (0x20) IX[B]
        [17] -1 0       0x00001400 - 0x000014ff (0x100) IX[B]
        [18] -1 0       0x00001020 - 0x0000103f (0x20) IX[B]
        [19] -1 0       0x00001000 - 0x0000100f (0x10) IX[B]
        [20] -1 0       0x00009000 - 0x000090ff (0x100) IX[B](B)
        [21] 0  0       0xf01203b0 - 0xf01203bb (0xc) IS[B](OprU)
        [22] 0  0       0xf01203c0 - 0xf01203df (0x20) IS[B](OprU)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) R128(0): [drm] loaded kernel module for "r128" driver
(II) R128(0): [drm] DRM interface version 1.2
(II) R128(0): [drm] created "r128" driver at busid "pci:0000:01:00.0"
(II) R128(0): [drm] added 8192 byte SAREA at 0xd8af9000
(II) R128(0): [drm] mapped SAREA 0xd8af9000 to 0xb79df000
(II) R128(0): [drm] framebuffer handle = 0xf8000000
(II) R128(0): [drm] added 1 reserved context for kernel
(II) R128(0): [agp] Mode 0x1f000201 [AGP 0x8086/0x7190; Card 0x1002/0x5246]
(II) R128(0): [agp] 8192 kB allocated with handle 0x00000001
(II) R128(0): [agp] ring handle = 0xf4000000
(II) R128(0): [agp] Ring mapped at 0xb67c2000
(II) R128(0): [agp] ring read ptr handle = 0xf4101000
(II) R128(0): [agp] Ring read ptr mapped at 0xb67c1000
(II) R128(0): [agp] vertex/indirect buffers handle = 0xf4102000
(II) R128(0): [agp] Vertex/indirect buffers mapped at 0xb65c1000
(II) R128(0): [agp] AGP texture map handle = 0xf4302000
(II) R128(0): [agp] AGP Texture map mapped at 0xb60e1000
(II) R128(0): [drm] register handle = 0xf0100000
(II) R128(0): [dri] Visual configs initialized
(II) R128(0): CCE in BM mode
(II) R128(0): Using 8 MB AGP aperture
(II) R128(0): Using 1 MB for the ring buffer
(II) R128(0): Using 2 MB for vertex/indirect buffers
(II) R128(0): Using 5 MB for AGP textures
(II) R128(0): Memory manager initialized to (0,0) (1280,3276)
(II) R128(0): Reserved area from (0,1024) to (1280,1026)
(II) R128(0): Largest offscreen area available: 1280 x 2250
(II) R128(0): Reserved back buffer from (0,1026) to (1280,2050)
(II) R128(0): Reserved depth buffer from (0,2050) to (1280,3075)
(II) R128(0): Reserved depth span from (0,3074) offset 0xf02800
(II) R128(0): Reserved 0 kb for textures at offset 0xfff000
(II) R128(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Lines
        Dashed Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                10 128x128 slots
(II) R128(0): Acceleration enabled
(==) R128(0): Backing store disabled
(==) R128(0): Silken mouse enabled
(II) R128(0): Using hardware cursor (scanline 12300)
(II) R128(0): Largest offscreen area available: 1280 x 199
(**) Option "dpms"
(**) R128(0): DPMS enabled
(II) R128(0): X context handle = 0x1
(II) R128(0): [drm] installed DRM signal handler
(II) R128(0): [DRI] installation complete
(II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers
(II) R128(0): [drm] Mapped 128 vertex/indirect buffers
(II) R128(0): [drm] dma control initialized, using IRQ 11
(II) R128(0): Direct rendering enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "uk"
(**) Generic Keyboard: XkbLayout: "uk"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - disabled
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - enabled
```

---

### Post by christhemonkey on 2006-07-16
```
cd /usr/share/fonts/truetype
sudo mkfontdir 
```
Then restart X
```
sudo /etc/init.d/gdm restart 
```

Sounds like you need jack, alsa and midi working before you run it as well.

---

### Post by Matthew Bartram on 2006-07-17
Exactly the same thing. Thanks for all your help. Perhaps I'll just have to hope it works properly on my new (500MHz) computer which I'll either get this week or September (I'm away in between).

Unless you've got any last ideas?

But thankyou for the help anyway.

---

### Post by christhemonkey on 2006-07-17
Hmm.
Well i shall try this if i ever get my internet connection working, and will let you know how it goes.

(if you feel like helpling the thread is: )
[http://www.ubuntuforums.org/showthread.php?p=1217956](http://www.ubuntuforums.org/showthread.php?p=1217956)

---

### Post by Matthew Bartram on 2006-07-17
Sorry, 'fraid I don't know about such things. I have an ethernet router. Much easier :)

---

### Post by christhemonkey on 2006-07-17
Just got a job, so might be able to buy a "real" modem  soon :D

---

### Post by christhemonkey on 2006-07-30
Just had a thought, the ubuntu fonts dialog box (under System < Preferences < Fonts ) should let you install fonts easily.

Just drag the font file into it and it should setup/install them fine.
You may need to log out and back in again to use them though.

---

### Post by Matthew Bartram on 2006-07-31
Thanks, I'll try when I get back; I'm going away for 4 weeks

---

### Post by christhemonkey on 2006-08-15
Ok, internet is working now, FINALLY, will have a go at compiling this myself and let you know how it goes.

---

### Post by christhemonkey on 2006-08-16
Compiled it nicely now, and i get the same error as you about the font.

Strangely though, the font is installed and can be used by qt and gtk applications ( i know this as i can use it in the various dialog boxs)
I have emailed thedeveloper about it.
Will let you know his reply.

---

### Post by christhemonkey on 2006-08-17
Developer emailed back with a fix/workaround:
[QUOTE="Werner Scweer"]Hi Chris,

for unknown reasons some versions of the qt toolkit did not
find an "exact match" of the emmentaler font but have no problems
using it. You can try to comment out the check in the file mscore.cpp.
Around line 1224 comment out the whole "sanity check for score font" or
at least the "exit(-1);" statement in line 1239.

Werner
[/QUOTE]

I commented out the exit(-1) statement (with a // before it) and compiled and installed it, and it works!

Well, nearly, my laptop does not have enough ram, so jack dies on me, but with a better pc, it should work great!

---

### Post by christhemonkey on 2006-08-19
If anyone cares anymore,
installed it fine on my laptop, runs (with hack), can play and compose away :)
Except for my pc has just died.... need to get a new fan now.:D

---

### Post by Wilkinssohn on 2006-08-30
Hi there,

actually "Noteworthy Composer" works fine for me under wine through timidity!

I prefer fluidsynth (with qsynth), but did not get it to work at all (in wine).

A very reasonable piece of software under (k)ubuntu is noteeditor! It works with qsynth very nice and is similar to Noteworthy!

---

### Post by Matthew Bartram on 2006-08-31
Ok, when I go to the audio tab in wine config, it just exits
I presume noteeditor is the same as [noteedit](http://ubuntuforums.org/showthread.php?t=193848), which continually crashed on me.
And I'd also like to get [gscore working](http://ubuntuforums.org/showthread.php?t=243490), since that is what gaim's music messaging uses.

---

### Post by Wilkinssohn on 2006-08-31
> **Matthew Bartram said:**
> Ok, when I go to the audio tab in wine config, it just exits
I presume noteeditor is the same as [noteedit](http://ubuntuforums.org/showthread.php?t=193848), which continually crashed on me.
And I'd also like to get [gscore working](http://ubuntuforums.org/showthread.php?t=243490), since that is what gaim's music messaging uses.

Try this (wine audio-tab problem fix):

mkdir -p $HOME/.kde/socket-$HOSTNAME
sudo rm /usr/lib/wine/winearts.drv.so

and the wine-audio-tab should work fine.

And forget about noteedit, i just figured out that there is a heavy bug (keyboard disabled, you can't edit score) in the recent ubuntu-package. But I have found a fixed version, i don't know where it was, maybe in this forum or via google.

For me the best alternative is rosegarden4 (works with fluidsynth/qsynth).

edit no2:
ok, here are the packages that worked for me (packages are for dapper):

[http://www.arrakis.es/~caret/noteedit_2.8.0-2_i386.deb](http://www.arrakis.es/~caret/noteedit_2.8.0-2_i386.deb)
[http://www.arrakis.es/~caret/noteedit-data_2.8.0-2_all.deb](http://www.arrakis.es/~caret/noteedit-data_2.8.0-2_all.deb)

original post: [https://launchpad.net/distros/ubuntu/+source/noteedit/+bug/38743](https://launchpad.net/distros/ubuntu/+source/noteedit/+bug/38743)

---

### Post by Gongchime on 2008-06-17
Scientists (linguists/anthropologists?) are saying that musical ability in humans developed as a consequence of language acquisition. I took the relationship seriously and mapped the chart I have for frequency of tone occurrences onto another chart I have for frequency of letters in English to use sentences to generate melodic series and mapped to another chart for frequency of rhythms. 

The tone occurrences I gave before are 1534726 although there is an equal chance of there being a 5 or a 3 etc... Other notes are also like this but I won’t cover them here. Since there is an equal chance, you don’t need to roll dice to determine which one, just assign it a letter and that’s good enough.

The order of letters in English based on frequency are etaoinshrdlcumwfgy....This is more than you need to assign each letter a note. High frequency letters are paired with high frequency notes.

e t a o i n s h r d l c u m w f g y...
1 5 3 4 7 2 6

I also applied techniques I had discovered from studying computer music composition which increases the likelihood that the most frequent pitches; 1, 5, 3 etc... (in that order) will occur on the down beat by a factor of 3, on beat 3 by a factor of 2 and on beats 2 and 4 by a factor of 1. The off beats are not affected.

It means that if a note falling on the down beat currently is the pitch 2, then you have to move it back three places on my mapped chart, which changes it to pitch 3, a more important pitch. 

After contemplating the bad results, I thought about how musical phrases rhyme like poetry so tried to generate some music from a book of 100 famous English poems. The results were also less than stellar. Then I remembered something I read about infant vocalizations. Babies universally around the world repeat basic syllables such as mama, dada, papa, doodoo, poopoo, peepee, weewee, kaka and don’t forget bodacious tata’s, yabadabadoo and scoobydoobydoo. 

Repetition is a basic principle in music but most modern languages are far from these primal roots. (Although I mentioned before that Bahasa Indonesian uses the repetition of a word to indicate the plural.) The rhymes in the book of famous English poems occur too infrequently at the end of long sentences to be very musical so I started looking to song lyrics especially short repeated things which might be the correct length for generating interesting musical phrases. 

So, I generated some melodies from;

Get up stand up. Stand up for your right. Get up stand up. Don’t give up the fight.

We’re jammin, jammin, and I hope you like jammin too.

Holy Mount Zion, Holy Mount Zion, jah siteth in mount Zion.

No woman no cry. No woman no cry.

Sunday Bloody Sunday, Sunday Bloody Sunday Sunday Bloody Sunday

I want to run. I want to hide. I want to tear down the walls that hold me inside. 

I wait for you with or without you. 

The results are much better but I keep running across the tritone leap from F to B or from B to F. It’s not frequent though so some of the phrases are quite nice. 

To avoid problems having to do with voice leading, I experimented with dropping the 2 and 6 from the equation and that leads to a greater frequency of usable melodies but will lean toward the boring side if I also apply the rule about important pitches on the downbeat because then there are just too many repeats of pitches 1, 5 and 3. 

All of this ignores rules about how notes move which is a whole other thing.

I have the quarter note being the most frequent, two eighth notes being the second most frequent, a dotted eighth note followed by a sixteenth the third most frequent etc...

In the beginning I had included dotted eighth notes paired with an eighth but that was creating long boring pauses. I also had included 4 sixteenths which seemed to interrupt the flow, so that was also removed. 

Now the only fairly long pause occurs, for example, after a note falling on the "e of 1" (as in 1 e & a) followed by a note falling on the "a of 2" etc...

After I’ve circled the parts of the phrase up to the point where it’s not working then I can make the last note longer which is outside the delineated scheme.

Composing music is like an ant looking for food. In the beginning it’s fairly random but with more information the search becomes more focused. 

[http://www.musiccog.ohio-state.edu/Huron/Publications/huron.voice.leading.html](http://www.musiccog.ohio-state.edu/Huron/Publications/huron.voice.leading.html)

Have a look at this link for rules concerning melodic motion/voice leading especially charts 5 and 8 along with the first paragraph in the chapter called Types of Melodic Intervals. There’s also some cool charts 75% of the way down the page. The article also talks about note length as well as what to do with pitches on either side of a leap. 

As far as an example of a pitch series derived from letters in a lyric here is the resulting series from Got a Black Magic Woman, Got a Black Magic Woman etc... Dots indicate holding the note for the indicated number of pulsations. Lower case letters indicate the octave and underlined notes indicate the lower octave

cG..G.Eb.C..Bb.FEbDC..G.EbEb....EbF..FCDBb..CF.CEb.....EbC..BbEb.EbD........

Concerning my second post one could map the order of common interval motion to common letters which might look something like;

e....t.....a....o....i.....n....s....h....r......d....l.....c.....u 
M2..Uni..m2..P4..m3..M3..P5..M6..Oct..m7..M7..m6..TT

The resulting intervals derived from, "Get up. Stand up. Stand up for your right." results in M2 Unison P5 Unison m2 M3 m7 P5 Unison m2 M3 m7 P4 Oct P4 Oct Oct m3 M6 Unison. The tritone has been left out. The octaves also look like they need to be left out. The problem now is in acquiring a guiding principle delineating which direction each interval should move. 

We should also assign more letters to the interval of a major second since it occurs with significantly greater frequency. I suspect a minimum of between 6 and 12 letters.

Note durations could be based on interval sizes preceding and following. 

I came up with three really good tunes using these methods. I only went through a handful of nonsense to find them after a night and the next day of fiddling. But I’ve altered the interval method. 

After looking more closely at the chart of melodic interval motion I’ve remapped the intervals so that intervals which occur significantly more frequently get more letters. With this one, the octave does’t need to be eliminated since it is now more infrequent.

M2....................Uni........m2........P4......m3.....M3.....P5.....M6....Oct.....m6....m7....M7
e t a o i n s.........h r d l...c u m.....wf......g.......y.......p......b.......v.........k......j......x

As I said before, this last method probably doesn’t need any special kind of repeating short text. Just use your favorite book, play through the results and then use the best, discarding the rest. 

It does make for some interesting decision trees on the staff. 

I was worried about finding a rule for deciding which direction an interval should go, either ascending or descending but mostly that is decided for you like this;

If you’ve got an interval of a major second you’re supposed to use, then if you’re assuming the male vocal (mocal?Hehe) range/tessitura and you’re starting at the bottom of that range on C then obviously you must ascend to D. Also, if you’re trying to stay diatonic then the Bb below C, if it were allowed, still would not be an option since its not diatonic.

But, if you’re on G then you can either go to the A above or the F below. However, it’s best not to decide just yet and keep track of where each line goes because there may be some situation where one of the lines terminates because there is an interval combination that won’t work for that line such as if you’re on D and the interval you should travel from there is a Major third. There is no diatonic major third from D (If you’re in C Major) so then you’d have to abandon that line. 

I actually came up with a really cool thing when all the lines terminated because of a similar problem. I just used the non diatonic interval on the longest line and then continued from there. It created a Bb in C Major which sounded like a folk melody in the style of Led Zeppelin’s tune that goes "Shoot straighter than before. Dance in the dark of night sing to the morning light...." I can’t remember the name.

Anyway, the other way to decide if you’ve got several good lines to choose from is to give priorities to lines that contain the most number of 1s, 5s, and 3s in that order etc... It was really kind of fun making these babies. 

Now I’ve got several ways to come up with new tunes rapidly; traditional transformations on existing melodies, note frequencies mapped to the freqeuncy of English letters which requires short texts and the frequency of intervals mapped to English letters which has no length requirements. Still working on mapping the rhythms although I’ve got something that kind of works already. The chart on the link I gave really opened my eyes to how that should look/sound. Still ruminating.

One of the things I learned from my little experiment is that using language as a source will yield
melodic and rhythmic combinations which are common to English because of common letter combinations and common words such as "the" etc... Many possible and perhaps good combinations will never arise because things like "q" followed by "a" don’t exist.

To overcome the bias of English to common letter/word combinations and to overcome the bottle-neck of using dice perhaps cards or tiles would be best. 

There are inherently unavoidable problems with these methods though that we need to be aware of. And will also exist in any computer program. 

The pitch frequency method has the problem of not placing important pitches on important beats and creating too frequently the tritone leap. Even worse, it does not frequently enough create motion by step or third. 

So, we could use the interval method to evaluate the fitness of anything produced by the pitch frequency method. If the ratio of seconds to other intervals is not within a certain parameter...something like 80% of the ideal, then we can probably say with some confidence that it’s not a good melody without even listening to it. If it’s got a lot of 5ths, 6ths and 7ths and only a couple of seconds and thirds, it’ probably shite.

The problem with the INTERVAL method is that it gets trapped in a back and fourth motion, for example going between G and A or F when it’s calling for all those Major seconds. It also does not place important pitches on important beats. Anything created with this method should be evaluated for fitness by the rules of the first method by simply counting notes and if there aren’t enough 1s, 5s and 3s not being anywhere near the ballpark of the called for parameter, then what the interval method has produced is also probably shite. 

It’s not hit and miss if you do this step before listening. Chucking the probable shite into the circular file.

Both methods also create lines longer than four measures without real coherent motifs. Although the first method can get closer if using short rhyming text. 

The problem with the rhythm method (there’s a joke in here somewhere) is that it creates a string of unrelated rhythms without much underlying structure. There are repeating rhythms and there are repeating melodic series if using language but they usually don’t line up together, which is O.K. but not the whole ballgame. That is something that also needs to happen that these methods just can’t accommodate. So you’re left with the musical cortex on that count.

So YOU repeat or sequence something YOU find interesting. Hey, you’re a composer now. Wow!

In order to improve the pitch method you’d need tiles or cards. 10 tiles for C, 9 tiles for E, 9 tiles for G, 8 tiles for B, 7 tiles for A, and 7 tiles for D.

Perhaps for the interval method you’d need 1 tile for M7, 1 tile for m7, 1 tile for m6 and 1 tile for the Octave. Then 2 tiles for M6, 3 tiles for the P5, 4 for M3, 5 for m3, 10 tiles for P4, 15 tiles for m2, 20 tiles for the unison and 35 tiles for the M2. 

Rhythms are the killer. I’ve got a chart favoring eighth notes by having 10 "pairs of eighth notes" but only one "sixteenth note rest followed by two sixteenth notes followed by another sixteenth note rest" which occurs very infrequently. The total chart has 97 items (9 dotted eighths followed by sixteenths etc...) 

One of the things you realize even after only a cursory look at songbooks (I’ve currently got Mariah Carey, U2, Sting, Santana, Bob Marley and George Benson) is that any rhythm can be repeated up to 32 and even 64 times, even a normally very infrequent rhythm. So, there can’t just be one of those infrequent rhythms because we may need to use it 64 times. So it means if we’re going to have enough of the most infrequent rhythm just in case we want to use it that much, we need more items in the list. 97 multiplied by 64 is 6, 008!!! 

It would probably take me a couple of weeks to make a bag full of that many tiles with the correct rhythms written on them and I’m not inclined to do it. And I’m still not sure about the weighting. There may need to be exponentially more instances of 2 eighth notes. I’m sure of my melody and interval charts but my current rhythm chart is just an approximation. It was difficult to understand the data because it was recorded in seconds and milliseconds not in eighths, dotted eighths, eighth note triplets etc... 

Anyway, the goal is to get to the gems faster, not wade through tons of crap. So, how to focus the search for viable rhythms? Of course one way is to use the existing melodic rhythms from songs we already like. But thats not in the spirit of what I’ve been trying to do here.

There is a similar issue with the interval method. Right now there is only the possibility of having 4 major thirds and 5 minor thirds. Having more than that is within the realm of possibility so the number of tiles may have to be doubled/tripled etc... in order to create that ability. 

I just realized that I’ve been miscalculating the number of basic rhythms. It’s closer to 127 basic cells. Now its looking like there are over 186, 000 possible rhythm combinations over 8 beats in 2 measures. 

Also, the reason the scholarly journal article measures the rhythms in seconds is because when looking at the sheet music, some common rhythm cells are tied to previous and/or subsequent cells. The cells that tie over cannot even be ranked because you would have to know the cell that it ties to in order to determine if the tied note was short or long. Since it can tie to anything, it cannot be determined how it ranks. 

I was able to find some useful information about the frequency of stress patterns in English lyrics. First off, short words are more common than longer words.

There are 995 words that have two syllables where the second syllable is stressed and occur 24, 558 times out of a million words and have a weighted frequency of 19.98%. This is the most frequent stress pattern.

There are 3, 624 words that have two syllables where the first syllable is stressed and occur 67, 693 times out of a million words and have a weighted frequency of 18.08.

These first two are by far the most frequent.

2, 619 words account for three syllables with the stress falling on the first beat and occur 24, 558 times out of a million and have a weight of 9.38.

A three syllable word with the second syllable accented occurs 15, 278 times out of a million words and has a weighted frequency of 10.12. This is the third most common stress pattern. 

All of the rest of the words have much fewer instances. 

A three syllable word with the third syllable accented occurs only 1, 398 times and has a weighted frequency of 3.79.

A four syllable word with the first syllable accented occurs only 3, 549 times out of a million and has a frequency of 7.14.

A four syllable word with the second syllable stressed occurs 9, 014 times and has a weighted frequency of 6.77. (This is the ONLY kind of word longer than three syllables that occurs in Mariah Carey’s 1 hits. That word is eMOtional. I guess it better be important.) 

A four syllable word with stress on the third syllable occurs 6, 831 times and is weighted at 6.72.

A four syllable word with stress on the fourth beat occurs 97 times out of a million words. NOT MUCH!!! and is weighted at 2.62. 

Five syllable words aren’t even in the ballpark. 

Other useful information is that 90% of all content words such as nouns and pronouns (not verbs, adjectives or adverbs) begin with stressed syllables. A greater frequency of verbs have the second aka last syllable stressed.

I put some new items up on myspace within pics in the folder called Music Composition at [http://viewmorepics.myspace.com/index.cf....albumId=1823777](http://viewmorepics.myspace.com/index.cf....albumId=1823777)

Of course you have to log in first to see them.

It's got the basic rhythm cells from my journal along with the rhythm schemes (called the Scheme Pool on my Music Composition Flow Chart which is also there).

There is also a chart of the first and second measure's possible rhythm schemes where you would plug in the basic cells. There is a second chart for the the placement of anacrussis rhythms in a "second measure".

The thing to look at on my current composition flow chart is how the notes branch on the staff under the "Interval Series" heading. Notice how paths are chosen based on their weight aka predominance of pitches 1,5,3etc...

One of the things I came up with was to use a fit melody as guide tones for subsequent composition. But even after all this work, expert systems are still supposed to be better. That's where you input a melody and perform continuing transformations on it to come up with new material. That's in the lower right hand corner of my Music Composition Flow Chart but just roughed in. There wasn't enough space.

The chart I used a while back which shows simultaneous Top-Down and Bottom-Up decisions is there also as well as rhythms for half of all my favorite drum kit, bass, keyboard and guitar rhythms, as well as a chart of Middle Eastern, Latin, Afro-Cuban and Indonesian hand drum rhythms.

Something for everyone.

---


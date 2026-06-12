---
title: "PSX backups in various formats, how to consolidate?"
date: 2007-08-25
forum: Gaming &amp; Leisure
---

### Post by xen on 2007-08-25
Hello fellow Ubuntu users!

Over the years I have created backups of the Playstation games that I own. I've been into the system's emulation from the start. However, as the years went on, I used different applications to backup my games and ultimately I've been left with a messy collection of my games in various image formats.

Here are the formats that I have games in:

.bin
.iso
.img
.mdf

It should also be noted that some other files were created when I backed up my games including .cue's and .sub's among other things. In my young stupidty I deleted many of these files because I found they were not needed to run the games in emulators. Did I make a mistake in deleting these fies?

Which of the above formats is the best? Is there a way that I can convert my existing images to this format without losing any data integrity? Some of the games I will be able to backup again if I dig them out of the loft although my main priority is to convert the existing images into a single format.

Thanks for any help in advance!
EDIT: Naturally, I need to achieve the results within my (K)Ubuntu installation without the use of Windows.

---

### Post by acoustibop on 2007-08-25
It depends what emulator(s) you're using, xen.

I would guess if you've found the extra files unnecessary, you're probably using ePSXe.  In this case, the extra files from ripping are unnecessary; I don't think the plugins used by ePSXe use them.  I have to say, though, I've never really used ePSXe in Linux much, although I do have it installed and working.

Unfortunately, from the very basic nature of the built in plug-in, I don't know if it will handle copy protected games well, if at all.  In Windows, plugins such as Pete's (or P.E.Op.S) CDR plugins can be used to generate files including subcode information if this is needed to defeat protection.  There doesn't seem to be any such option in Linux.

But you don't need the extra files in ePSXe as long as you're happy with its limitations.  AIR in Windows, I used to find .img images worked a little better than anything else, but I don't think it's that significant.

I don't know, but I would suspect pretty much the same applies for PCSX as ePSXe.

If you're using pSX, which is pluginless, it will read subcode information if it's included in the image; however, you will need the extra files for this.  Since not all image formats include subcode, this makes .ccd/.img/.sub and .mds/.mdf the best formats for pSX, as they're the two that do.  pSX will also need a .cue file or equivalent (the .ccd file with the .img format and the .mds file with the .mdf format) for optimum results with any format, so for pSX you do want the extra files.

If you haven't tried pSX yet (I suspect you haven't), give it a go; you may be pleasantly suprised: [http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/)

---

### Post by xen on 2007-08-25
Thanks for your reply!

Infact the emulator I am using is pSX, and it hasn't seemed to require any .cue files as I had previously deleted these. I've managed to convert nearly all of my images to .img and found a program to generate the missing .cue files. I guess all thats left is converting these mdf/mds files (which won't seem to play in pSX or ePSXE as far as I can tell without prior mounting or burning) to the same format.

Unfortunately I know for a fact that I mistakenly deleted .sub files, although fortunately I have not had any problems playing any games (yet) and since I have the original discs in the loft somewhere I can dig them out should I need to.

I would prefer to use ePSXE since some of the graphical enhancements are really neat however I don't know how to set this up on my 64-bit installation, whereas I found an easy guide for using 'pSX32'.

Thanks for the help so far,
xen

---

### Post by acoustibop on 2007-08-25
Which version of pSX are you using, xen?  The current version of pSX, 1.12, now recognises the .mds/.mdf format.  This format also doesn't require an extra .cue file; the .mds file is the equivalent of a cue file.

Yes, pSX will run images without the .cue/.ccd/.mds files, but if you run it from a terminal, you'll see it's guessing the format of the image; this doesn't always work.  Many images include separate files such as music files, and these won't work without a properly written .cue file.  In fact, the best way to run images in pSX is to select the .cue file (or .ccd or .mds file) rather than the image itself.

I would presume you're probably using NTSC-US games, as otherwise the odds are some of your games would be copy protected and probably wouldn't play without subcode information.  Protection is not nearly as common in NTSC-US games as it is with PAL games - it's also often mod rather than copy protection.

I used ePSXe for many years (probably 6 or 7) in Windows and think it's a great emulator, but I have to say when I found pSX it didn't take long to realise how much better that is.  pSX is aimed at accurate Playstation emulation rather than enhancement.  Enhancement is all very well, but actually introduces graphical inaccuracies into the picture - once I started using pSX, it didn't take long to realise the difference it makes.

I've yet to get the analog sticks for an analog controller working with ePSXe in Linux and I'm not sure they can be made to work; it's also not easy to set up even in 32 bit Linux.  In pSX, on the other hand, there are no such problems.  pSX is still in active development, as well, which certainly isn't true for any other Playstation emulator in Linux - ePSXe hasn't seen an update in 4 years.

But the bottom line for me is transparency: playing a game in pSX is so much more like playing it on a console: you don't get the glitches and slowdowns which constantly plague playing games in ePSXe.

I would guess the guide you found for using pSX was probably dfreer's?  Check out his [How-To: install pSX on AMD64/i386]("http://ubuntuforums.org/showthread.php?t=394097") in this forum, and [LINUX v1.11 on AMD64 How-To]("http://psxemulator.proboards54.com/index.cgi?action=display&board=feedback&thread=1174936096&page=1") in the pSX forum.

---

### Post by xen on 2007-08-26
Thanks for the information,

When I was using ePSXe on my laptop in Linux I managed to get the analog sticks working on my PS2 controller with adapter. I think I had to use a plugin called 'padJoy', you have probably heard of this.

Yeah most of my games are NTSC although I have a few PAL import games, namely Final Fantasy games (the European's always got the better, traditional FF box artwork!).

I wish pSX was open source so I could write a nice Qt GUI for it, or atleast GTK+2, the only bad thing about pSX is the UI but this comes as a cost of being cross-platform, which we just can't complain about!

I think I'll stick with the mds/mdf files for now then, thanks for all your help.
xen

---

### Post by acoustibop on 2007-08-26
Yes, most of the European Final Fantasies aren't copy protected, xen, although the European versions of Final Fantasies VIII and IX are.  In fact, I just got a copy of Final Fantasy IX and had some trouble running and ripping it - then I tried it in my DVD-RW instead of my DVD-ROM - no problem!  -RW drives generally read more formats than -ROM drives, and this can be important when reading copy protected games.

BTW there is an excellent Frontend for pSX written by one of the pSX forum admins, [Ultima's pSX Frontend]("http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1156715263"): he has Linux versions as well as Windows.  It offers a very complete set of starting options for pSX, including ones, such as BIOS selection, that you can't set via switches.

Edit: PadJoy 0.8 is actually the input plugin I'm using for ePSXe.  But I just can't get the analog sticks to work in it.  Apart from that, the pad works Ok as a digital-only pad.

Edit 2: did a little research and managed to get analog enabled.  But it's a bit of a palaver to switch between analog and digital...

---

### Post by xen on 2007-08-27
BTW I have converted all of my game backup's to the .cdz format using pSX. I know this limits me to using pSX, it is by far the best emulator and I can always convert them back to the regular files using it.

I think it is a great format because it compresses the images using zlib compression and includes all of the subcode/cue information and the actual image into a single file. Excellent stuff!

I feel that pSX can only get better, and maybe one day it will be open source. I live in hope.

xen.

---

### Post by acoustibop on 2007-08-27
The other advantage of .cdz, xen, is that apparently it can be decompressed 'on-the-fly.'  Other formats require the entire file to be decompressed for use.

---

### Post by aphirst on 2007-10-15
> **acoustibop said:**
> The other advantage of .cdz, xen, is that apparently it can be decompressed 'on-the-fly.'  Other formats require the entire file to be decompressed for use.

He speaks truth...

xen: what's wrong with pSX's GUI? it seems perfectly fine to me. Although, to be fair, I care little for aesthetics; functionality does it for me, and it controls all the essential features (as I see things...).

I keep all of my PSX backups in pSX's cdz format, simply because it saves space; and I'm a real tightwad for HDD space :P .

Hang on; I thought pSX was already open source. dfreer seemed to imply that it was; as he built the packages himself for his repository... interesting.

Screenshots, if anyone cares... :D

---

### Post by acoustibop on 2007-10-15
No, pSX Author is the developer of pSX emulator, aphirst.  dfreer simply maintains and provides a package that installs it conventionally.  The emulator actually comes as an executable with some extras like the cdz tool and the basic set of default folders - you can, if you wish, just tar the download from the [pSX site]("http://psxemulator.gazaxian.com/") to a folder wherever you want (in your home folder, for instance) and run it from there.

And no, pSX Author hasn't released any source code, although it's possible he may share it with some other developers.

I agree, pSX' gui is perfectly adequate.  The whole point of the emulator is accuracy and, for me, its premier quality is 'transparency' - that is, it intrudes much less on the game playing experience than other Playstation emulators, leaving you free to get immersed in the game rather than the details of the emulator.   I can't help feeling that a fancy gui might intrude on this transparency rather than improve the emulator.

---

### Post by dfreer on 2007-10-16
eh, I thought I had covered the question on whether pSX was open-source or not... oh well, more to add to the FAQ.

---

### Post by aphirst on 2007-10-16
Yes, you had covered it in your FAQ. I was blind and missed it :rolleyes: . How silly of me.

So, dfreer, if I undersand correctly, you made a package containing the executables, a *.desktop menu entry, and dependency tree information to be able to install the program through apt, rather than having to get the executables and realise you havent installed any of the libraries? Good stuff.

And might I just say, how honoured I am, and how we all must be, that the great dfreer himself has emerged, in the flesh, into this humble thread. We bow before his immenseness, bringing ease of emulation of Final Fantasy to us all. XD

---

### Post by dfreer on 2007-10-16
> **aphirst said:**
> So, dfreer, if I undersand correctly, you made a package containing the executables, a *.desktop menu entry, and dependency tree information to be able to install the program through apt, rather than having to get the executables and realise you havent installed any of the libraries? Good stuff.

Yep, plus I made a repository on my web server so that people can simply add it and get the latest* version via apt-get update. The only real dependency on AMD64 systems was a metapackage of 32-bit libraries and a 32-bit version of libgtkglext. I also created a thread on pSX forums raising awareness for the need for configuration files to be stored in user home directories in linux, which pSX author included in 1.13.

> **aphirst said:**
> And might I just say, how honoured I am, and how we all must be, that the great dfreer himself has emerged, in the flesh, into this humble thread. We bow before his immenseness, bringing ease of emulation of Final Fantasy to us all. XD

Hmmm, perhaps I should start my own religion, eh? I could get used to hero worship :rolleyes:
In all fairness, acoustibop is a sexy beast, and I like to stalk him across various forums around the internet. And pSX author is the maker of this great emulator, what I did with the packages is really rather easy once you know how to do it, and can probably be done much better.

---


---
title: "nes emulator"
date: 2005-11-21
forum: Gaming &amp; Leisure
---

### Post by ikki_72 on 2005-11-21
downloaded tuxnes but i don't really know how to install n use it. i tried following the readme file, but nothing's happening? here's what i did. i double-clicked the file. type the ./configure stuff n all. :confused:

---

### Post by pud on 2005-11-21
Havent tried that one but plenty others at [http://www.zophar.net/unix/unix.phtml](http://www.zophar.net/unix/unix.phtml)

---

### Post by ikki_72 on 2005-11-23
at least can anyone tell me how to install anyhing in ubuntu?

---

### Post by MaxDougal on 2005-11-23
Extract it and read the readme.

---

### Post by unixfudotnet on 2005-11-23
I like zsnes, it can play nes games too, i think, though not sure.

---

### Post by jdodson on 2005-11-23
fceu is a good nes emulator.  i use it with my gravis gamepad(serial connection).

#sudo apt-get install fceu

---

### Post by NMUrugbysteve on 2005-11-23
FCEU isn't usable if you don't have a gamepad because there's no support for changing the inputs.

---

### Post by alias_401 on 2005-11-23
is there a window emulator

---

### Post by ikki_72 on 2005-11-25
i used to play alot of emulators on windows(zsnes,jnes,neorage-x,mame,epsxe n all) but in linux..sigh...

---

### Post by ikki_72 on 2005-11-25
[QUOTE=MaxDougal]Extract it and read the readme.[/QUOTE]
here's the situation; extracte it on desktop, but the synaptic thing won't work/load. n i dunno how to install i through command. tried following redme, that ./configure stuff, but i got stucked when trying to open the file, which extracted on desktop. i cd /desktop then cd /"the file name" but it can't find. i feel like singing beatles song, help.:(

---

### Post by cdsboy on 2005-11-26
if the file ends in .sh all you have to do is "sh *file.sh"
if its a .run file its "./*file.run"
if its a .deb file is "dpkg *file.deb"
if its a .rpm then you have to go "sudo apt-get install alien" (if haven't already) and then go 'alien -i *file.rpm"
and all of this is in the terminal. you have to be in the same folder as the file for any of these to work. to get to diff folders you type "cd *folder" and to go back a folder you type "cd .."
and if its a source thing then they should have instructions for installing.
it is always a good idea to make sure you have a c++ compiler on hand too. to get a good one go "sudo apt-get install g++"

-hope it helps

---

### Post by cdsboy on 2005-11-26
oh and also "dir" shows the contents of the folder

---

### Post by SolidAndShade on 2005-11-26
[QUOTE=NMUrugbysteve]FCEU isn't usable if you don't have a gamepad because there's no support for changing the inputs.[/QUOTE]

You can change the directional inputs if you hex edit ~./fceultra/fceu98.cfg. Start up the hex editor GHex (after installing GHex if you don't have it) and use it to open the fceu98.cfg file. Look through the text display until you find something that reads "GamePadConfig."  Several empty spaces after the GamePadConfig line, you'll see "w  z  a  s" or whatever crappy default directional configuration fceu comes with. I changed the letters to "w  s  a  d" to create a standard directional pad. To change the letters, highlight them and type in the hex value of the desired letter. [This table]("http://www.lookuptables.com") gives the hex values of all ASCII characters.

---

### Post by holomate on 2005-11-27
[QUOTE=jdodson]fceu is a good nes emulator.  i use it with my gravis gamepad(serial connection).

#sudo apt-get install fceu[/QUOTE]

Yup it's that easy. Of course you'll have to mess around with the various options to customize it to your system (this is no different than windows).

At the moment I'm able to play games with the keyboard, but even with the -xinput gamepad option, it doesn't want to use my Gravis Gamepad (hooked up to the gameport on my soundcard (which works)). Any suggestions?

Also. How does one increase fceu's priority and let it grab more cpu cycles over some of the other programs I want in my background?

---

### Post by quietglow on 2005-11-27
Try System>Synaptics Package

and then do a search for nintendo etc.

Zsnes and others (mame I think) are in the repositories and install with a click. Nice!

---

### Post by ikki_72 on 2005-11-27
its nauseating since the synaptic package manager won't load when i choose it. how to fix it?

---

### Post by quietglow on 2005-11-27
It won't load? Does it get as far as asking your root pw? Are you putting it in? Need some more info.

---

### Post by ikki_72 on 2005-11-28
well, i choosed from the drop-down menu, but it won't load at all. not even asking 4 pwd. reinstall ubuntu?

---

### Post by smack on 2005-11-29
[QUOTE=ikki_72]well, i choosed from the drop-down menu, but it won't load at all. not even asking 4 pwd. reinstall ubuntu?[/QUOTE]

Try running synaptic in a terminal and see if it gives you any errors. 'sudo synaptic'

---

### Post by ikki_72 on 2005-11-30
i'd try that

---

### Post by Barts_706 on 2005-12-01
[QUOTE=ikki_72]i used to play alot of emulators on windows(zsnes,jnes,neorage-x,mame,epsxe n all) but in linux..sigh...[/QUOTE]

No sighing. In Linux you can use zsnes (I know, because I played FF6 on it) and you can use Mame emulator with graphical front-end (X-Mame for example) and it will run your arcasde games plus Neo-Geo games (correct me if I'm wrong). I think there is epsxe version for Linux, and even if not, there are Linux PSX emulators around. 

So happy face instead of sighing - you can emulate quite a lot of things under Linux.

---

### Post by BoyOfDestiny on 2005-12-01
I use mednafen and fceu for nes. For snes zsnes is the way to go. I made some .debs (in breezy) here:

[www.safaribans.com/gpl/](www.safaribans.com/gpl/)

Sources included too...

Anyway, just download a deb and type sudo dpkg -i nameofdeb.deb

I like mednafen a little better since it can run some other things too (i.e gba and gb) and has an internal gui (sort of like advmame) which makes it easy to set the inputs for keyboards, gamepads, etc.

Best of luck!

A little shot of Terranigma (in zsnes) and Dr. Mario (in mednafen):
[[IMG]http://img228.imageshack.us/img228/8656/screenshot6gi.th.jpg[/IMG]](http://img228.imageshack.us/my.php?image=screenshot6gi.jpg)

Here you can see DOSBox running Space Quest I VGA (floppy version) and AdvanceMAME running Final Fight (US version)
[[IMG]http://img218.imageshack.us/img218/257/screenshot27ve.th.jpg[/IMG]](http://img218.imageshack.us/my.php?image=screenshot27ve.jpg)

---

### Post by dugan on 2005-12-01
Nes emulator? Here's the BEST solution. Not the easiest, but the best.

Go to [http://www.filespace.org/blip/](http://www.filespace.org/blip/) and download fceu-0.98.12-blip.src.rar

[http://fast.filespace.org/blip/fceu-0.98.12-blip.src.rar](http://fast.filespace.org/blip/fceu-0.98.12-blip.src.rar) is the direct link.

Compile it using the instructions at [http://bisqwit.iki.fi/nesvideos/ConvertingFCMToAVIInLinux.html](http://bisqwit.iki.fi/nesvideos/ConvertingFCMToAVIInLinux.html)

You'll end up with a heavily patch FCE Ultra capable of not only playing back the speedruns at [NESVideos](http://bisqwit.iki.fi/nesvideos/), but also of recording your own.

---

### Post by gold4tune on 2005-12-01
Is somebody can tell me how i can make work fwnes...  thx

---

### Post by ikki_72 on 2005-12-04
u guys r great, let me try to get this thing working.:D

---

### Post by quietglow on 2005-12-04
I've been slacking on my emulator work, cause I just finally bought a PS2. The real thing is pretty nice too :-)

---

### Post by ikki_72 on 2005-12-05
here's the situation, i downloaded the fwnes, extracted it to desktop but dunno how to use it. anyway, i only use 2 partition for swap n filesystem. so i can't edit files in the filesystem.

---

### Post by NMUrugbysteve on 2005-12-06
[QUOTE=SolidAndShade]You can change the directional inputs if you hex edit ~./fceultra/fceu98.cfg. Start up the hex editor GHex (after installing GHex if you don't have it) and use it to open the fceu98.cfg file. Look through the text display until you find something that reads "GamePadConfig."  Several empty spaces after the GamePadConfig line, you'll see "w  z  a  s" or whatever crappy default directional configuration fceu comes with. I changed the letters to "w  s  a  d" to create a standard directional pad. To change the letters, highlight them and type in the hex value of the desired letter. [This table]("http://www.lookuptables.com") gives the hex values of all ASCII characters.[/QUOTE]

Cool, but do you know what values i can change to set my own controls for the other buttons? (A, B, Select)

---

### Post by daveg on 2005-12-07
[QUOTE=Barts_706]No sighing. In Linux you can use zsnes (I know, because I played FF6 on it) and you can use Mame emulator with graphical front-end (X-Mame for example) and it will run your arcasde games plus Neo-Geo games (correct me if I'm wrong).[/QUOTE]

I'm using xmame with gxmame (which yes, does run Neo Geo games) as the frontend and snes9x with snes9express as the frontend. All those programs were in the universe repositories except for gxmame which I got from [here]("http://sourceforge.net/project/showfiles.php?group_id=50621")

> I think there is epsxe version for Linux, and even if not, there are Linux PSX emulators around.

You'll need to add this to /etc/apt/sources.list for epsxe

> # epsxe
deb [http://www.fbriere.net/debian/dists/unstable](http://www.fbriere.net/debian/dists/unstable) ./

Then sudo apt-get update and sudo apt-get install epsxe

> So happy face instead of sighing - you can emulate quite a lot of things under Linux.Besides epsxe, xmame and snes9x, I'm also happily using Hu-Go! (PC Engine/TG16), visualboyadvance (GBA/GB), gens (Megadrive/Genesis), modeler (arcade emulator) & RAINE (another arcade emulator).

And there's plenty more!

---

### Post by omeg on 2005-12-08
[QUOTE=dugan]Nes emulator? Here's the BEST solution. Not the easiest, but the best.

Go to [http://www.filespace.org/blip/](http://www.filespace.org/blip/) and download fceu-0.98.12-blip.src.rar

[http://fast.filespace.org/blip/fceu-0.98.12-blip.src.rar](http://fast.filespace.org/blip/fceu-0.98.12-blip.src.rar) is the direct link.

Compile it using the instructions at [http://bisqwit.iki.fi/nesvideos/ConvertingFCMToAVIInLinux.html](http://bisqwit.iki.fi/nesvideos/ConvertingFCMToAVIInLinux.html)

You'll end up with a heavily patch FCE Ultra capable of not only playing back the speedruns at [NESVideos](http://bisqwit.iki.fi/nesvideos/), but also of recording your own.[/QUOTE]
I didn't realize there were fans of tool-assisted speedruns here. :)

I'm using FCE Ultra on Windows, which is an excellent emulator, but I'm very disappointed that the Linux version has no graphical user interface. Does anybody know if there is an alternative version of this emulator that does sport an interface? I'm not a big fan of tab-completing ROM names and setting up my emulator via a text editor.

---

### Post by BoyOfDestiny on 2005-12-08
[QUOTE=omeg]I didn't realize there were fans of tool-assisted speedruns here. :)

I'm using FCE Ultra on Windows, which is an excellent emulator, but I'm very disappointed that the Linux version has no graphical user interface. Does anybody know if there is an alternative version of this emulator that does sport an interface? I'm not a big fan of tab-completing ROM names and setting up my emulator via a text editor.[/QUOTE]

The closest is here:

[http://mednafen.com/](http://mednafen.com/)

Mednafen (or the other Nintencer release) is built on fceu. It has an interface similar to mame's with hotkeys etc. However, as far as I know, you can't load games from within it... I just associate my .nes with mednafen to get around that... 
Anyway we need more emulation folks coming in (using Linux and/or other alternative OS's)... I'm sure things will continue to improve regardless...

---

### Post by BoyOfDestiny on 2005-12-08
[QUOTE=NMUrugbysteve]FCEU isn't usable if you don't have a gamepad because there's no support for changing the inputs.[/QUOTE]


Absolutely False.

Here ya go:

fceu -inputcfg gamepad1 somerom.nes

Here is the output for keyboard and gamepad (although I didn't set the rapid fire on the keyboard...)
It does work with either or both:

Starting FCE Ultra 0.98.12...
GamePad #1: A (1)
GamePad #1: A (2)
GamePad #1: A (3)
GamePad #1: B (1)
GamePad #1: B (2)
GamePad #1: B (3)
GamePad #1: SELECT (1)
GamePad #1: SELECT (2)
GamePad #1: SELECT (3)
GamePad #1: START (1)
GamePad #1: START (2)
GamePad #1: START (3)
GamePad #1: UP (1)
GamePad #1: UP (2)
GamePad #1: UP (3)
GamePad #1: DOWN (1)
GamePad #1: DOWN (2)
GamePad #1: DOWN (3)
GamePad #1: LEFT (1)
GamePad #1: LEFT (2)
GamePad #1: LEFT (3)
GamePad #1: RIGHT (1)
GamePad #1: RIGHT (2)
GamePad #1: RIGHT (3)
GamePad #1: Rapid A (1)
GamePad #1: Rapid A (2)
GamePad #1: Rapid B (1)
GamePad #1: Rapid B (2)
Loading /home/*******/ROMS/NESRen/World/Balloon Fight (JU) [!].nes...

NOTE: You just need to do this once. So basically if you just map for keyboard let's say, you press A, then press it again and it moves to the next button setting. It does this so you can set it up for multiple devices... Anyway good luck!

---

### Post by ikki_72 on 2005-12-09
[QUOTE=daveg]I'm using xmame with gxmame (which yes, does run Neo Geo games) as the frontend and snes9x with snes9express as the frontend. All those programs were in the universe repositories except for gxmame which I got from [here]("http://sourceforge.net/project/showfiles.php?group_id=50621")



You'll need to add this to /etc/apt/sources.list for epsxe



Then sudo apt-get update and sudo apt-get install epsxe

Besides epsxe, xmame and snes9x, I'm also happily using Hu-Go! (PC Engine/TG16), visualboyadvance (GBA/GB), gens (Megadrive/Genesis), modeler (arcade emulator) & RAINE (another arcade emulator).

And there's plenty more![/QUOTE]
how am i gonna smile since i don't have any internet connection? sudo apt-get anyone?

---

### Post by SolidAndShade on 2005-12-09
[QUOTE=NMUrugbysteve]Cool, but do you know what values i can change to set my own controls for the other buttons? (A, B, Select)[/QUOTE]

Sadly, no. I tried for a while to figure it out but couldn't. You might be able to if you carefully search through the hex file. Remember that keys on the numeric keypad have two-byte keystroke codes. You can find their keystroke codes on that ASCII website I posted earlier.

---

### Post by SolidAndShade on 2005-12-09
[QUOTE=BoyOfDestiny]Absolutely False.

Here ya go:

fceu -inputcfg gamepad1 somerom.nes

Here is the output for keyboard and gamepad (although I didn't set the rapid fire on the keyboard...)
It does work with either or both:
[/QUOTE]

Thanks!  I didn't see that anywhere in the FCEU man page. So much for hex editing the config file.

---

### Post by NMUrugbysteve on 2005-12-09
[QUOTE=BoyOfDestiny]Absolutely False.

Here ya go:

fceu -inputcfg gamepad1 somerom.nes

Here is the output for keyboard and gamepad (although I didn't set the rapid fire on the keyboard...)
It does work with either or both:
[/QUOTE]

That's sweet, thanks so much!

I couldn't find this in any FCEU docs.

---

### Post by BoyOfDestiny on 2005-12-09
[QUOTE=NMUrugbysteve]That's sweet, thanks so much!

I couldn't find this in any FCEU docs.[/QUOTE]

No problem, I didn't find it there either :). I had to search google. 

Anyway, I guess spread the word, as this seems to happen to a lot of people...

I should work on my page more, instead of just providing the debs...

---

### Post by ikki_72 on 2005-12-19
zsnes deb works:p

---

### Post by Shadomaster_Kitty on 2005-12-27
TuxNES works fine for me, but under ALSA I have no sound. Haven't tried it on my good box under OSS yet, but can anyone inform me where I missed something?

---

### Post by punkrockguy318 on 2006-06-12
[QUOTE=NMUrugbysteve]FCEU isn't usable if you don't have a gamepad because there's no support for changing the inputs.[/QUOTE]

Not quite true.  There's a new graphical front-end, check out this post:
[http://ubuntuforums.org/showthread.php?t=195413](http://ubuntuforums.org/showthread.php?t=195413)

---


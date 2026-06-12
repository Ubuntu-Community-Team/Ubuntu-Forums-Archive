---
title: "making a backup of a playstation disc"
date: 2007-06-25
forum: Gaming &amp; Leisure
---

### Post by dfreer on 2007-06-25
Has anyone seen this article before?
[http://www.megagames.com/psx/psx_copy_patch_linux.shtml](http://www.megagames.com/psx/psx_copy_patch_linux.shtml)

For those who don't RTFA, basically it covers how to make a .bin/.toc of your original playstation discs (for backup purposes, duh! ;) ) using cdrdao, how to *patch* the .bin, and then how to burn the image back to disc.
Now, from what I read the original playstation used a copy-protection scheme, in which all original discs would produce a zero checksum, and current CD burners cannot be modified to produce the same checksum? 
Regardless of how it works, I was just wondering if this ApplyPPF software will actually patch my images so that, when burned back to CD-R, it will play in my playstation without need of a mod-chip? Has anyone used it?

I have tried compiling the program, but can't seem to get it to run. The instructions on the guide state that you need to run the command like so:
```
applyppf filename.bin filename.ppf
```
However, once the program is compiled and I try to run the program, it gives me a syntax error like so (also note I do not have a file named jet_moto.ppf... I have no idea what a *.ppf file is nor what it does):
```
$ ./applyppf jet_moto.bin jet_moto.ppf
MakePPF v2.0 Linux/Unix by Icarus/Paradox
Usage: MakePPF <Original Bin> <Patched Bin> <ppffile> [file_id.diz]
```

Obviously I have no idea what the ApplyPPF program does.
Here's the link to the sourcecode I downloaded for applyppf:
[http://www.megagames.com/console/files/pdx-mpsc.zip](http://www.megagames.com/console/files/pdx-mpsc.zip)

Anyways, any comments?

---

### Post by wingnux on 2007-06-25
A PPF is a "Playstation patch file" that patches the game in order to bypass some copy/regional protections ;)

---

### Post by dfreer on 2007-06-25
So basically I would need to find the .ppf specific for my game online *somewhere*, this program doesn't make them?

---


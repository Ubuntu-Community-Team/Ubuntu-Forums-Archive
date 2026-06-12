---
title: "bin to iso"
date: 2005-12-26
forum: Desktop Environments
---

### Post by spacifique1 on 2005-12-26
I tried to convert a .bin to .iso file but nothing seems to happen.
I installed bchunk and typed 'bchunk' in terminal and the readme data comes through. But it does not say how to use it!!!

Anybody knows of an alternate program.

---

### Post by NewbieNik on 2005-12-26
you need to run:-

bchunk (bin file) (iso file)

so you need to name the file you want to convert and the final name (and path if needed) of the converted file including the extensions!!!

---

### Post by spacifique1 on 2005-12-26
I tried : bchunk file.bin file.iso but nothing happens.

---

### Post by NewbieNik on 2005-12-26
[QUOTE=spacifique1]I tried : bchunk file.bin file.iso but nothing happens.[/QUOTE]

Sorry, I don't think I explained myself thoroughly.

Lets say the file is called image.bin and is in your home folder.
You then need to run the terminal and in there type the command:-

bchunk image.bin image.iso

This tells bchunk to use the image.bin file and convert it to image.iso. You could call the .iso file whatever you want, e.g:-

bchunk image.bin myfile.iso

You will then have an ISO file in your home folder called myfile ready to burn.

I hope this makes it a little clearer.

---

### Post by wazzo on 2005-12-29
Usage: bchunk [-v] [-r] [-p (PSX)] [-w (wav)] [-s (swabaudio)]
         <image.bin> <image.cue> <basename>
Example: bchunk foo.bin foo.cue foo
  -v  Verbose mode
  -r  Raw mode for MODE2/2352: write all 2352 bytes from offset 0 (VCD/MPEG)
  -p  PSX mode for MODE2/2352: write 2336 bytes from offset 24
      (default MODE2/2352 mode writes 2048 bytes from offset 24)
  -w  Output audio files in WAV format
  -s  swabaudio: swap byte order in audio tracks

I think you need to add the cue file

---

### Post by Ocxic on 2005-12-29
you could try downloading and installing NeroLinux. that will let you burn .bin .cue images, iether to cd-r/w or creat an iso image for you to use.

---


---
title: "Does Usplash support widescreen resolutions?"
date: 2006-06-05
forum: Desktop Environments
---

### Post by MetalMusicAddict on 2006-06-05
I have a widescreen monitor and I was wondering if there were settings for them?

Something like vga=799? (<-example. not real) Im looking for 1920x1200 or some form of 16:10 or 16:9.

```
      _color           depth   | 640x480  800x600  1024x768 1280x1024_

      256             (8bit)  |  769      771       773      775
      32000           (15bit) |  784      787       790      793
      65000           (16bit) |  785      788       791      794
      16.7 Mill.      (24bit) |  786      789       792      795
```

:-k

---

### Post by MetalMusicAddict on 2006-06-07
Anyone. :)

---

### Post by MetalMusicAddict on 2006-06-17
Me again. ;)

---

### Post by MetalMusicAddict on 2006-06-18
I hate that my post count goes up by doing this. :(

---

### Post by Ramses de Norre on 2006-06-18
Just got the right code for me from your grid, but I have no idea for your resolution..

(and one less bump for you ;))

---

### Post by Anduu on 2006-06-18
I'm guessing the answer is probably no :(

---

### Post by hayalci on 2006-06-22
install hwinfo package and see if your framebuffer supports that resolution

```
sudo apt-get install hwinfo
sudo hwinfo --framebuffer
```

Output will be lines like this, and you can put the hexadecimal number specified in "Mode" in place of vga=XXX (ie. vga=0x0317 )

```
...
 Mode 0x0317: 1024x768 (+2048), 16 bits
...
```

---

### Post by MetalMusicAddict on 2006-06-22
Thanx for the info hayalci. Looks like its a no though. All the outputs are 4:3. This is a handy tool. ;)

---


---
title: "GTK apps launching slowly - font caching problem?"
date: 2006-07-18
forum: Desktop Environments
---

### Post by richardq on 2006-07-18
I'm still having problems with GTK-based apps starting up very slowly (Gedit, GCalctool, Terminal). Watching the strace output on launching Gedit, everything flies by except there is a slowdown when it gets to the chunk of stuff shown below. Now I don't know if the reads are just slower by nature but there are other reads in the output that fly by much much quicker.

I am wondering if this is a font caching problem. I've erased the font-cache files in the /usr/share/X11/fonts/75dpi and 100dpi folders and forced a recache of all the fonts to no avail.

I have 1200+ fonts installed. Is this number high? I also have no idea how to remove fonts from the system (can I just delete them?) if there are too many.

Here's the chunk of output. It really slows down when it hits these read statements. BTW, an strace of Gcalctool also slows when it hits a similar block of reads. The initial instances of Gedit, Gcalc, Gimp etc. are taking over 10sec to appear.

```
munmap(0xb7dde000, 4096)                = 0
open("/usr/share/X11/fonts/100dpi/fonts.cache-1", O_RDONLY) = 17
stat64("/usr/share/X11/fonts/100dpi", {st_mode=S_IFDIR|0755, st_size=12288, ...}) = 0
stat64("/usr/share/X11/fonts/100dpi/fonts.cache-1", {st_mode=S_IFREG|0644, st_size=230508, ...}) = 0
fstat64(17, {st_mode=S_IFREG|0644, st_size=230508, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7dde000
read(17, "\"courB08-ISO8859-1.pcf.gz\" 0 \"Co"..., 4096) = 4096
read(17, "lias=False:index=0:outline=False"..., 4096) = 4096
read(17, "h|da|de|en|es|eu|fj|fo|fur|fy|gd"..., 4096) = 4096
read(17, "sv|sw|tn|to|tr|ts|ven|vo|vot|wa|"..., 4096) = 4096
read(17, "|vo|wa|xh|yap|zu:fontversion=0:f"..., 4096) = 4096
read(17, "t=110:weight=200:width=100:pixel"..., 4096) = 4096
read(17, "e:antialias=False:index=0:outlin"..., 4096) = 4096
read(17, "%#|>^1!|>^1!|>^1!P0oWQ[tJ)#*q&y|"..., 4096) = 4096
read(17, "wa|wen|wo|xh|yap|zu:fontversion="..., 4096) = 4096
read(17, "ntversion=0:fontformat=PCF\"\n\"cou"..., 4096) = 4096
read(17, "y|da|de|en|eo|es|et|eu|fi|fj|fo|"..., 4096) = 4096
read(17, "|om|pt|rm|sma|smj|so|sq|sv|sw|tn"..., 4096) = 4096
read(17, "foundry=Adobe:antialias=False:in"..., 4096) = 4096
read(17, "ang=aa|ast|ay|bi|br|ch|da|de|en|"..., 4096) = 4096
read(17, "y#fx!!!!5 !!!!3!!#lg  !!#3H!!!)/"..., 4096) = 4096
read(17, "1!P0oWQ |>^1!|>^1!|>^1!:lang=aa|"..., 4096) = 4096
read(17, "%&&x#y#fx!!!!5 !!!!3!!#lg  !!#3H"..., 4096) = 4096
read(17, "oWQ |>^1!|>^1!|>^1!:lang=aa|ast|"..., 4096) = 4096
read(17, ".gz\" 0 \"LucidaBright-8:style=Ita"..., 4096) = 4096
read(17, "|>^1!P0oWQ |>^1!|>^1!|>^1!!!!%#|"..., 4096) = 4096
read(17, "tformat=PCF\"\n\"lubI08-ISO8859-1.p "..., 4096) = 4096
read(17, "lse:dpi=100:charset= !!!!#|>^1!|"..., 4096) = 4096
 
```

---


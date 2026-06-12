---
title: "ePSXe emulator wont work properly"
date: 2005-07-17
forum: Gaming &amp; Leisure
---

### Post by immoral giant on 2005-07-17
After many years without Final Fantasy 9 i decided to play.  Problem was that the laser on my PSX is broken so it's pretty much useless. 

I found out about PSX emulators and tried ePSXe.

I followed this guide [here](http://terror.snm-hgkz.ch/gaming/linux/epsxe_howto/#basic)

I get up to step 12 in the basic setup section.  Then once i do step 13 i get problems.

```
 * Running ePSXe emulator version 1.5.2.
/usr/local/games/epsxe/libpthread.so.0: symbol _errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference.
``` 

Same happens if i skip to step 14, but step 15 and 16 are fine.

So it must be the plugins, which were talked about in step 9 and step 10.  I have done both step 9 and step 10 with no problems.

So i don't know how to fix this, any help and i would be grateful.

---

### Post by Refund on 2005-08-14
in the .sh file you made, get rid of this entry

export LD_LIBRARY_PATH=$EPSXE

after I did that mine worked fine.

---

### Post by kokoro on 2005-09-11
[QUOTE=Refund]in the .sh file you made, get rid of this entry

export LD_LIBRARY_PATH=$EPSXE

after I did that mine worked fine.[/QUOTE]

Okay I know this is pretty old but.....

I had the same problem with the  export LD_LIBRARY_PATH=$EPSXE entry in place. 
However when I removed it I got: ./epsxe: undefined symbol: PSEgetLibType

---


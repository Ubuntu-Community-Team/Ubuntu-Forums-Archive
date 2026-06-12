---
title: "Eternal Lands no sound"
date: 2007-12-06
forum: Gaming &amp; Leisure
---

### Post by Arveician on 2007-12-06
Ok  this is what I get when I try with sound enabled.

I launch program

sudo ./el.x86.linux.bin

Here comes the bad

I/O warning : failed to load external entity "extentions.xml"

It appears to me that I am missing some app or file.

Any help would be great.

---

### Post by Arveician on 2007-12-06
Ok after some more research and checking the error log this appears to be the problem. 

 Warning: ALC_ENUMERATION_EXT not found. Unable to retrieve list of sound devices.

I fixed it, if you are getting this error you can try this.

Download the latest source from cvs.

Compile the binary, copy the new binary to your install, yes over write.

Launch game and you should be able to enable all sound and music.

---


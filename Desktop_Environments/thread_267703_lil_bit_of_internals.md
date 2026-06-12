---
title: "lil bit of internals"
date: 2006-09-29
forum: Desktop Environments
---

### Post by mnshsnghl on 2006-09-29
Hi Guys, 
  I know this is not the right forum for such questions, but since dapper is involved... I thought I give this community a try :)

I was trying to run gdb (or kgdb) on my dapper kernel (existing and the one I compiled with debug mode ON). I just want to look at some current kernel data structures only and nothing else .. no actual debugging. So on Net I found out that I need to run gdb on /proc/kcore as core .. and then I can do anything. 
Problem is /proc/kcore is a weird file ... as a root (or sudo) if I do file on /proc/kcore... it says its a regular file, but no read permissions :(.. Well this is simply different !! But when I give following command -
gdb /boot/vmunix /proc/kcore  #(Yes, I have vmunix ... the uncompressed one) 

Again I get "Operation not permitted" ... 

Is there a way, that I can analyze live kernel data structures ?? or read through /proc/kcore.

Thanks.

---


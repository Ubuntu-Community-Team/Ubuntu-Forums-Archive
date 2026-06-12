---
title: "NWN crashes on load"
date: 2006-01-23
forum: Gaming &amp; Leisure
---

### Post by Elvish Legion on 2006-01-23
When ever I click the load button in NWN my game crashes.

Here is console output

jduvall@home-607cf1d13d:~/nwn$ sh nwn
*** glibc detected *** malloc(): memory corruption: 0x0eaa7190 ***
nwn: line 14: 13103 Aborted ./nwmain $@
jduvall@home-607cf1d13d:~/nwn$

I'm using the platinum verison installed via script on ubuntu, 512 ram amd 3400, and an nvidia 6200 gcard

The fix I found on biowares website export MALLOC_CHECK_=0 Doesn't seem to work, any one have any advice?

---

### Post by leech on 2006-01-25
Try running nwn like this ```
./nwn
```.  If that doesn't work (this will only let bash execute it rather than sh, so perhaps the fix for Bioware forums will work with that.) 

If not, then could you please post your nwn script?  Especially line 14 where it is giving the error?  

Leech

---


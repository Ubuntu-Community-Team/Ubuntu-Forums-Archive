---
title: "How to change decimal point on the fly"
date: 2009-11-29
forum: Desktop Environments
---

### Post by RikardSvenningsen on 2009-11-29
Hi
I am having trouble whit tshark because of a bug in tshark.
When using this command:
tshark -r testfile.cap -q -z io,stat,120,"COUNT(smb.time)smb.time"
This command don't work because of a bug in how to treat decimal point, it only works whit . (dot) as separator.
But generally i need to use , (comma)  in my day to day work.
So i need a way to change to dot as separator from time to time.

Anyone know how to do that??

---


---
title: "can't execute script from cd"
date: 2010-10-20
forum: Desktop Environments
---

### Post by sonic6567 on 2010-10-20
Hello,

I have written a shell script and set the permissions to executable.
It works fine.

I burn it to a cd.

But then, I cannot run it from the cd.  All of the execute permissions are gone.

Can anyone assist?

Thanks

---

### Post by sonic6567 on 2010-10-20
SOLVED

Need to use geniosimage.

The issue was with the format the cd image was in.

I was using the built in brazero burner which has no real options to set.

So I tried with K3b.  It has the required options:  Rock Ridge.  You must use Rock Ridge format in order to preserve unix file permissions.
However, even after selecting the correct options, the resulting cd still did not work.

The only way it would work is if I used the command line:
genisoimage -o ~/Desktop/cdout.iso -V CdName -R -J ~/Desktop/dataFolder

This created an iso that I could then use anything to burn.

bingo

---


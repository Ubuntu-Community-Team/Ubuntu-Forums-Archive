---
title: "GDL-IDL compatibility"
date: 2009-11-07
forum: Education &amp; Science
---

### Post by Kettarie on 2009-11-07
Hello!

I'm trying to use GDL for an  IDL program, which must open astronomical files. But I have some problems with compilation.   I have following errors:

GDL> .r /home/Kettarie/Sun/30Mar2001/norp_i_v_1.pro
% Compiled module: $MAIN$.
% Compiled module: RESTORE.
% Compiled module: CMSVLIB.
% Compiled module: CMSV_OPEN.
% RESTORE: FILE not found.
% Variable is undefined: TIM
% Execution halted at: $MAIN$    

I'm absolutely not familiar with IDL or GDL, so I would be very thankful for any help!

---

### Post by tuwe on 2009-11-10
i think restore is not supported by default in GDL. 

[QUOTE=http://gnudatalanguage.sourceforge.net/]SAVE and RESTORE are supported through Craig Markwardt's [CMSVLIB library](http://cow.physics.wisc.edu/~craigm/idl/down/cmsvlib.tar.gz).[/QUOTE] - you need to install this first.

edit: after re-reading your post, it seems as if the file to restore was not found. could you post your code?

---

### Post by Kettarie on 2009-11-14
Yes, I have found and installed this library, and now it works! Now I can start with plotting. Thank you!

---


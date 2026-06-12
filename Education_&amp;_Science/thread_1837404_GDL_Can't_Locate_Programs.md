---
title: "GDL Can't Locate Programs"
date: 2011-09-01
forum: Education &amp; Science
---

### Post by mihalybaci on 2011-09-01
I have GDL installed on my desktop computer (32-bit 11.04), and it works fine and all my programs work. I copied the file structure to my laptop (64-bit Ubuntu 10.04.2), and it won't locate any programs besides the main GDL procedures. Here's my setup

In my .cshrc file I have:

setenv GDL_STARTUP "/home/michael/.gdl/.gdl_startup"

In my .gdl_startup file I have:

!PATH=!PATH + ':/usr/share/doc/gnudatalanguage/examples/pro/'
!PATH=!PATH + ':/usr/share/doc/gnudatalanguage/examples/pro/dicom/'
!PATH=!PATH + ':/home/michael/gdl/lib/'
!PATH=!PATH + ':/home/michael/gdl/lib/coyote/'
!PATH=!PATH + ':/home/michael/gdl/lib/coyote/experimental/'
!PATH=!PATH + ':/home/michael/gdl/lib/coyote/public/'
!PATH=!PATH + ':/home/michael/gdl/lib/astro/pro/'
!PATH=!PATH + ':/home/michael/gdl/lib/mine/'
!DIR='/home/michael/gdl/'
print, '%** Personal settings are loaded and active **';

When I load GDL, I see the printed message above, so I know that the startup path is correct. When I try to use READFMT, which is one of the programs in /home/michael/gdl/libb/astro/pro/, I get the following error:

GDL> readfmt
No parser output generated.
Procedure not found: READFMT
% Procedure not found: READFMT
% Execution halted at: $MAIN$          
GDL> 

I have no idea what the 'parser output' error is trying to tell me. Help anyone?

---


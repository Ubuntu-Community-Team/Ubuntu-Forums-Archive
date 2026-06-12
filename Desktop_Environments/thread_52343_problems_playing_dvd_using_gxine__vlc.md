---
title: "problems playing dvd using gxine / vlc"
date: 2005-07-27
forum: Desktop Environments
---

### Post by ssck on 2005-07-27
hi all,

i seem to be having problems playing dvds using vlc and gxine.i have installed all the necessary codecs and libdvdcss2.it will hang half way.what could be the problem ? there are no problems playing the same dvd on a win xp machine.any ideas ?

---

### Post by super on 2005-07-27
what kind of problems? try running vlc from the command line with:

[FONT=Courier New]vlc -v /dev/hdc[/FONT]

(replace "/dev/hdc" with the path to your dvd drive is)
this will print the output from vlc to your terminal window and will show you what is causing the problem.

---

### Post by ssck on 2005-07-28
[QUOTE=super]what kind of problems? try running vlc from the command line with:

[FONT=Courier New]vlc -v /dev/hdc[/FONT]

(replace "/dev/hdc" with the path to your dvd drive is)
this will print the output from vlc to your terminal window and will show you what is causing the problem.[/QUOTE]

i tried your solution.this is the error from the output shown :

[00000280] main audio output warning: PTS is out of range (1266116), dropping buffer
[00000280] main audio output warning: PTS is out of range (1234139), dropping buffer
[00000280] main audio output warning: PTS is out of range (1202161), dropping buffer
[00000280] main audio output warning: PTS is out of range (1170185), dropping buffer
[00000280] main audio output warning: PTS is out of range (1138208), dropping buffer
[00000280] main audio output warning: PTS is out of range (1106232), dropping buffer
[00000280] main audio output warning: PTS is out of range (1074255), dropping buffer
[00000280] main audio output warning: PTS is out of range (1042277), dropping buffer
[00000280] main audio output warning: PTS is out of range (1010300), dropping buffer
[00000281] main video output warning: late picture skipped (1106872)
[00000281] main video output warning: late picture skipped (1066936)
[00000281] main video output warning: late picture skipped (946949)

what does it mean ?

thanks.

---

### Post by ssck on 2005-08-01
does anybody have solutions for this ? i have also enabled dma but the results are still the same.

HELP !!

---

### Post by ioan123 on 2008-06-06
I have the same problem with Hardy Heron - did anybody got a fix by any chance? Any help will be highly appreciated
Thank you
Ioan

---


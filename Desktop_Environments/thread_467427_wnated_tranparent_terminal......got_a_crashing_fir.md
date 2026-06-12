---
title: "wnated tranparent terminal......got a crashing firefox broswer...."
date: 2007-06-07
forum: Desktop Environments
---

### Post by aggie333 on 2007-06-07
hi,
   i am using fluxbox and wanted a transparent, borderless eterm at startup...i put * Eterm -f green -x --scrollbar=false --buttonbar=false --default-font-index=4 --geometry 20x20+0+0 -O -0 & * in my *.fluxbox/startup* file....the problem is i still get the default eterm background image...it is almost as though the  transparent attribute is not being recognised....and to add to the fun, firefox does not start now...it crashes saying it recieved an xserver error....this is really annoying...someone please help...

---

### Post by diatribe on 2007-06-08
try running esetroot to set your eterms transparency, also run firefox froma  terminal and see what the output is

---

### Post by aggie333 on 2007-06-09
hi diatribe,
  the output from running firefox in the terminal is
[I]$firefox
The program 'Gecko" received an X Window System error.
This probably reflects  a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window paramet
er)'.
(Details: serial 751 error_code 9 request_code 66 minor_co
de 0)[/I]

   this only started after i tried to startup a transparent Eterm at startup.....it seems to me that Eterm is trying to set its own background inspite of me telling it not to...i removed the default images in the /usr/share/Eterm/pix directory but the error remains......can some one tell me how to properly set this up please....

---


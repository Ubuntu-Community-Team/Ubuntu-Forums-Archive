---
title: "Wine :    Half Life   game problem"
date: 2005-02-11
forum: Gaming &amp; Leisure
---

### Post by dejavu on 2005-02-11
hi to all ..

i used wine to run Half life 1  and it started it and asked me for the serial number . When the correct number is entered it open an error message saying that HL requires 16-bit colors to run on .. does this means that iam runing  on 8-bit  desktop settngs  cause i dont think so since the images at wallpapers are showing good quality ... like 32 bit 
or do i need to do something with wine ?

need help
asap  ... plz

---

### Post by YokoZar on 2005-02-17
[QUOTE=dejavu]hi to all ..

i used wine to run Half life 1  and it started it and asked me for the serial number . When the correct number is entered it open an error message saying that HL requires 16-bit colors to run on .. does this means that iam runing  on 8-bit  desktop settngs  cause i dont think so since the images at wallpapers are showing good quality ... like 32 bit 
or do i need to do something with wine ?

need help
asap  ... plz[/QUOTE]
Try editing ~/.wine/config and setting your windows version to win98 (there should be a line that goes like winver=win95 or something in there)

---

### Post by valadil on 2005-02-17
I think hl1 has a problem with a 24bit desktop, which is actually the same as a 32bit one.  If you edit your XF86Config to use 16 instead of 24 you should be fine.

---

### Post by bored2k on 2005-02-26
[QUOTE=valadil]I think hl1 has a problem with a 24bit desktop, which is actually the same as a 32bit one.  If you edit your XF86Config to use 16 instead of 24 you should be fine.[/QUOTE]

im running an open gl 32bit 1024*768 hl1 game under cedega 4.2.1 , and its running smoothly .

---


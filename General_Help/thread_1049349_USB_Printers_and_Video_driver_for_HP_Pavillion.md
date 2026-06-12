---
title: "USB Printers and Video driver for HP Pavillion"
date: 2009-01-24
forum: General Help
---

### Post by bobritter on 2009-01-24
Two quick and easy, I hope.
How to set up my Epson USB printer. I did System/Admin/Printing but it didn't seem to know anything about USB printers and couldn't find mine.

Video driver support for HP Pavillion 513n. I downloaded a .tar that said it might work but I unzipped it and ran the install but nothing happened. I installed an old video card that got me going but I'd rather use the on board video if possible.

As you might guess I'm a newby at Ubuntu. Been a programmer since 40 column cards with round holes but never Linux. Did some workstation Unix back in the 90s but that was before Linux GUIs.

               Thanks, Bob Ritter

---

### Post by cariboo on 2009-01-24
In an Applications-->Accessories-->Termianl type:

```
lsusb
```

with your printer plugged in and paste the output in your next post.

You shouldn't need to dowenload any drivers for your onboard graphics adapter. Remove the addon graphics card, when you are back at the desktop, go to System-->Administration-->Hardware Drivers and there should be a listing of drivers available, select the recommended driver and follow the prompts.

Jim

---

### Post by bobritter on 2009-01-25
Printer was me being brain dead. I'd plugged it into my other machine,
No joy with the video. Without the video card XP boots OK but Ubuntu comes up with a blank, black screen. With the video card it's just the opposite. I can just go with the video card BUT this machine only has 3 IDE slots and they are all taken.  I did download a driver that said it would work but when I opened the .tar and ran the instll program a window flashed to fast to see and nothing else. Thanks for the help, Bob Ritter

---


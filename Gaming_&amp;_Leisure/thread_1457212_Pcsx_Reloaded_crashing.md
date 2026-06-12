---
title: "Pcsx Reloaded crashing"
date: 2010-04-18
forum: Gaming &amp; Leisure
---

### Post by dragonboss on 2010-04-18
So I've been playing FFVIII from ISO and reached some lighthouse area saved in the world map had a battle and then after i won pcsx crashed. I restarted pcsx crashed again after I loaded my save so then I tried it from terminal to see what it says and it gives this:

```

jeremy@Acer-lap-one:~$ pcsx
RGB not found.  Using YUV.
DFInput error: could not open device /dev/input/js1!
DFInput: starting thread...
Segmentation fault
```

What is all this about and how do I fix this?
And the controller I use is a logic3 xbox controller with a usb mod

---

### Post by hikaricore on 2010-04-18
Sadly there's nothing strange in your error output aside from a Seg fault.
Do you know if the message about the input device was occuring before?  If so it's probably not related.

---

### Post by dragonboss on 2010-04-18
No it was not happening before and I tried another game save and it worked so I think its a corrupt game save, but it did not show errors for this. The save loads and then just when the graphics are to be displayed it halts. Luckily i had a save state, but unfortunately it was taken 5 hours before. :-(

---

### Post by Whistler on 2010-04-21
try using a real dumped BIOS instead of Internal HLE BIOS (which is still buggy and causes problems with FF8 ).

---

### Post by dragonboss on 2010-04-21
I was using the SCPH1001.BIN at the time of the error, and still am.

---


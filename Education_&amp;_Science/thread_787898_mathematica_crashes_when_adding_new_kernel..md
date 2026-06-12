---
title: "mathematica crashes when adding new kernel."
date: 2008-05-09
forum: Education &amp; Science
---

### Post by kangyu29 on 2008-05-09
I'm using mathematica 6.0 in hardy. I had some problem with font rendering and multiple windows which were fixed with the help from following thread.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/197163](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/197163)

Now, I find that if I try to add a kernel from "kernel configuration options", the mathematica crashes.

Anyone knows how to fix this problem or anything I did in the first paragraph messed this up?

Thanks in advance!!!

---

### Post by WaterWater on 2008-06-27
I can confirm the same problem. Running from the console I get a steady stream of X Errors while Mathematica operates normally:

> X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RENDER)
  Minor opcode of failed request:  4 (RenderCreatePicture)
  Serial number of failed request:  23456
  Current serial number in output stream:  23459

X Error of failed request:  RenderBadPicture (invalid Picture parameter)
  Major opcode of failed request:  155 (RENDER)
  Minor opcode of failed request:  7 (RenderFreePicture)
    Picture id in failed request: 0x4400d03
Serial number of failed request:  23463
  Current serial number in output stream:  23464

Then when I choose Evaluation>Kernel Configuration Options>Add the whole kit and kaboodle dies and I'm left with:

> /usr/local/Wolfram/Mathematica/6.0/SystemFiles/FrontEnd/Binaries/Linux/Mathematica: symbol lookup error: /usr/local/Wolfram/Mathematica/6.0/SystemFiles/Libraries/Linux/libQt3Support.so.4: undefined symbol: _ZN14QUnicodeTables8categoryEj


in the console.

Any love?

---


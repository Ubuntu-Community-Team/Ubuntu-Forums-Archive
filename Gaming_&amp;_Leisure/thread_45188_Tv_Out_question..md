---
title: "Tv Out question."
date: 2005-06-29
forum: Gaming &amp; Leisure
---

### Post by poofyhairguy on 2005-06-29
Ok. I followed this fine Faq to get a working TV out:

[http://www.ubuntuforums.org/showthread.php?t=23628](http://www.ubuntuforums.org/showthread.php?t=23628)

I kinda get the concepts, but I don't know how to do what I really want to do. 

Does anyone know how to get any emulator to output to the TV? What command tells the program to use my other display?

I want to use this old computer for some SNESing, but I can't seem to get this to work.

Thanks in advance.

---

### Post by Lunde on 2005-06-29
[QUOTE=poofyhairguy]Ok. I followed this fine Faq to get a working TV out:

[http://www.ubuntuforums.org/showthread.php?t=23628](http://www.ubuntuforums.org/showthread.php?t=23628)

I kinda get the concepts, but I don't know how to do what I really want to do. 

Does anyone know how to get any emulator to output to the TV? What command tells the program to use my other display?

I want to use this old computer for some SNESing, but I can't seem to get this to work.

Thanks in advance.[/QUOTE]
 Just sharing some thoughts about the subject. I don't know what is possible or not, but maybe my input can be of some help.

If you are thinking about using TV-out from a guest OS in an emulator
Emulators like VMware, Qemu, Win4lin are also emulating the hardware, so you are not communicating directly with your graphics card and therefor have no TV-out by default.

The TV-out is sent from the Svideo output by default when the computer start, the same picture appear on both screens. Then when you start X, there need do be some configuration to output graphics to the TV or the TV turns black. 

I think there are possibuilities to run several x sessions simultaniously if this will help. 
I dont think there are problems starting an emulator in the TV screen if your television is configurated as the default screen in the X session

Maybe there are ways to send input directly to the TV-out server, I would definitly like to know about this too.

---


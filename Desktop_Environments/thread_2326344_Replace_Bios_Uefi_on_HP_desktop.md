---
title: "Replace Bios Uefi on HP desktop ?"
date: 2016-05-30
forum: Desktop Environments
---

### Post by royjg22 on 2016-05-30
Greetings

Is it possible to replace HP's Uefi bios on a cleveland GL-8 motherboard, HP desktop p6745 ?

I was able to install Amd HD7700 graphic card, but nothing better, 3 beeps and desktop does not start, many users on many forums had same problem  (tried gtx-960 and R7-370)

Some have found solution by replacing motherboard

Was wandering if disabling HP's locked Uefi may be possible or forget about this desktop for gaming

No Bios updates from HP

---

### Post by Frogs Hair on 2016-05-31
Hello and Welcome

Replacement would be difficult because the software is loaded before the OS by the OEM and is likely tailored to HP specifications. My guess is that would be why some people have replaced the mother-board.  On my laptop there is an option to disable UEFI from the boot options in the Bios set up , but I don't know if doing so would help or not. Explaining why you think disabling UEFI would help may be useful to those trying to assist you.

---

### Post by yoshii on 2016-05-31
I think to disable UEFI on HP Desktops you boot into the BIOS/UEFI settings editor by pressing ESC several times during boot until the menu pops up.  
Then it tells you which key to press to change settings.  After you press that key, it gets you into the BIOS/UEFI settings editor.  

Then I believe you have to disable Secure Boot.  After Secure Boot has been disabled, you can enable "Legacy Mode" (BIOS mode booting).  
And last but not least, you then edit the device boot order and UEFI items can be disabled there and other items moved around.  

Be sure to save the changes and allow booting to continue.  Then shut down / power down completely, and then restart.  
I believe that's how it's done.

---

### Post by royjg22 on 2016-06-07
Tried to modify secure boot, I am not even offered the option,  my tech had tried as much as he could, recommended in the future to avoid HP and Dell who sell desktops that you can only upgrade by buying new pc, they all tend to copy Apple... thank you for looking into it, will forget about trying to upgrade it, motherboards with sockets for processors of second generation hard to find

---


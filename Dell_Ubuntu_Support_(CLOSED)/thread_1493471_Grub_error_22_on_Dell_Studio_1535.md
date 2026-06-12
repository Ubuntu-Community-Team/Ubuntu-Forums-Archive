---
title: "Grub error 22 on Dell Studio 1535"
date: 2010-05-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by eyvoom on 2010-05-25
I recently, like a moron, deleted the partition that I had ubuntu installed on and combined it with my main partition to give myself more space for windows.  Windows continued to run fine, but when I restarted my comp I got a GRUB Error 22.  To be clear, this message is received after the initial Dell boot screen.  I had it set so that next a menu would appear allowing be to choose my OS (vista or ubuntu).  There is no longer any such menu, just the error 22 message.

I've been looking for solutions on these and other forums.  I've tried super grub disk to no avail (though I may have done it slightly wrong, who knows), and I've also tried to reinstall ubuntu with the install disk I made, using the .iso file (not sure if that can be used to install it from boot).  Everything I do stills gives me the damn error message.

Maybe I just need things broken down for me or something, but I can't get any of the fixes to work that I've found.

---

### Post by mikewhatever on 2010-05-27
try this howto
[http://arstechnica.com/civis/viewtopic.php?f=16&t=158228](http://arstechnica.com/civis/viewtopic.php?f=16&t=158228)
```
Here is the quick and very easy fix to remove GRUB and get Windows working again. These instructions are from Microsoft's site but with my own added tips for a brainless recovery:

1. Put the Windows Vista installation disc in the disc drive, and then start the computer (set to boot from CD in BIOS).

2. Press a key when you are prompted.

3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.

4. Click Repair your computer.

5. Click the operating system that you want to repair (Vista in this case), and then click Next.

6. In the System Recovery Options dialog box, click Command Prompt.

7. Once in the command prompt, type exactly Bootrec.exe /FixMbr and then press ENTER. You will see "operation completed successfully."

8. Reboot and set BIOS to boot from the HDD again.

GRUB will be overwritten in step 7 and Vista's bootloader will once again take control of loading your OS(s).


```

Hope that helps.

---


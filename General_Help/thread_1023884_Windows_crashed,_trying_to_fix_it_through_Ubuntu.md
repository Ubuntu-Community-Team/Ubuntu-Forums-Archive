---
title: "Windows crashed, trying to fix it through Ubuntu"
date: 2008-12-28
forum: General Help
---

### Post by jrc27 on 2008-12-28
I ran sp26595.exe on my computer when running windows xp to update the atapi driver because my DVD rw drive wasn't working.  The exe saved some files to my computer, but when i ran it, it said it couldn't apply changes to my dvd-rw drive.  The next day, windows xp won't boot anymore, it just starts to boot and then the computer restarts.  I was able to force access the windows hard drive from ubuntu, but I want to know if there's anyway to fix windows since i have access to all the files.  Is there a way to regress to a system restore point or even undo whatever changes the exe made?

---

### Post by Titan8990 on 2008-12-28
Ah, the search for the magic undo button.


Your best and probably only option is to troubleshoot this the traditional way.


Right before the Windows splash screen hit F5 and disable automatic restart. Post the BSOD stop code here.

---

### Post by HermanAB on 2008-12-28
Windows XP?  You can do a 'Repair Install' - Google for the magic key press.  A Repair Install will not erase installed applications or data.  

However, if it is a dual boot system, then that will overwrite the MBR and render Linux unbootable, so then you have to fix that too - Google for that too.

Cheers,

Herman

---

### Post by jrc27 on 2008-12-28
> **Titan8990 said:**
> Ah, the search for the magic undo button.


Your best and probably only option is to troubleshoot this the traditional way.


Right before the Windows splash screen hit F5 and disable automatic restart. Post the BSOD stop code here.

This is what came up when I pressed F5:

Windows Advanced Options Menu
Please select an option:

   Safe Mode
   Safe Mode with Networking
   Safe Mode with Command Prompt

   Enable boot logging
   Enable VGA Mode
   Last known good configuration
   Directory Services Restore Mode
   Debugging Mode
   Disable automatic restart on system failure

   Start Windows normally
   Reboot
   Return to OS Choices Menu

Should I select 'Disable automatic restart on system failure' at this screen?  What'll that do for me?

---

### Post by northern lights on 2008-12-28
> **jrc27 said:**
> Windows Advanced Options Menu
Please select an option:

   Safe Mode
   Safe Mode with Networking
   Safe Mode with Command Prompt

   Enable boot logging
   Enable VGA Mode
   Last known good configuration
   Directory Services Restore Mode
   Debugging Mode
   [COLOR="Red"]Disable automatic restart on system failure[/COLOR]

   Start Windows normally
   Reboot
   Return to OS Choices Menu

Should I select 'Disable automatic restart on system failure' at this screen?  What'll that do for me?Yup. Now it won't restart, but hang during boot. Hopefully also return an error message.

---

### Post by jrc27 on 2008-12-28
I selected disable automatic restart and got the following message on a blue screen:

A problem has been detected and Windows has been shut down to prevent damage to your computer.

An attempt was made to execute non-executable memory.

If this is the first time you've seen this stop error screen, restart your computer.  If this screen appears again, follow these steps:

Check to make sure any new hardware or software is properly installed.  If this is a new installation, ask your hardware or software manufacturer for any windows updates you need.

If problems continue, disable or remove any newly installed hardware or software.  Disable BIOS memory option such as caching or shadowing.  If you need to use safe mode to remove or disable components, restart your computer, press F8 to select Advanced Start Options, and then select Safe Mode.

Technical information:
*** STOP: OxOOOOOOFC  (OxF79D38E8, OxO6C8F963, OxF79D3848, OxOOOOOOO1) ***

---

### Post by HermanAB on 2008-12-28
I would do a Repair Install - doesn't take long.

---

### Post by jrc27 on 2008-12-28
i'm worried that if i mess up the repair install, i'll lose ubuntu and will have no access to the internet and then i really won't be able to fix windows

---

### Post by northern lights on 2008-12-28
This BSoD error can have several causes.

It sounds like bad RAM, but that's not one of them.

Did you recently install any new drivers?
Or SP3?

Anyhow, Herman's Repair install is what you'd have to do.

It shouldn't mess up your Ubuntu, and if it does, there's always the LiveCD to connect to the net.

---

### Post by jrc27 on 2008-12-29
I did run sp26595.exe ([http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv-42566-1&lc=en&cc=us&dlc=en&product=1841799&os=228]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv-42566-1&lc=en&cc=us&dlc=en&product=1841799&os=228"))to update my HP DVD-RW Drive, and I think that's what did it because it said it was going to affect my atapi driver, and when i try to run windows in safe mode, it prints out a list of file locations under a driver folder in system32 and one of them is atapi.something.  Any ideas on how to fix that?  I have a second computer with Windows XP, maybe I could copy its atapi driver file and replace the one on the crashed computer?

---


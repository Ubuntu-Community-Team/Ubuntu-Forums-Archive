---
title: "Can I change the boot sequence?"
date: 2010-01-18
forum: Desktop Environments
---

### Post by sellewe on 2010-01-18
I am using ubuntu 8.4 but have lost my desktop.  I want to reinstall the os but the boot sequence as it is set to C A (and I do not remember what the other one is)  Is it possible to get into the bios to re set this to make it start with the CD?
This has been bugging me for two weeks and I cannot seem to find an answer.  I can get to the command line part but do not have any idea what commands to type.

---

### Post by howefield on 2010-01-18
Yes, there will be key, usually displayed on the computer screen just after switching on, but before the operating system starts to load (often ESC or F2) to enter setup.

You will find the boot up sequence opetions in there.

What is the make / model of you computer.

(Mine displays 2 keys, F2 to enter setup and F12 to change the boot sequence).

---

### Post by sellewe on 2010-01-18
It is an old GMAC and I have no idea of the model.  I was originally windows 98 but I installed ubunto on it to try to find what it was like!!!  I removed a program from it and the next time I booted up I had lost the 'Desktop'

---

### Post by mk1w86 on 2010-01-18
Also try the del key to get into the BIOS. ;)

---

### Post by sellewe on 2010-01-18
The BIOS is set at A,C,SCSI but the setup is at C,A,SCSI and I have tried to alter this by pressing almost al of the @F@ keys as well as several combination of keys but cannot find any way to change this.

---

### Post by mk1w86 on 2010-01-18
> **sellewe said:**
> The BIOS is set at A,C,SCSI but the setup is at C,A,SCSI and I have tried to alter this by pressing almost al of the @F@ keys as well as several combination of keys but cannot find any way to change this.

Oh, so as I understand it now you can actually get in to the BIOS. ](*,)

Have you tried the + and - keys to change the option, also try the arrow keys.  On some BIOS's if you press enter when the option is selected it will give you a list of options to select.  When you have finished press F10 (usually) to save your changes.

---

### Post by sellewe on 2010-01-18
Sorry, I can see this on my screen but there is no wat to alter the settings as this not a command line screen which is my original problem.  Is there any to use a 'flopy disk to overcome this?

---

### Post by mk1w86 on 2010-01-18
Hmm... So you can not change ANY settings? :confused:  I assume the BIOS isn't password protected?  If it is and you don't know the password you could overcome this by clearing the CMOS.  To do this you temporarily move a jumper on your motherboard which will reset all the BIOS settings including password protection.

You might however be able to avoid this. :D You could try Smart Boot Manager which should allow you to boot from the CD drive:

[http://sourceforge.net/projects/btmgr/](http://sourceforge.net/projects/btmgr/)

You can get a floppy disk image from here:

[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

---

### Post by sellewe on 2010-01-18
Thanks for your advice.  I will work on this to see how far I can get but for now would you please send instructions as to how to perform the tip regarding the motherboard.

---

### Post by HyperHacker on 2010-01-18
To clear the BIOS settings there usually is a jumper on the board that has to be moved or removed. This can be very difficult to reach in some computers. However it sounds like you're having a different problem. Are you asked for a password when entering the BIOS settings? It's possible you're entering the "user" password which does not allow you to change those settings rather than the "admin" or "supervisor" password.

The BIOS is a little different on each model but pressing +, right arrow, page up/down, or Enter should allow you to change the settings. If you're doing something wrong it should beep. What is happening to you?

If you want to reinstall the OS I suggest you also upgrade to version 9.10.

---

### Post by sellewe on 2010-01-18
Thanks for all your help and advice.  Will sign off for now.

---


---
title: "Cannot log into Ubuntu-10.10(64-bit)"
date: 2011-03-19
forum: Desktop Environments
---

### Post by Kaushik Guha on 2011-03-19
Hello! Friends,I've installed Ubuntu-10.10(64-bit) "Maverick Meerkat" onto my system successfully.I've downloaded packages from "Synaptic Package Manager" and configured the Ubuntu-10.10 successfully.
**Problem is**: Now I am unable to log into my Ubuntu-10.10(64-bit) system.
When I press to log into Ubuntu,Linux-2.6.35-28 desktop,at the **GRUB Menu** it seems to start successfully,but eventuall comes to a **BLANK SCREEN** with a frozen cursor as " **-** " on the upper left corner of my computer's blank screen.

Please help me out.
Thank you all
-kguha

---

### Post by Krytarik on 2011-03-20
Are you able to successfully boot into "recovery mode"?

---

### Post by Kaushik Guha on 2011-03-22
Nope.
In recovery mode, the same things occur as the normal desktop mode.
While booting in(**Recovery Mode**) , boot-up scripts rolls by,the configuration window comes momentarily for a second,and then the screen goes blank with the freezing cursor on left upper portion of the screen.:shock::oops::evil:

---

### Post by Krytarik on 2011-03-22
And how about "recovery mode" -> "root shell prompt"?
Or did you mean that?

---

### Post by Kaushik Guha on 2011-03-24
^Friend,can't get access to the root prompt in the configuration window(which resides momentarily)on the screen,while booting onto the **recovery mode**.The screen becomes blank,with a forever frozen cursor.
In normal desktop mode of booting(Ubuntu-10.10),before the blank screen and freezing of cursor occurs,this message is read lastly on screen:

....
**Cannot reserve MMIO region**

---

### Post by Krytarik on 2011-03-24
> **Kaushik Guha said:**
> 
**Cannot reserve MMIO region**
I looked up those error message, and it seems neither to be related, nor serious.

Can you boot into a LiveCD?

If so, please run those script, follow the instructions on the website:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Then post its result here, in code-tags please (the #-button in the editor), or attach the text file.

Do you have another OS installed? And if so, does it run ok?

---

### Post by AndyCinDallas on 2011-03-24
Oh.... you might have the same problem I did, where I had to change the boot parameters to **acpi=off** just to get Ubuntu started.

Check [here](http://ubuntuforums.org/showthread.php?t=1713733)

Basically when Grub starts, use your arrow keys to highlight the kernel you want to boot - then press the letter "E" on your keyboard to edit the parameters.

Scroll down and find the line that starts with the word "linux" and ends with "quiet" and "splash".

Delete the words "quiet" and "splash" (this way you can see what happens during the boot-process) - and replace them with **acpi=off**

Press Ctrl+X to boot using the new parameters.

---


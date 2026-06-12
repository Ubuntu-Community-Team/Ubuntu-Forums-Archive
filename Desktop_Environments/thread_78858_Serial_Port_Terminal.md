---
title: "Serial Port Terminal"
date: 2005-10-19
forum: Desktop Environments
---

### Post by MarmiteOnToast on 2005-10-19
I am completely new to Linux so please forgive any stupid and obvious mistakes.

I've installed Ubuntu on my laptop which was surprisingly easy. I also added the 'Serial Port Terminal' application found under Accessories so that I can configure switches via my USB to serial converter. This works up to a point. You see I need to use CTRL+R on one particular switch to navigate the menu system but this key combo is used by the program itself. Can I change this?
As an alternative I tried installing the Terminal Emulator I found under Add Applications/System Tools but when I try and run it it gives me the following error:

Details: Failed to execute child process "Terminal" (No such file or directory)

What does this? How can I fix it? Are there any other Terminal emulation programs I could try that easy to install?
Any help would much appreciated.


Ta
Mark

---

### Post by steve.horsley on 2005-10-19
The only serial program I have ever found was called minicom. I can't remember offhand if ^R is used by the program, but I think it probably has a quote mode. I seem to remember that most program stuff is accessed by ^Z followed by a letter (e.g. ^ZQ to quit). 

You should find minicom in synaptic multiverse of universe. It is a text-mode command-line program, not GUI. Works nicely in a terminal window though. 

I will have to investigate this "serial port terminal" when I have time.

Steve

---


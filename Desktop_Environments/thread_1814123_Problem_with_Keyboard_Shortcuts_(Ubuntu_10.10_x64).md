---
title: "Problem with Keyboard Shortcuts (Ubuntu 10.10 x64)"
date: 2011-07-28
forum: Desktop Environments
---

### Post by cpsusie on 2011-07-28
It seems that critical shortcuts have stopped working for me.  I am  referring most especially to switching to the text terminals by  ctrl-alt-f1 .... f6 and (to a lesser extent) restarting the x server via  ctrl-alt-backspace.   
 
 Strangely, these shortcut keys work sometimes but inexplicably stop  working very frequently.  Currently, I have rebooted several times to  try to get their functionality back, without success (though they have  worked in the past).
 
 Here is my config:
 
 I have Ubuntu 10.10, 64 bit edition.  I have an NVIDIA GTX 280 graphics card and am using the nvidia proprietary drivers.
 
 By default, I boot into a CLI, not a gui.  I achieved this by editing a line in /etc/default/grub
  thus: [FONT=&quot]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"[/FONT]  Please note that I desire this behavior.  **Also, please note that the  ctrl-alt-f switching does not work even when I log into the text cli  (i.e. I can't change to tty2 or 3 etc).**
 
 I have the regular version of Ubuntu, however, I subsequently added KDE.  I use both gnome and KDE, but KDE more frequently.
 
 When I want a GUI I type: sudo /etc/init.d/gdm start, then I just log in  and choose my desired desktop environment.  **Please note that the  ctrl-alt-f whatever shortcuts do not work in Gnome or in KDE (or the  CLI). ** I CAN get back to the console by running a terminal in gnome or  kde and killing the gui: sudo /etc/init.d/gdm stop .  (I can only go back to the first tty though).
 
 I've searched these forums and googled extensively.  While I've found  people with similar problems, I've found no solutions that work for me.   Can someone please help?
 
 Thank you!

---

### Post by Russ.pinkslippa on 2011-07-29
Hi,
 
 I have no idea either, but some troubleshooting might shine some light. 
 
 e.g;
 
 - testing your keyboard (if it's a desktop) on a different computer as it could be your hardware
 - when the keys stop working open a terminal and press them singly, f5-10 shows up as ~
 - get an earlier or later version of ubuntu and boot live and see if they work then.
- see whether the Onboard keyboard program registers the keys when you  click on them (Universal Access > onBoard - enable full keyboard in  settings to get function keys) and again open terminal to see the ~ show up
 
 Regards,
 
 Russ

---

### Post by cpsusie on 2011-07-29
The function keys seem to work.  I have some stupid function lock button on the keyboard.  After depressing it once F1 gave A. F2 B. F3 C etc ....

Regardless of toggling it, I still can't get it to work.  This is a vexing problem.

---

### Post by enimeizoo on 2011-07-29
What output do you get in xev when you press ctrl, alt, F1 ... FX ?

The function keys are another thing. (If we are both talking about the fn+X combinations)

Do usual shortcuts invloving alt and control work? (eg alt+tab ...)
Are you able to define shortcuts in kde involving control? alt? the FX keys? (and do they work?)

Oh, also, try to run this command, and see (I don't think it will work, but it has the advantage of being keyboard-independent, meaning that if it doesn't work, your keyboard is probably fine)
```
xdotool key control+alt+F1
```What is the output of ?
```
cat /proc/sys/kernel/sysrq
```So, more troubleshooting suggestions than actual solution, but it is all I can think of.

---

### Post by cpsusie on 2011-08-13
Solved the problem by doing two things.  Not sure which (if either) did the trick.

I have a Microsoft Natural Ergonomic Keyboard 4000.  I loaded Gnome and went into System->Preferences->Keyboard->Layout and selected "Microsoft Natural Keyboard Pro USB" as my keyboard model.  I then clicked Apply System Wide and authenticated when prompted.

I then killed gnome and rebooted my machine. 

My machine boots into TTY1 without starting any GUI by default.  BEFORE the login prompt appeared I depress the F Lock key causing the indicator to light up.

Now  I switch among terminals at will by Ctrl-Alt-F(x) where x = tty number.  It works in a tty terminal as well as in Gnome and KDE environments.

I hope this can help someone.

---

### Post by phuongdt3 on 2011-08-15
hello,i'm a newbie,i'm having semilar problem,thanks for feedback

---

### Post by cpsusie on 2011-08-15
Hi [FONT=&quot]phuongdt3.  Glad my feedback was at least somewhat helpful to you.  What is your precise problem and what have you done to try to resolve it?
[/FONT]

---


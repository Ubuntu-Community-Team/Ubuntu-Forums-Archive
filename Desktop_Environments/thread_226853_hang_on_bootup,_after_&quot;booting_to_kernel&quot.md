---
title: "hang on bootup, after &quot;booting to kernel&quot; message"
date: 2006-07-31
forum: Desktop Environments
---

### Post by spaznrq on 2006-07-31
I am having the exact problem that was previously discussed in a closed thread, so I'm opening it up again for discussion as I have not found any open threads about this topic:

[http://ubuntuforums.org/showthread.php?t=182553&highlight=boot+rc+hang](http://ubuntuforums.org/showthread.php?t=182553&highlight=boot+rc+hang)

Basically, the problem is that everytime I boot up my computer, I would see the brown Ubuntu startup screen with all the messages and [OK]'s, then it would come up to "booting to kernel" and the screen would switch to a white text on black background (just as you would have if you hit Ctrl+Alt+Fx besides F7) and it would show "uncommand not founnd".  That isn't a typo; it actually shows as if it was displaying the "command not found" message on top of previously outputted text.

What I would have to do is try Ctrl+Alt+F6, login, then do "sudo shutdown -rF now" to reboot the computer.  The important part is that I have the -F option.  I believe it is the disk check option but I'm not sure.  I don't know if this has anything to do with why I am not able to boot up, but it does indeed boot up and bring me to the regular Ubuntu login screen that I should be getting after booting up.  I hope this can let you understand better what my problem is.

Can anyone figure this out?  I'm just leaving my computer on 24/7 to avoid having to go through all that boot process I just described.

---

### Post by greenstar on 2006-08-01
With wierd symptoms like that, text overwriting in terminal... I'd check my RAM with Memtest, dust off my processor's heatsink & fan, and check my processor via Prime95 or CPU Burn-in or something similar. Oh, yeah, dust out your power supply before you do this, so it doesn't overheat.

See if this helps,
Greenstar

---

### Post by spaznrq on 2006-08-01
Thanks for the advice.  The text overwrite happens at the same point everytime, though.  All other messages appear normal until the last message before it hangs.  You could be right, and it'll be something worth looking into, but it's a lot of work that I don't want to get into right now.

Any other suggestions?

---

### Post by greenstar on 2006-08-01
> **spaznrq said:**
> Thanks for the advice. 
Thanks for wasting my time.

> **spaznrq said:**
> You could be right, and it'll be something worth looking into, but it's a lot of work that I don't want to get into right now. 
A lot of work?? What planet are you on? What's so much work that you'd rather waste our time than try our suggestions, which *you asked for*. What's so hard about popping off the side panel, dusting off the CPU heatsink, blowing out the power supply, then running Memtest & Prime95... don't strain yourself. That would amount to about 10 or 15 minutes hands-on. You can walk away while Memtest works, same for Prime95. 

> **spaznrq said:**
>  Any other suggestions?
Not until you check those.

---

### Post by spaznrq on 2006-08-01
I apologize, Greenstar.  I didn't mean to be rude and turn down your suggestion, and I do appreciate your help.  However, I was looking to see if anybody else would have any other suggestions (either quicker fixes or more complicated) BEFORE I start hacking away with this solution.

At any rate, I was planning and will try out your solution.  I merely didn't want anyone reading this thread to think this discussion is closed because there has been one posted solution.  I'd like to hear from everyone else.

---

### Post by greenstar on 2006-08-01
> **spaznrq said:**
> I apologize, Greenstar.  I didn't mean to be rude and turn down your suggestion, and I do appreciate your help.  However, I was looking to see if anybody else would have any other suggestions (either quicker fixes or more complicated) BEFORE I start hacking away with this solution.

At any rate, I was planning and will try out your solution.  I merely didn't want anyone reading this thread to think this discussion is closed because there has been one posted solution.  I'd like to hear from everyone else.

Not a problem. I apologize if my curt response was unneccessary. The reason I suggested those 1st: if that is the problem, doing anything else first would probably not be a good idea. 

For example, if your CPU or power supply is overheating, every time you power the box on, you're killing it. I've seen CPU's & power supplies die just like that due to overheating. I've had a customer power on their PC to show me what it was doing wrong, and the power supply bit the dust right in front of both of us. Perhaps it had been run too long with the heat problem unremedied. Pet hair is also a silent killer of computers.

I'd hate for you to kill your box. I know it would wreck my day if I borked my box. Power supplies are pretty cheap. CPU's are not.

Good luck, I'll help where I can.

Greenstar

---

### Post by spaznrq on 2006-08-02
Okay, I have tried cleaning out my computer's dust.  It wasn't very dirty.  Computer's fairly new.

I have seen this issue happen to others, but I have never come across a solution to this booting problem.  Is anyone currently having this problem as well?

---

### Post by greenstar on 2006-08-02
> **greenstar said:**
> With wierd symptoms like that, text overwriting in terminal... **I'd check my RAM with Memtest**, dust off my processor's heatsink & fan, and **check my processor via Prime95 or CPU Burn-in or something similar**.

Did you test your RAM & CPU?

Greenstar

Edit:
P.S. If you don't know how to run Memtest or Prime95, let me know.

---

### Post by spaznrq on 2006-08-03
> **greenstar said:**
> Did you test your RAM & CPU?

Greenstar

Edit:
P.S. If you don't know how to run Memtest or Prime95, let me know.

Yes, please.  I'd like to know how to run either/or and whatever necessary to check it.

I rebooted last night, and actually wrote down what I'm seeing to give you a better description of my problem.  In a black screen with white characters, I see this:

....
*Starting Enterprise Volume Management System...
 ...done.
*Checking all filesystems...
*running local boot scripts (/etc/rc.local)      undcommand not founde[ok]


Exactly like that.  Now, everytime this happens, I hit Ctrl+Alt+F6 and do a "sudo shutdown -F now" and it would reboot and do something extra after coming back to *Checking all filesystems, then it would boot fine.

---

### Post by greenstar on 2006-08-03
> **spaznrq said:**
> I rebooted last night, and actually wrote down what I'm seeing to give you a better description of my problem. In a black screen with white characters, I see this:

....
*Starting Enterprise Volume Management System...
 ...done.
*Checking all filesystems...
*running local boot scripts (/etc/rc.local)      undcommand not founde[ok]


Exactly like that. Now, everytime this happens, I hit Ctrl+Alt+F6 and do a "sudo shutdown -F now" and it would reboot and do something extra after coming back to *Checking all filesystems, then it would boot fine.

Excellent info, that will probably be useful.
Please post a copy of /etc/rc.local

> **spaznrq said:**
> Yes, please.  I'd like to know how to run either/or and whatever necessary to check it.

Memtest is the 3rd option on your GRUB boot menu, here's how to get to it:

If you have a dual-boot system, Memtest will be an option in your grub menu, where you choose which OS to boot.

If you just have Ubuntu, you will have to press Esc when you see:

```
GRUB Loading Stage1.5
GRUB Loading, please wait... 
``` 
(You have to be quick. If you miss it, Ctrl-Alt-Delete and try again.)

To run Prime95, I use the UBCD - Ultimate Boot CD, available at:
[http://ubcd.sourceforge.net/](http://ubcd.sourceforge.net/)

The zip download is the faster download (the ISO is much larger & the .exe is for Windows users). The basic version (94MB) will probably serve your needs, but if you need INSERT, then download the full version (158MB).

Boot the CD, then choose [F1] Mainboard Tools, then choose either (your choice) [F2] CPU Burn-in or [F3] Mersenne Prime Test

You'll also find several tools to test your RAM on the UBCD, right below the CPU utilities, on the Mainboard Tools page.

The UBCD is so loaded with great tools that it's nearly indispensable to me. Check it out.

Greenstar

---


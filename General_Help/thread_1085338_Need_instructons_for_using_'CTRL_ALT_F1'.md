---
title: "Need instructons for using 'CTRL ALT F1'"
date: 2009-03-02
forum: General Help
---

### Post by Len Tyree on 2009-03-02
i would like to find a list of instructions for 'ctrl alt f1'.

i live in a small town in Thailand; no linux users period; local pc experts do not know 'linux' systems.  only understand windows with the questions "YOU DON'T USE/LIKE WINDOWS"??

i have to be my own technician/operator/user, etc.  there is no help except UBUNTUFORUMS and LINUXQUESTIONS.

thanks for any help. len tyree

---

### Post by orethrius on 2009-03-02
Uh, Ctrl-Alt-F1 is bound to GeTTY 1 (a text terminal, number one (1) by default).

What are you trying to do with it?

---

### Post by Len Tyree on 2009-03-03
it was passed to me for a different reason.  however, i thought it might be a way to get into the system when nothing comes up. 

i can do nothing with my defunct system now, after my harddrive burnt out, and looking at ways to get into the system when it is unusable, as unable to load ubuntu 8.04 or 8.10.

thanks, len tyree.

---

### Post by orethrius on 2009-03-03
Let me start off by saying that if you're using proprietary (ATi / nVidia) drivers, short of disabling the proprietary drivers and rebooting, you're out of luck.  This is where the nature of proprietary drivers causes issues; without full access to the source code, nobody outside of the issuing company can determine how to safely discard a GUI session (X, or Windows for the analogy) for the CLI (BASH, or DOS in continuing the analogy).

Now, that being said, I believe another analogy is in order.
The CPU of a system is its brain.
The RAM (or other memory) would be tied to its capacity to remember.
The hard drive is its heart.  It can be transplanted and - to some extent - repaired by outside parties, but the reality is that a system with a dead hard drive cannot access anything on that drive (this goes double for Windows; the drive is just as inaccessible on Vista as it is on Ibex).

Now, that being said, you can still get some of the minimum capacity of your system back with a LiveCD (questionably legal for Windows) or other bootable media, but your hard drive - and any data on it - is fried until it gets to data recovery specialists, who cannot make any guarantees of recovery.

For future reference, Ctrl-Alt-F1 is really only useful on a system that is not using proprietary display drivers, and totally useless for a dead drive.

---

### Post by heindsight on 2009-03-03
If Ubuntu won't boot at all, then Ctrl+Alt+F1 won't help you.

Once you've booted into Ubuntu, pressing Ctrl+Alt+Fn (for n=1..6) takes you to a virtual terminal, once you log in there, you get the same command line interface that you get when you open a terminal window in the graphical interface. You can use commands to find, list, copy, move or delete files edit files etc. In fact you can do anything you could do from the GUI (except of course running GUI programs), but you do it by typing commands rather than clicking with a mouse. For more info, see this: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

If your hard drive is really "burnt out" then you probably won't be able to boot anything from it, and so you won't have more any access to a terminal session than to a graphical session. I'd recommend booting from a live cd, then trying to mount your root partition from your hard disk to see if you can salvage anything.

---

### Post by orethrius on 2009-03-03
> **heindsight said:**
> If Ubuntu won't boot at all, then Ctrl+Alt+F1 won't help you.

Precisely. :-)

> **heindsight]Once you've booted into Ubuntu, pressing Ctrl+Alt+Fn (for n=1..6) takes you to a virtual terminal, once you log in there, you get the same command line interface that you get when you open a terminal window in the graphical interface.[/quote]

I'm running an ATi Radeon Mobility Xpress 200 (relative picked out the laptop, you can put down the rifle now! :-D) said:**
> If your hard drive is really "burnt out" then you probably won't be able to boot anything from it, and so you won't have more any access to a terminal session than to a graphical session. I'd recommend booting from a live cd, then trying to mount your root partition from your hard disk to see if you can salvage anything.

Right, and if it's been mounted incorrectly, that could be another issue altogether.  The general idea is that we don't have mounting information, and without that, we can't really determine whether this drive is truly dead or merely incorrectly configured.

In light of this, does the drive make strange churning noises for large lengths of time?  Has it booted *anything* correctly in recent history?

---

### Post by Len Tyree on 2009-03-03
thanks orethrius and hindsight.

the HD was in good condition, only 2.5 yrs. old; worked fine, until one day it only booted part way.  tried to re-boot several times until i smelled heat like that from an electrical appliance.
took it to pc shop, guy does not understand linux but should know how to check out HD, said it was fried.  bought new HG (it was clean) and am now trying to install my ubuntu 8.04 on it.  was running ubuntu 8.10, but do not have ubuntu 8.10 CD.
ubuntu 8.04 will not install from CD?  (says it installed, remove CD, press enter, etc), but then will not run. 
have backup on USBdrive, but it will not load onto system.  therefore, thought maybe CTRL+ALT+F1 would provide an answer.  sorry.

if you can think of anything i can do, please let me know.
thanks, len tyree.

---

### Post by heindsight on 2009-03-03
Can you please describe exactly what happens when you try to boot without the CD?

Perhaps you should make sure that your BIOS is configured to boot off your new HD.

---

### Post by Len Tyree on 2009-03-03
thanks heindsight

your q?
>Can you please describe exactly what happens when you try to boot without >the CD?
a.  the little bubble on the screen just goes back and forth, back and forth, etc, until  get a message from (fend???) saying to type help for a list of cammands.  type 'help', brings up list, but do not know what they  do, can't see anything that might help?   

uour statement.
>Perhaps you should make sure that your BIOS is configured to boot off your >new HD.
good idea.  i will look at that.

thanks, len tyree.

__________________

---

### Post by dcstar on 2009-03-03
> **Len Tyree said:**
> 
......
ubuntu 8.04 will not install from CD?  (says it installed, remove CD, press enter, etc), but then will not run. 
......

When you install, select the "Advanced" options near the end of the install phase and manually specify where Grub is to be installed (as the auto selection sometimes does not work).

---

### Post by heindsight on 2009-03-04
> **Len Tyree said:**
> the little bubble on the screen just goes back and forth, back and forth, etc, until  get a message from (fend???) saying to type help for a list of cammands.  type 'help', brings up list, but do not know what they  do, can't see anything that might help?

Do you mean you see a black screen with an Ubuntu logo and a progress meter under that? Like in the picture in [this post]("http://ubuntuforums.org/showpost.php?p=6192477#post6192477")? If that's the case, then ubuntu is starting to boot, but if you don't get to a login screen then something is probably going wrong somewhere during the boot process.

I'm afraid I have no idea what "fend" is. Perhaps you could post the exact text you see on the screen when it stops booting? If it's not in english, could you perhaps try to translate it?

---

### Post by Len Tyree on 2009-03-05
to dcstar...

did that, 3 times as there are/were 3 types of set-up

same results.  says it loaded, but will not run??

len tyree

---


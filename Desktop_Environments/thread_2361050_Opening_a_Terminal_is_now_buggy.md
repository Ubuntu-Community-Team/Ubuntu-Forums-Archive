---
title: "Opening a Terminal is now buggy?"
date: 2017-05-11
forum: Desktop Environments
---

### Post by cybrsaylr on 2017-05-11
Used to hit Ctrl, Alt and T, on my keyboard to open up a Terminal in the past with no issue forever. However the last few days have to hit Ctrl, Alt and T several times on keyboard before a Terminal opens! Any ideas how to remedy this and get it back to working the first time those keys are pressed?

---

### Post by UbuntuWho on 2017-05-11
I assume by your signature that it's one of your laptops. Please tell which one, as there are variances between Ubuntu 14.04 and 16.04.

---

### Post by cybrsaylr on 2017-05-11
Actually it's my i7 desktop running 16.04LTS.

---

### Post by vasa1 on 2017-05-11
Is all other keyboard usage satifactory?

---

### Post by UbuntuWho on 2017-05-11
Okay, so you're having trouble opening a terminal. Hmmm, according to the specs you gave, it can't be from being too slow as you have a relatively fast CPU and plenty of memory installed. Also, after looking up a picture of your computer, I'm kicking myself for not noticing the word "desktop" from the start! I'll propose some ideas and see where we can go from there:

[LIST]
[*]*Can junk get under your keys?* You may need to use a can of compressed gas made for cleaning out debris from within your keyboard. 
[*]*Did this happen after an update?* Believe it or not, not all updates are beneficial, as some can introduce new bugs to programs. If the answer is "yes", you may need to revert to a previous version. 
[*]*Can you open other programs via key combinations?* If not, check your keyboard shortcut settings. If they seem fine, something else is wrong; we'll take it from there. 
[/LIST]

---

### Post by oldos2er on 2017-05-12
What does hitting Alt-F2 and entering *xterm* do?

---

### Post by cybrsaylr on 2017-05-12
> **vasa1 said:**
> Is all other keyboard usage satifactory?

Appears so but am testing them out more now.

---

### Post by cybrsaylr on 2017-05-12
> **UbuntuWho said:**
> 

[LIST]
[*]*Can junk get under your keys?* You may need to use a can of compressed gas made for cleaning out debris from within your keyboard. 
[*]*Did this happen after an update?* Believe it or not, not all updates are beneficial, as some can introduce new bugs to programs. If the answer is "yes", you may need to revert to a previous version. 
[*]*Can you open other programs via key combinations?* If not, check your keyboard shortcut settings. If they seem fine, something else is wrong; we'll take it from there. 
[/LIST]

Just used compressed air, vacuumed and cleaned out keyboard. Haven't done this in years.  There was more debris than expected in spite of keeping keyboard covered when not in use! Testing out keyboard shortcuts via Super key and most seem to run good. Opening a Terminal via Ctrl, Alt, T, is really the only shortcut I've used. It works better now but still buggy opening a Terminal. 

My keyboard has 2 pairs of Ctrl, Alt keys and the one Ctrl key on the lower left may be the problem! Also the Alt key on the right is not responding also! Suspect this may be the problem. 

Don't recall if this started after any updates.

Played around with those other Shortcut key combinations and most seem to run fine, just that they were never used much in the past.

---

### Post by cybrsaylr on 2017-05-12
> **oldos2er said:**
> What does hitting Alt-F2 and entering *xterm* do?

I get this:

[IMG]https://s17.postimg.org/gueh920cf/Screenshot_from_2017-05-12_12-08-46.png[/IMG]

---

### Post by oldos2er on 2017-05-12
You typed in xterm as the run command?

---

### Post by vasa1 on 2017-05-12
And try another keyboard while you're at it.

---

### Post by cybrsaylr on 2017-05-12
> **oldos2er said:**
> You typed in xterm as the run command?

May have? Don't really know what the function is of that is....

Just posted what came up when hitting Alt-F2.

---

### Post by cybrsaylr on 2017-05-12
> **vasa1 said:**
> And try another keyboard while you're at it.
Doing that.
 
Current keyboard is 2 years old and works fine. Picked it because it has illuminated keys which I like for use at night.

Am typing this now with my original 7½ year old keyboard that came with this Dell i7 and never had any problems other than it not being illuminated. Super Key shortcuts work but Ctrl, Alt, T keys when pressed on this OEM keyboard also do not open a Terminal using either of the pairs of Ctrl, Alt keys on it! 

OK, after several attempts hitting Ctrl, Alt, T keys, a Terminal just opened using the OEM Dell keyboard. 


So it appears both keyboards are not the problem here.....

---

### Post by oldos2er on 2017-05-12
> **cybrsaylr said:**
> May have? Don't really know what the function is of that is....

Just posted what came up when hitting Alt-F2.

In post #6 I asked you to run Alt-F2 and enter xterm. Trying to determine if there's a bash issue that needs to be resolved.

---

### Post by cybrsaylr on 2017-05-12
> **oldos2er said:**
> In post #6 I asked you to run Alt-F2 and enter xterm. Trying to determine if there's a bash issue that needs to be resolved.

OK, not at all familiar with this but do that and get this:
[IMG]https://s29.postimg.org/dty1oggqv/Screenshot_from_2017-05-12_13-26-34.png[/IMG]

---

### Post by oldos2er on 2017-05-12
So xterm works if you need a terminal, that means there might be an issue with gnome-terminal (what you see if you run Ctrl-Alt-t). Perhaps someone who's more familiar with gnome-terminal can help you from here.

---

### Post by cybrsaylr on 2017-05-12
> **oldos2er said:**
> So xterm works if you need a terminal, that means there might be an issue with gnome-terminal (what you see if you run Ctrl-Alt-t). Perhaps someone who's more familiar with gnome-terminal can help you from here.

Yes I have a couple way of opening a Terminal. It's just that Ctrl-Alt-t was the easiest way, until things got buggy a few days back.

---

### Post by oldos2er on 2017-05-12
Ok, I guess I misunderstood your problem then; it's with Ctrl-Alt-t specifically, and not gnome-terminal (which I assume from what you said runs ok).

---

### Post by cybrsaylr on 2017-05-12
Yes it's specifically the shortcut Ctrl-Alt-t, that is now acting buggy.

---

### Post by UbuntuWho on 2017-05-13
Are there any other keyboard shortcuts that might have set themselves to CTRL+ALT+T? I know that programs can conflict when more than one are set to the same shortcut, especially when they're running. So:
[LIST=1]
[*]Make sure no program is running. This includes any program you may have started that is still running after you closed its window. If programs are running, you can use the "kill" command in a terminal or simply log out and back in again. If that doesn't fix it, reboot. 
[*]Check all system shortcuts to make sure others are not set to CTRL+ALT+T. You should be able to find them by checking Unity's settings. 
[*]Try assigning the GNOME Terminal a new shortcut. Make sure it isn't one already in use. 
[/LIST]
 If it still doesn't work, then are *you* in a pickle! It's probably a software bug, and there's not much else you can do unless you can edit the source code. :confused:

---

### Post by vasa1 on 2017-05-13
> **cybrsaylr said:**
> Yes it's specifically the shortcut Ctrl-Alt-t, that is now acting buggy.
Try making an additional keyboard shortcut for the terminal: Ctrl+Alt+G (or some other letter that isn't already used with Ctrl+Alt).

---

### Post by cybrsaylr on 2017-05-14
> **vasa1 said:**
> Try making an additional keyboard shortcut for the terminal: Ctrl+Alt+G (or some other letter that isn't already used with Ctrl+Alt).

Just did that!

Created a new shortcut via this method: [https://www.google.com/search?client=opera&q=how+to+create+keyboard+shortcuts+on+mac&sourceid=opera&ie=UTF-8&oe=UTF-8#q=how+to+create+keyboard+shortcuts+on+ubuntu+16.04](https://www.google.com/search?client=opera&q=how+to+create+keyboard+shortcuts+on+mac&sourceid=opera&ie=UTF-8&oe=UTF-8#q=how+to+create+keyboard+shortcuts+on+ubuntu+16.04)

At first going into Keyboard > Shortcuts, there was nothing there to launch a terminal. So set one up as per direction Ctrl-Alt-C. It worked! Then changed it and reset it again to Ctrl-Alt-T and it works fine as it used to. 

Figure something buggy must have occurred causing this to fail in  the first place. However now it seems to have been corrected.

Thanks for the help guys.

---

### Post by UbuntuWho on 2017-05-14
I'm happy to see that your issue is resolved, but it looks like it could occur again, as we still don't truly know what caused it. Please keep this thread open in case it does happen again.

EDIT: Wait, no shortcut was set up? Then it's a wonder it worked in the first place!

---

### Post by cybrsaylr on 2017-05-16
UbuntuWho good point. 
I've been using Linux 10 years now and have noticed buggy things like this do happen on occasion. Sometimes after an update or sometimes just some software glitch. In this case not sure what caused it. 

Another thing that happened which I have no clue why, was I've always set my PC to turn off the screen when inactive for 10 minutes. At times this messes up and screen stays on forever! Right now it's working and shuts off monitor after being inactive for 10 minutes......most of the time. Gotta love technology.

---

### Post by vasa1 on 2017-05-16
> **cybrsaylr said:**
> ...
Another thing that happened which I have no clue why, was I've always set my PC to turn off the screen when inactive for 10 minutes. At times this messes up and screen stays on forever! Right now it's working and shuts off monitor after being inactive for 10 minutes......most of the time. Gotta love technology.
If you want support on that, please start a new thread with an informative title in the appropriate subforum. Thanks!

---


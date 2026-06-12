---
title: "Hardware Acceleration for Multiple X Users"
date: 2005-10-26
forum: Desktop Environments
---

### Post by greathoj on 2005-10-26
I was wondering if it would be possible to allow several simultaneously logged in users to utilize hardware acceleration in X.org?  Typically, I'm constantly logged in, and since I was the first to login to X, I get the hardware acceleration.  My girlfriend has her own account, however, and when she clicks the "switch user" button and logs in, she does not get acceleration (she _does_ get it when she's the first to login).

So that's my question.  I've looked around for a solution, but haven't found any.  I'm using the 32-bit version of Ubuntu 5.10 (k7 kernel) on an AMD 64 3200+ with an ATI Radeon 9600 Pro (proprietary drivers).  Motherboard chipset is nForce 3.

I'm also a bit curious about the switch user capability in Gnome.  If we are both logged in and one of us hits that button ("switch user") from XScreenSaver, we are not taken to a login screen.  Instead, a dialog asking if we want to go to a currently open display pops up UNDERNEATH of XScreenSaver's root window, which means that to interact with said dialog, we have to type in the other persons password to unlock the system.  Is there a way to force that dialog to appear on top of XScreenSaver?  Without this capability, the switch user functionality is essentially worthless.

---

### Post by Dr. Nick on 2005-10-27
I never has used the switch user function, what I do occasionaly is a "new login"
Applications-System Tools-New login

Once you do that use ctrl+alt+f7 to get back to the 1st login, may end up with a locked screen so you will need to hit a key to get switch off the screensaver then give your password

I believe I get hardware accel in both as the nvidia logo appears at both logins

---

### Post by greathoj on 2005-10-27
Perhaps this is an ATI problem, then...

Any ATI users have any advice on this matter?

At either rate, thanks for your input.  I knew about the Ctrl+Alt+F7 thing, but I don't particularly think that's a good solution (especially for my somewhat computer-illiterate girlfriend).  Maybe when I have some free time I can take a stab at writing a patch to fix that switch user issue.  Though by then, someone else will probably have fixed it.  Damn my lengthy, non-stop homework assignments!

---


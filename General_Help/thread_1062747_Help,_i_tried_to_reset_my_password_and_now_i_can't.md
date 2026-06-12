---
title: "Help, i tried to reset my password and now i can't boot ubuntu!"
date: 2009-02-07
forum: General Help
---

### Post by RandomDudeWithComputer on 2009-02-07
I took someone's advice, entered a root shell to reset my password, it didn't work, and now every time i try to boot ubuntu it goes to the root shell! Please help. Anybody. I'm desperate.

---

### Post by Monotoko on 2009-02-07
try running startx from shell

and why were you trying to reset the root password from shell?
Just use sudo and your own password, no need to touch root.

---

### Post by RandomDudeWithComputer on 2009-02-07
I lost my username too T_T i'm pathetic

---

### Post by RandomDudeWithComputer on 2009-02-07
Thx, but how do i run startx?

---

### Post by RandomDudeWithComputer on 2009-02-07
I'm a complete moron to ubuntu

---

### Post by ByteJuggler on 2009-02-07
What exactly happens when you boot?  Please tell the exact message(s) if any that you're given particularly the last ones before you're dropped at a prompt.

Edit: Normally you'd run "startx" by just typing that and pressing enter.  However, running X from a root shell is not advised, you should run it from your own account, so I'd like to first fix your password issue then figure out why X isn't starting as it should.

---

### Post by RandomDudeWithComputer on 2009-02-07
I just wish there was some way to completely restart it

---

### Post by RandomDudeWithComputer on 2009-02-07
It says too much for me to memorize, but it shows 2 options

Choice 1. Safely remove hardware from windows
Choice 2. Force it using the following command line:




Then it shows a command prompt

---

### Post by RandomDudeWithComputer on 2009-02-07
By the way thx for helping

---

### Post by RandomDudeWithComputer on 2009-02-07
> **RandomDudeWithComputer said:**
> It says too much for me to memorize, but it shows 2 options

Choice 1. Safely remove hardware from windows
Choice 2. Force it using the following command line:




Then it shows a command prompt

Is that enough information?

---

### Post by RandomDudeWithComputer on 2009-02-07
If i run startX from shell what will it do?

---

### Post by Monotoko on 2009-02-07
Hmm, do you have a Windows partition that wasnt shut down properly??

It will start the GUI, but as the other guy said, its not advisable from root, sorry i didnt think of that

---

### Post by DrMelon on 2009-02-07
Whoa whoa whoa, slow down! :D
Forums don't provide instant answers; we usually think and devise ways of solving the problem.

What happens when you try to boot Ubuntu? Does it just boot Windows instead, or are there error messages?

---

### Post by RandomDudeWithComputer on 2009-02-07
[Windows Partition] If i knew what that was, maybe i'd have an answer T_T

---

### Post by theozzlives on 2009-02-07
Are booting off USB???

---

### Post by RandomDudeWithComputer on 2009-02-07
> **DrMelon said:**
> Whoa whoa whoa, slow down! :D
Forums don't provide instant answers; we usually think and devise ways of solving the problem.

What happens when you try to boot Ubuntu? Does it just boot Windows instead, or are there error messages?

Sorry. 
It goes directly to the shell, no error or anything

---

### Post by RandomDudeWithComputer on 2009-02-07
> **theozzlives said:**
> Are booting off USB???

Not sure. I installed ubuntu off windows then booted it

---

### Post by RandomDudeWithComputer on 2009-02-07
Note: i am a moron to ubuntu. Try to use small words. :D

---

### Post by RandomDudeWithComputer on 2009-02-07
Thanks helping by the way :D

---

### Post by ByteJuggler on 2009-02-07
> **RandomDudeWithComputer said:**
> Is that enough information?

The options you list is not familiar as Linux/Ubuntu messages to me, it smells of Windows tbh.  Do you have a dual-boot setup?  Exactly what does the prompt/command line you're given look like?  (E.g. what text is on the prompt line?)

---

### Post by RandomDudeWithComputer on 2009-02-07
I have windows and ubuntu set up, if thats what you mean. Now it says "Could not mount the partition /dev/disk/by-uuid/A4EC4C22E000E1C3. You can fix this problem by rebooting into windows, log on, enter 'chkdsk /r' reboot, log onto windows, then try to boot ubuntu again." Is that any help?

---

### Post by RandomDudeWithComputer on 2009-02-07
> **Monotoko said:**
> Hmm, do you have a Windows partition that wasnt shut down properly??

It will start the GUI, but as the other guy said, its not advisable from root, sorry i didnt think of that

Maybe the warning meant that. [Windows partition]
How do i shut down a windows partition?

---

### Post by RandomDudeWithComputer on 2009-02-07
Help please?

---

### Post by ByteJuggler on 2009-02-08
> **RandomDudeWithComputer said:**
> Maybe the warning meant that. [Windows partition]
How do i shut down a windows partition?

When you run Windows and you shut down, the Windows filesystem is shut down as well in an orderly fashion, and a flag is set to indicate this.  If on the other hand you reset your PC or turn it off without shutting down Windows, then the Windows filesystem was also not shut down in an orderly fashion and it will be left in an inconsistent state, with the flag set to show that the system was not shut down properly.  To prevent Data loss, Linux/Ubuntu will refuse to mount Windows/NTFS partitions that have not been shut down properly as explained above.  The way to fix this, is to boot into Windows first, allowing Windows to check and clean up any inconsistencies on the filesystem, then shut it down normally again, after which Linux/ubuntu will be able to mount it properly again.

---

### Post by ByteJuggler on 2009-02-08
> **RandomDudeWithComputer said:**
> I have windows and ubuntu set up, if thats what you mean. Now it says "Could not mount the partition /dev/disk/by-uuid/A4EC4C22E000E1C3. You can fix this problem by rebooting into windows, log on, enter 'chkdsk /r' reboot, log onto windows, then try to boot ubuntu again." Is that any help?

What's changed since the last time/what have you done to now get a different message?  (My guess would be you booted into Windows and then didn't shut it down properly as explained in the other post, as evidenced by the above message.)  

You still haven't told me exactly what the prompt you get left at when you try to boot looks like.  I need to know this to have an idea of whats actually happening and where you're left at when you boot, which would help me help you (albeit, the above message is definitely an Ubuntu/Linux message.)

---


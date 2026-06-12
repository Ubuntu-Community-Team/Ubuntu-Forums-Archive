---
title: "Desktop icons not showing up"
date: 2016-09-14
forum: Desktop Environments
---

### Post by stuart_jones2 on 2016-09-14
Last night my computer was running fine, this morning however after logging in just the screen saver appears, no side or top bars.
I found this thread 
[https://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears#76951](https://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears#76951)

and used the settings manager to enable Unity and also the post marked 130, but nothing
I'm running 16.04 LTS on a Packard bell Desktop
Many thanks in advance for any help

---

### Post by rmgak2 on 2016-09-15
I am having problems with launcher icons and start menu not showing up on my account with I logo in with Ubuntu 16.04  I can login to my guest account and launcher icons and start menu show up.  Any ideas on how to solve this problem?

---

### Post by steve3332 on 2016-09-17
A few days ago there was a couple of threads regarding the same problem and the solution seemed to be to simply run Bleachbit and let it clear out the system cache:

[https://ubuntuforums.org/showthread.php?t=2337115&page=4](https://ubuntuforums.org/showthread.php?t=2337115&page=4)

After doing so my system has been fine with no lingering effects though I have no idea what happened to cause the problem.

---

### Post by stuart_jones2 on 2016-09-17
Thanks for your reply steve3332,
I use Bleachbit quite regularly and think I had used it a few times in the days leading up to this problem.
My question though is how do I use it when the icons do not show up, I can open a terminal through right click on the desktop, is there a command I need to use?
Sorry I'm still very new to Ubuntu

---

### Post by steve3332 on 2016-09-18
On the icon-less desktop I right clicked with the mouse, opened a terminal window and typed "bleachbit" minus the quotations. Made the appropriate selections and let 'er rip.

---

### Post by stuart_jones2 on 2016-09-18
Thanks steve 3332,
ticked all the box's marked cache and ran bleachbit, had to hard shut down, but now life is good again. 
Thanks for your time and help

---

### Post by rmgak2 on 2016-09-19
Running Bleachbit worked for me for me.  I had to launch Firefox (gksudo firefox) from the terminal command line since I could not use the launcher icons . Download the software using Firefox and install the software.  I cleaned out the system file and it work!  Thank you.

---


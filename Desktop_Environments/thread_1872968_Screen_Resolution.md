---
title: "Screen Resolution"
date: 2011-10-31
forum: Desktop Environments
---

### Post by Uchiha_Kori on 2011-10-31
Hello all.
 
I am very new to Ubuntu, and Linux in general. I am currently dual booting Ubuntu beside Windows 7 Ultimate. In windows 7, I can set my screen resolution to 1600x1200, and this is the configuration I have got used to. In Ubuntu, however, the resolution never goes higher than 1060x768. Is there any way I can alter this to my 1600x1200 liking?
 
Thanks in advance,
Kori

---

### Post by Paddy Landau on 2011-10-31
It seems as though you don't have the right driver for your screen.

Open Additional Drivers and see whether or not any drivers are listed. If they are, you may need to enable them, and log out and in again.

I presume that you have opened your Monitors application and tried to change it there?

---

### Post by Uchiha_Kori on 2011-11-10
Yes, I have the correct driver, this is not the cause. I can achieve the resolution I want, however it is not permanent. I used the Newmode and Addmode commands in terminal, but I can't figure out how to make them permanent. Any ideas help?

-Thanks,
Kori

---

### Post by Paddy Landau on 2011-11-11
I have never even heard of the commands Addmode and Newmode. I use only the GUI to do anything with my monitors.

What application did you install to use Addmode and Newmode? I wonder if you would have success if you were to uninstall that program, reboot, and use the GUI that comes with Ubuntu?

---

### Post by Uchiha_Kori on 2011-11-11
I'm using xrandr --addmode and xrandr --newmode in the terminal. GUI is a new term to me, something I have never heard of before. Is it included in Ubuntu 11.04?

---

### Post by Paddy Landau on 2011-11-11
xrandr is quite an out-of-date way of doing things.

GUI simply means Graphical User Interface -- in other words, don't use the command line, but use programs with the mouse (such as Firefox, Writer, and so forth).

Forget about xrandr. Instead:


[LIST]
[*]Log out and in again.
[*]Start the *Monitors* application.
[*]Change what you need to change there.
[*]Log out and in again to test.
[/LIST]

---

### Post by Uchiha_Kori on 2011-11-12
Thanks for that tip. I finally configured my graphics setting using a lot of xrandr commands and the xorg.conf (I had to make the xorg.conf file myself, but succeeded). Everything is running smooth now. 

To be honest, I had little respect for Ubuntu, Linux, and the people who use it at first. However, I decided to break away from Windows 7 and try Ubuntu. I was shocked at how much more comfortable Ubuntu is compared to Windows. Needless to say, I'll never return to Windows 7 again. I'll use Linux from now  on.

---

### Post by Paddy Landau on 2011-11-12
> **Uchiha_Kori said:**
> Thanks for that tip. I finally configured my graphics setting using a lot of xrandr commands and the xorg.conf (I had to make the xorg.conf file myself, but succeeded). Everything is running smooth now.
You have done it the most difficult way possible! I'm glad you have it solved. Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

However, when the time comes to upgrade, I think you'll have to go for a clean install rather than an upgrade, otherwise you could hit the same problem again. Next time use the *Monitors* application.

> **Uchiha_Kori said:**
> To be honest, I had little respect for Ubuntu, Linux, and the people who use it at first. However, I decided to break away from Windows 7 and try Ubuntu. I was shocked at how much more comfortable Ubuntu is compared to Windows. Needless to say, I'll never return to Windows 7 again. I'll use Linux from now  on.
Well, it's all a personal opinion, and if Ubuntu serves you, that's great. I have also left Windows with much relief, but some people prefer Windows. It will be interesting to hear the comments from people once Windows 8 comes out; it is very different.

---

### Post by ErtanERBEK on 2011-11-12
Sorry, I wrong write.

---


---
title: "Unable to use mouse or switch windows in Unity or Gnome"
date: 2011-07-13
forum: Desktop Environments
---

### Post by steelstiletto on 2011-07-13
I recently installed Ubuntu desktop, since I had been running my server as Ubuntu Server on a guest OS on Windows 7 and never really used the Windows part of the computer. Since then, I've been unable to use the mouse in a graphical environment for longer than a few minutes without it starting to act crazy. The mouse moves around normally, but won't respond to clicks (left, middle, or right) but the keyboard shortcuts still work. I'm not sure if things have changed since I last used Gnome though, but Alt+Tab is not working for me either when this happens. Sometimes, the active window is even behind another window, and isn't pulled to the foreground.

After a bit of frustrated clicking and jamming of buttons on the keyboard, sometimes the mouse kind of starts working because I'll notice a right click menu open. But, I am still unable to move windows or click on them to bring them to the foreground, and my mouse presses only work on the current window. And then, eventually, after about a minute or so, it'll stop respond again too.

I saw in one thread that someone had dead spaces where he couldn't click, so he installed and ran Gnome and that fixed it, but I tried using Ubuntu Classic and it is still giving me the same behavior. I'm actually posting this message now in links, because I can't use Firefox or Chrome well enough when it's hidden behind other windows.

Any help or ideas would be appreciated, thanks in advance.

---

### Post by killabee44 on 2011-08-06
I am going through the same hell. This almost makes the computer unusable. WTH is going on? I am looking all over for an answer but nothing I have tried has worked. I am using Lucid..

Someone please chime in if you have found an answer!

---

### Post by arch8472 on 2012-01-02
I have the same problem with Ubuntu 11.10 which I have just installed.  Very frustrating.  It's very difficult and sometimes impossible to change an active window to another window using the mouse.  Often I can open a new window which then sits in front of the active window... yet my mouse is still controlling the original window which is behind the new one!  There seems to be some sequence of clicks that allows me to swap active window occasionally but it seemingly happens at random.  Alt-tab doesn't work either.  Once I have managed to obtain the correct active window my mouse works perfectly.

Any help is greatly appreciated.

Thanks!

---

### Post by dave-o-dave on 2012-01-10
I think I have the same problem. At least it sounds the same. 
For details, please see the link. 
[http://ubuntuforums.org/showthread.php?t=1906918](http://ubuntuforums.org/showthread.php?t=1906918)

There are some suggestions about reinstalling all the packages related to the mouse from the synaptic. 
Another is to reinstall compiz. 
Another is to try
sudo aptitude purge irqbalance 

none of these worked for me, but maybe they do for one of you. 

I also saw a solution about a problem with the clocksource suggesting to change it. 
Maybe some of those ideas help you guys.

---

### Post by dave-o-dave on 2012-01-11
what kind of mice are you guys using? Although my problem sounded the same as yours, I now believe mine is a hardware problem. 
I was using a logitech external wireless mouse. It turned out there were problems in my windows host, not just the linux guest. But they were much less subtle. 
Are you perhaps also using external mice?

---


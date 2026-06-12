---
title: "Another Microphone Dilemma"
date: 2009-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tacantara on 2009-05-08
I just did a reinstall of Jaunty on my XPS M1330, using the version for Dell PCs.  The built-in microphone only picks up sound when I put my face right on the screen, and I can't get my headset mic to work at all.  I've tried just about every combination of settings in the terminal version of alsamixer, but nothing seems to work.  I also took out pulseaudio, rebooted, and still no change.  Does anyone have a fix for this, or am I doomed to making Skype calls with my face against the screen ad infinitum?

---

### Post by x C0MMAND0 x on 2009-05-08
[http://ubuntuforums.org/showthread.php?t=1048568](http://ubuntuforums.org/showthread.php?t=1048568) 

That was my original thread.  You can use it as a guideline.  I have since updated to Jaunty and everything is working just fine for me on my Dell XPS M1330.  I Would do the following and see where you are:

```
sudo apt-get install kmix
```

In kmix, make sure capture is checked and Maximized, and make sure Digital Mic 1 is selected.

[IMG]http://img117.imageshack.us/my.php?image=kmix.png[/IMG]

For your regular Sound Manager, Open up Volume Control and Under OPTIONS make sure that is set to Digital Mic 1, and under RECORDING that everything is maximized.

Sometimes, if you click on preferences, there will be a +20db Mic Boost.  If so, ENABLE THAT.

Best of luck.

---

### Post by tacantara on 2009-05-08
Thanks, Commando :)   After I posted this thread, I found your original post on the same topic, and I applied the kmix changes that you suggested.  Works like a charm!  I tested it on Skype, and it worked perfectly.

....and to think I went through a complete reinstall of Ubuntu, only to go back to a KDE package for the audio fix.  I had KDE installed, and was using it for everything (essentially had a Kubuntu system running, with my Ubuntu/Gnome as an alternate for boot).

---

### Post by x C0MMAND0 x on 2009-05-08
I'm glad it worked out for you.  I use Skype a few days a week to stay in touch with my girlfriend, who unfortunately lives an hour away.

---

### Post by josephe on 2009-09-08
Hi Seem to work for me to so thanks very much was about ready to leave Skype in a VM or find another Voip client for Ubuntu

Joseph

---


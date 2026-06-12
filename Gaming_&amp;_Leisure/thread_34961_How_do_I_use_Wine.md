---
title: "How do I use Wine?"
date: 2005-05-17
forum: Gaming &amp; Leisure
---

### Post by Goober on 2005-05-17
Ok, this should be a relatively simply question, I think.  Using the recent HowTo in the Customization Section, I successfully installed Wine.  I even successfully installed a couple programs, one is a game, the other is some drivers and such for my WebCam.  But, how do I run those programs with Wine?

I know that I type in "wt2" in a Terminal, and you can get to the WinTools menu, where you can select things such as Control Center, Registry Editor, Show Installed Software, Uninstaller, Simulate a Windows Reboot, and the like.  I assume that is the menu that I use to run my installed programs, but how?  Which option?

Thanks in advance for your answeer,

Goober.

---

### Post by thierry on 2005-05-17
Did you try just clicking on the .exe file ? If you right click it should give you the option of starting the file with wine...

If it works, you can add an entry to your menu :

wine ~/.wine/the path to the file or wine /the path to your windows partition.

Remember wine is far from working with everything.

---


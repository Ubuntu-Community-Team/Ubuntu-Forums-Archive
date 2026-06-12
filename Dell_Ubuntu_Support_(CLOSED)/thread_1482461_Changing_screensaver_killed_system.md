---
title: "Changing screensaver killed system"
date: 2010-05-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fritzk on 2010-05-13
Hello, I'm looking for some help to change my screen saver back to what it was--Cosmos.  I haven't seen anyone else who has had a similar problem.

Here's my problem.  About May 5th, I upgraded from Ubuntu 9.10 to 10.04.  Everything seemed to be working OK until today when I changed my screen saver from Cosmos to Ant spotlight.  After I changed it, my system hung with my monitor turning black.  At about 2 second intervals, I get a band of black and white bars about 1/8-inch wide about one-third of the way from the top of the screen.  

As long as my screen saver doesn't kick in, my system works fine. 

I've rebooted and tried changing the screen saver back to Cosmos several times, but when I go through System-> Preferences-> Screensaver, my system crashes about two seconds after I click on Screensaver.

According to Ubuntu Help, I should be able to click on System-> Preferences-> Appearance-> Visual, however, on my Ubuntu 10.04, the first item under System-> Preferences is "Broadcast Preferences."  There is no option for "Appearance."  Could be an error in the doc?

My system is a Dell 2400 desktop computer with 2 GB of RAM, and a generic Dell M992 19-inch monitor.  I'd appreciate any help you can provide.

Thanks, Fritz

---

### Post by binary10 on 2010-05-13
Sounds like wrong settings in the X11 config given you corrupted graphics. 

What graphics card is in that box 'lspci | grep VGA', then search the forum to see if it comes up as requiring a bit of extra config.

---

### Post by Richard85 on 2010-06-07
I have the same problem on my dell desktop. It's related to the intel graphics card that I have. I've tried one of the workarounds in the release notes but so far I don't know how to fix it!

---


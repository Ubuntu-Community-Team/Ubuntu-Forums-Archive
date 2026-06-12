---
title: "top left hand corner of screen is dead"
date: 2013-03-17
forum: Desktop Environments
---

### Post by TheClawsThatCatch on 2013-03-17
Hello,

I have xubuntu 12.10 installed.

  The entire display works when I first log in. Then, inexplicably, I will no longer be able to click on anything in the top left hand corner of the screen. In fact, if I hover over icons, no graphical effects occur. Occasionally that part of the screen even turns black.

Here's an image I screenshotted to show. You can see that I have the cursor hovering over the chromium icon, but only half of it is highlighted. The half that is in the "dead zone" doesn't show.

[http://i.imgur.com/BHXnTxS.png](http://i.imgur.com/BHXnTxS.png)

What's going on?

---

### Post by meteorrock on 2013-03-18
A glitch in the matrix. :)  Just kidding , hehee. 

  Have you updated your headers and software for your desktop and your distro? Those headers are always being improved for your kernel base. Run this code in your terminal. Some will think this is a matter of course but new linux users might not know these tricks. Just copy paste that code into your terminal. Sudo will give you root file access so be careful on copy pasting any elaborate rogue code into your terminal on the internet. When you get more comfortable using the terminal you will recognize what is bogus code. This code I will give you is safe though.  The sudo upgrade and update command is also handled by the software up-grader on ubuntu builds also in your system. 

```
sudo apt-get update && sudo apt-get upgrade
```


Then remove any dependencies that might be causing that interface glitch on your desktop in the terminal.

 ```
sudo apt-get autoclean
```

 That code will give you a list of dependencies or apps, installation programs for some software that you might have installed that is no longer needed for your ubuntu build.  Make sure you research the dependencies or "apps" to make sure they are no longer needed for your ubuntu build. The apt-get is really smart but it is not foolproof. If, however, you are just learning linux auto removing programs or dependencies no longer needed by your system is fairly safe.   Some dependencies left behind could also cause slight glitches if dependencies are not met. 

Then remove them with this command.

```
sudo apt-get autoremove [application or X]
```

So try those tips and see if that helps you. If it does not, post in your thread here  and someone with more experience than I can help you further. Be careful as to not remove the Gstreamer packages as they are for mp3 encoder/decoding and DVD playback. Also check for applications you installed from earlier that you might need. Do not delete those either. 

More experienced coders can use this code here.

```
sudo sh -c "apt-get update;apt-get dist-upgrade;apt-get autoremove;apt-get autoclean"
```

Check this thread here on a better explanation if needed. [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by TheClawsThatCatch on 2013-03-18
I did what you said. Deleted stuff. didn't help.

But I figured something out. It's directly related to Steam.

When I have the Steam application running, that segment goes dead. When I quit steam, the glitch goes away.

What is going on?

---

### Post by meteorrock on 2013-03-19
Probably a slight GUI interface bug. You could try to purge steam and then reinstall it. You will lose all of your settings but it might help if that glitch is bothering you. It could of been slightly corrupted also when you installed it from the internet. That happens sometimes, but its not common.

Open up your terminal .

```
 sudo apt-get purge steam
```

Then reinstall Steam through the Ubuntu software center. That might help to remove that application and reinstall it.

---


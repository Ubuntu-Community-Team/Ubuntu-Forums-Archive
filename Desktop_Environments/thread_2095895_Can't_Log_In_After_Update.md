---
title: "Can't Log In After Update"
date: 2012-12-18
forum: Desktop Environments
---

### Post by amtur_poet on 2012-12-18
I recently installed some updates on Ubuntu 12.10 for my Toshiba Qosmio X775-38V78, but I encountered a strange issue. After rebooting, I could not log into Unity. As soon as I tried, I got a black screen for about a second, but then was dumped right back to the login screen. I tried to log in to Gnome and KDE, and I was actually able to get to the desktop for a few seconds before going back to the login screen again. What can I do to fix this?

---

### Post by grahammechanical on 2012-12-18
There is a Recovery Mode option in the Grub Menu. It is in the Advanced Options submenu. Click on that and then click on Resume. That might get you to a desktop without loading the proprietary video driver.

You can then go to System Settings>Software Sources>Additional Drivers tab and try to activate a different video driver. Just a suggestion.

Regards.

---

### Post by Yougo on 2012-12-18
A different suggestion:
When at the login screen, press ctrl+alt+F3.
the screen should change to black with a text prompt

Type in your username, press enter
Type your password, press enter. 

Note: you don't see your password as you type, not even dots. This is normal.

Type  ```
dir .Xau 
``` and press enter. If you see " .Xauthority " in the lines below your command, type the following:
```
sudo rm .Xauthority
``` and press enter
Type your password and press enter.
Then, type exit and press enter.
Then press ctrl+alt+F7 to return to the login screen. 

See if you can login now.

---

### Post by amtur_poet on 2012-12-20
> **Yougo said:**
> A different suggestion:
When at the login screen, press ctrl+alt+F3.
the screen should change to black with a text prompt

Type in your username, press enter
Type your password, press enter. 

Note: you don't see your password as you type, not even dots. This is normal.

Type  ```
dir .Xau 
``` and press enter. If you see " .Xauthority " in the lines below your command, type the following:
```
sudo rm .Xauthority
``` and press enter
Type your password and press enter.
Then, type exit and press enter.
Then press ctrl+alt+F7 to return to the login screen. 

See if you can login now.
When I try that first command, it says "No such file or directory."

---

### Post by dannyboy79 on 2012-12-20
hit the tab button after entering .Xau to have it auto-complete. also, check df -h to make sure your / partition isn't full

---

### Post by amtur_poet on 2012-12-21
Nope. Still dumps me back to the login screen. :(
I think I should mention that I installed those video card drivers that Nvidia released for Linux a while back. They worked fine until now.

---

### Post by dannyboy79 on 2012-12-21
which nvidia driver version and what card do you have? can you log into tty1 session and look at your /var/log/Xorg.0.log file for any X errors?

i thought since the nvidia drivers now have DKMS, you don't neeed to reinstall them after a kernel upgrade but maybe you do.

you could try to mv your xorg.conf temporarily so the system uses the default nouveau driver so that then you can at least get to gui.

---

### Post by amtur_poet on 2012-12-21
What exactly am I looking for in Xorg? Also, what should I do once I get to recovery mode? I really have no idea what to do.
EDIT: My graphics card is an Nvidia GeForce GT 560M. I am using the Nividia 304.64 version driver. Here is a picture of what output when I ran cat /var/log/Xorg.0.log:
[https://lh4.googleusercontent.com/-kTo64IEHkyo/UNUIgzML68I/AAAAAAAABxg/eWJ7rCnjGFc/s912/20121221_200949.jpg](https://lh4.googleusercontent.com/-kTo64IEHkyo/UNUIgzML68I/AAAAAAAABxg/eWJ7rCnjGFc/s912/20121221_200949.jpg)

> There is a Recovery Mode option in the Grub Menu. It is in the Advanced Options submenu. Click on that and then click on Resume. That might get you to a desktop without loading the proprietary video driver.

You can then go to System Settings>Software Sources>Additional Drivers tab and try to activate a different video driver. Just a suggestion.

Regards.Tried that, got the same error. :(

---

### Post by matt7195 on 2012-12-21
I had the same issue when I upgraded, but it might have had something to do with the fact that I was running Cinnamon as my desktop environment, so I'm sorry if my suggestion doesn't work for you.

First, out of random trial and error, I tried logging in as 'guest', and was able to get in.  So if you can't even get in as guest, you can probably stop reading.

Anyway, as guest I couldn't do much work on the system, so I just logged back out again.

Then I noticed that there was a blank white circle by my username on the login page.  But it was a circle with an Ubuntu logo in it by 'guest'.  So I clicked the blank circle, and a list of the desktop interface choices came up.  I chose Unity, logged in, an was good to go!

The reason I guessed it was an issue with Cinnamon was that Cinnamon wasn't even in the list of possible environments.  Since it was my default before I upgraded, I wasn't surprised it got confused after the upgrade.

Again, not sure if this helps, or if I just stumbled on an obvious setting change, but it's worth checking.

All the best!

---

### Post by amtur_poet on 2012-12-21
> **matt7195 said:**
> I had the same issue when I upgraded, but it might have had something to do with the fact that I was running Cinnamon as my desktop environment, so I'm sorry if my suggestion doesn't work for you.

First, out of random trial and error, I tried logging in as 'guest', and was able to get in.  So if you can't even get in as guest, you can probably stop reading.

Anyway, as guest I couldn't do much work on the system, so I just logged back out again.

Then I noticed that there was a blank white circle by my username on the login page.  But it was a circle with an Ubuntu logo in it by 'guest'.  So I clicked the blank circle, and a list of the desktop interface choices came up.  I chose Unity, logged in, an was good to go!

The reason I guessed it was an issue with Cinnamon was that Cinnamon wasn't even in the list of possible environments.  Since it was my default before I upgraded, I wasn't surprised it got confused after the upgrade.

Again, not sure if this helps, or if I just stumbled on an obvious setting change, but it's worth checking.

All the best!
Thanks for the suggestion, but I have Unity, Gnome, Gnome-Classic, KDE, and standalone XBMC installed as desktop environments, and none of them work for more than a few seconds. :(

---

### Post by amtur_poet on 2012-12-22
No ideas? Please don't tell me that I have to do a fresh install...

---

### Post by amtur_poet on 2012-12-22
Nothing? Nothing at all?

---

### Post by steeldriver on 2012-12-22
I've never had to do it - but since you can get into a virtual terminal you could try the compiz reset described here

[http://ubuntuforums.org/showthread.php?t=2087068](http://ubuntuforums.org/showthread.php?t=2087068)

---

### Post by dannyboy79 on 2012-12-22
can you get a look at temperatures from tty1 session? it may be a hardware issue. can you boot to a 12.10 live cd and it work ok?

---


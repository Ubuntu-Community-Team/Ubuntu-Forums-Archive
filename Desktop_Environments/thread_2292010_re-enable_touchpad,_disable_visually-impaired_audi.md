---
title: "re-enable touchpad, disable visually-impaired audio"
date: 2015-08-24
forum: Desktop Environments
---

### Post by George Heine on 2015-08-24
My travel computer is a Toshiba NB-505 notebook with Ubuntu 14.04 LTS (also has a Windows 7 partition).  A few weeks ago, for unknown reasons (perhaps from playing with the function keys to get it synced with a projector), the touchpad quit working.  At first I thought this might be a hardware failure, but after much experimentation, was able to get it re-enabled by booting to Windows and pressing Function/F9.

What is the key sequence in the Ubuntu interface to re-enable (or disable) the touchpad?

Also, the computer now seems to have audio enabled for visually-impaired users.  For example, at the login screen I get an audio message asking for my password, then for each key pressed, the audio pronounces the name of the key (or just "asterisk" if entering a password).  Not a major issue because audio is usually muted anyway, but how do I disable this functionality?

More generally, where is there a guide to keypad sequences for controlling the hardware?  Better yet, how many of  these functions can be controlled
with BASH commands typed at the terminal, and where is there a guide to these commands?  (e.g., I had to learn "sudo poweroff" to shut down the computer when the touchpad was disabled.)  I am familiar with the bash man pages, but is there a more concise guide somewhere to just hardware control commands? 

Thanks for any assistance.

---

### Post by ajgreeny on 2015-08-24
> **George Heine said:**
> What is the key sequence in the Ubuntu interface to re-enable (or disable) the touchpad?
There is no standard key sequence that I know of for that; it is going to be very dependent on the exact hardware you have and how the maker put it all together.  Do a web-search on your Toshiba model to find out more if you don't have a written manual.
> **George Heine said:**
> Also, the computer now seems to have audio enabled for visually-impaired users.  For example, at the login screen I get an audio message asking for my password, then for each key pressed, the audio pronounces the name of the key (or just "asterisk" if entering a password).  Not a major issue because audio is usually muted anyway, but how do I disable this functionality?I've never come across that before but I assume it must be Screen-reader in the "Universal Access" control dialogue.  I don't use Ubuntu with unity so will leave you to deal with that.

> **George Heine said:**
> More generally, where is there a guide to keypad sequences for controlling the hardware?  Better yet, how many of  these functions can be controlled with BASH commands typed at the terminal, and where is there a guide to these commands?  (e.g., I had to learn "sudo poweroff" to shut down the computer when the touchpad was disabled.)  I am familiar with the bash man pages, but is there a more concise guide somewhere to just hardware control commands? See my first answer above.

However, there are a some general commands that may help you out with some of these questions.  If the laptop has a synaptics touchpad you will normally be able to enable and disable the pad completely with  synclient, a command-line utility, using command ```
synclient TouchpadOff=1
``` to turn the pad off and ```
synclient TouchpadOff=0
```to turn it on again.  Look at **man synclient** or [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) for a lot more info on that.

For volume control in terminal  or using aliases or even as keyboard shortcuts you could try the three commands
```
amixer set Master playback 3dB-
```to lower volume,
```
amixer set Master playback 3dB+
```to raise volume and 
```
amixer -D pulse set Master toggle
```to toggle volume on and off.

---

### Post by George Heine on 2015-09-14
Thank you for the response, and please excuse the belated reply; had to deal with some pressing matters.  

"synclient" does appear to turn the touchpad on and off on my system; will try disabling it off before my next power-down; and, if it is still disabled on the next boot, try using synclient to enable.  The information about "amixer" is also interesting, and gives a lot of fine-grained control over an audio system which is actually quite primitive.

The audio that comes up at power-on appears to be the result of a program named "orca", installed by default on Ubuntu and some other Linux systems.  I entered "orca -t" to set options, and then was prompted to answer a series of questions at the keyboard.  On my next power-up, got an audio message "screen reading disabled", and then was able to enter a password without audio feedback for each keystroke.  A possibly related issue is that I have the CapsLock key (used in the Laptop version of orca) disabled in my user profile, but this does not become effective until after logging in.

---

### Post by George Heine on 2015-09-15
Tried using synclient to disable the touchpad, then rebooting.  But on reboot, the touchpad is enabled again.  Then booted into Windows, used Functionl-F9 to disable the touchpad.  Upon reboot, touchpad was disabled, and entering "synclient TouchpadOff=0" had no effect.  Had to reboot to Windows to re-enable the touchpad.

Searched the Toshiba manual without finding much. Unit has a Synaptics  touchpad, but there is no information about model number, etc.  (There  was a note in the troubleshooting section about using the Function-F9  key combination in Windows.)

The spoken audio prompts while logging in have disappeared; something, apparently something I did while configuring orca.

So, I guess the status of these problems is that both have been fixed for now, but I do not have clear information about why they occurred in the first place, nor a repeatable fix, other than booting to Windows for the touchpad. There are some further suggestions in [this thread]("http://buntuforums.org/showthread.php?t=2233632") , which I will try as time permits.

---


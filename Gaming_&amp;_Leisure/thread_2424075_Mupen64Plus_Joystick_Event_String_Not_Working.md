---
title: "Mupen64Plus Joystick Event String Not Working"
date: 2019-08-03
forum: Gaming &amp; Leisure
---

### Post by the-cat-coder22 on 2019-08-03
I&#8217;m not sure if this is the correct place to post this question, but I&#8217;m on Ubuntu 18.04 and I'm using Mupen64Plus (the command-line N64 emulator), and no matter what I try, I can&#8217;t seem to get the Joystick Event String functionality to work. I'm trying to make it so that button 10 on any active controller will load the save state. 

In the Mupen64Plus.ini file, I changed one of the Joystick lines (found under the CoreEvents section) from:
 
```
# Joystick event string for loading the emulator state

Joy Mapping Load State = ""
```
To:

```
# Joystick event string for loading the emulator state

Joy Mapping Load State = "J*B9"
```[FONT=courier new]
[/FONT]
**According to the Mupen64Plus documentation ([found here]("https://mupen64plus.org/wiki/index.php?title=Mupen64Plus_Core_Parameters")), this should allow me to use button 10 on any active joystick to load the emulator state, but it doesn&#8217;t**. I tried using other buttons, as well as using all the different video plugins and none of it made a difference. The controller I use works perfect as far as emulating the controller input though. This Joystick Event String mapping also **works as expected on Windows 10 for me.**
 
Any ideas on why it the emulator isn&#8217;t detecting those Joystick Event String mappings? Also, is there anywhere that would be better to post this question?

**Edit**: I was able to get the controller Joystick event string functionality to work by explicitly stating the joystick number, like so:

```
# Joystick event string for loading the emulator state

Joy Mapping Load State = "J0B9"
```

It appears that the asterisk functionality isn't implemented in the Linux version of Mupen64Plus (would have been nice to know...)

---


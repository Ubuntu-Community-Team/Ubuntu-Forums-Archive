---
title: "problem with zsnes and gamepad"
date: 2006-11-09
forum: Gaming &amp; Leisure
---

### Post by misfito on 2006-11-09
I can't configure gamepad in zsnes :confused: 
Hello friends, I want to know is there is a answer to the thread posted by lucidio: [http://ubuntuforums.org/showthread.php?t=230993](http://ubuntuforums.org/showthread.php?t=230993) that said:

Good afternoon to all!

i have a genius maxfire minipad gamepad but znes dont recognize the directions (the rest of the buttons seems to work fine).

i donwloaded and installed the packages joystick and jscalibrator and i calibrate my pad, which means that ubuntu recognize it.

When i enter in the configuration screen for znes to configure my pad, the program dont let me asign the direction of my pad.

any ideas?
__________________
Lucidio

Because I'm having the same problem.

I will really appreciate any help, thank you:p .

p.s. sorry if i posted this twice but in the general help no one helped me :(

---

### Post by misfito on 2006-11-27
Hello anyone???

---

### Post by monkey4ahead on 2006-12-09
I'm having exactly the same problem with a gravis gamepad pro (gameport not usb). Been searching on the web for an answer. If i can get this to work i can abandon windows forever! Can anybody help?

---

### Post by Jengu on 2006-12-10
I've actually filed a bug about this:

[https://launchpad.net/distros/ubuntu/+source/zsnes/+bug/70598](https://launchpad.net/distros/ubuntu/+source/zsnes/+bug/70598)

The quick fix is to make a symbolic link. Type this at the command line:

```

sudo ln -s /dev/input/js0 /dev/js0

```

Repeat for js1, js2, js3, etc. if you have more than 1 gamepad. I can't remember if that was the only problem I had or if there was a second one. Post back if this works.

---

### Post by adam0509 on 2006-12-22
No, that doesn't work.

I made "sudo ln..." + re-calibrate with jscalibrator + launch zsnes = doesn't workk unfortunatly

---

### Post by Frizzle on 2007-06-21
Hello,

I was just looking at this post which I found on google and recognized te exact problem I had with my Logitech Dual Action. After a little bit of searching I landed on this topic:
[http://board.zsnes.com/phpBB2/viewtopic.php?p=135928&sid=37c0b5a1f2ca0992dfe733c2d6257864](http://board.zsnes.com/phpBB2/viewtopic.php?p=135928&sid=37c0b5a1f2ca0992dfe733c2d6257864)

This worked for me:
I installed the .deb package provided in adam0509's post 
and set the  joystick_sensitivity = 0 option in  my "~/.zsnes/zsnesl.cfg" file.

So if anyone else lands on this topic, try it.

Greetz,
Frank

---

### Post by DoktorSeven on 2007-06-21
If nothing else works, also try **sudo rmmod analog**; I have to do that to get the pad workong for one of my gamepads.

---

### Post by KarmaticStylee on 2007-08-28
I still cannot get my Gravis Gamepad Pro to work in ZSNES.  It works in both my Genesis and NES emulators but not ZNSES.  It also functions perfect in the Joystick Calibrator app.  The only thing not working right in ZSNES is the directions.  I've messed with the config file to no avail.  Please help :confused:


UPDATE: After uninstalling JSCAlibrator -and- ZSNES and then reinstalling ZSNES it now works.  WOOT!

---

### Post by acoustibop on 2007-08-29
Yes, jscalibrator seems to have the effect of disabling directional controls in emulators, although it displays them itself as working.  Don't confuse it with joystick, a terminal-based calibrator that seems to work perfectly well.

---

### Post by adam0509 on 2007-09-29
as told in my topic :

[http://ubuntuforums.org/showthread.php?t=338457](http://ubuntuforums.org/showthread.php?t=338457)


> 
FOUND IT


jscalibrator gives real values to kernel, that's why it don't works.


ALL GAMES will works on Kubuntu, because of the joystick calibration thing give emulate value (it gives 32000 with my sidewinder gamepad, where jscalibrator will give "1"...)


:guitar:

---

### Post by lsd33 on 2008-12-31
[http://ubuntuforums.org/showthread.php?t=476030](http://ubuntuforums.org/showthread.php?t=476030)
install rejoystick if your d-pad is not recognized in zsnes but IS recognized elsewhere... you can map the joystick d-pad buttons to actual keys.

---


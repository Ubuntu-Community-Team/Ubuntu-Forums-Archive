---
title: "Mupen64 No Controller Problem"
date: 2007-07-30
forum: Gaming &amp; Leisure
---

### Post by MutualDisdain on 2007-07-30
Hi, I have just spent the weekend completing my first Linux install and am really happy with the results. Myth TV is great, and ZNES is awesome.

 I have been trying to get the mupen64 emulator to work properly but I continue to get a "no controller" error when I run any Rom.

I am using blight's input plug in to configure my Game Elements GGE909 controllers to work with the emulator. Blight allows me to configure each of my buttons correctly, but when the games start I get the dreaded, "No Controller" message.

I have attempted the solution listed here: [http://ubuntuforums.org/showthread.php?p=2439699](http://ubuntuforums.org/showthread.php?p=2439699), which is to link the name of the controller using the command: sudo ln -s /dev/input/js0 /dev/js0, but it still has not solved my problem.

Has anyone else had this problem, or know of some troubleshooting I can do on this end to fix it? I am relatively new to Linux so I might be missing something obvious here. Perhaps the device names I am linking above are not the real device names?

Thanks,
Jason

---

### Post by MutualDisdain on 2007-07-30
Hi, I have managed to solve part of my problem. I reread the thread I linked to above and realized that the plugged button had to be enabled in the input configuration. I had thought that dark grey meant that the button was enabled in the GUI.

I still have one remaining issue. When I configure my controller I am able to assign my DPAD values to the setup, but the DPAD does not work in game.  Any information on this problem?

---

### Post by RyCS42 on 2007-07-30
For the D-Pad not working in the game, I had the same issue too. Until I realized that the game I was trying it on didn't use the d-pad anyways... My first thought is try a game that you know for sure uses the d-pad in it.

As long as the controller is marked plugged in, and the d-pad values are correctly assigned, you should be good.

---

### Post by MutualDisdain on 2007-07-30
> **RyCS42 said:**
> For the D-Pad not working in the game, I had the same issue too. Until I realized that the game I was trying it on didn't use the d-pad anyways... My first thought is try a game that you know for sure uses the d-pad in it.

As long as the controller is marked plugged in, and the d-pad values are correctly assigned, you should be good.

Thanks, that seems to have been my problem. The mapping of controls to the game are different than I remember,  but I think I can easily get around this.

Now to download Beyond the Red Line

---

### Post by aphirst on 2008-05-30
I have a controller-based problem, which I would have put in a new thread, except this thread has the same name as the one I would have made.

If I insert a joystick into a USB port, open mupen64, configure Blight's Input plugin to use it (Jess Tech Dual Analog), I can play. However, Blight's Input Plugin's configuration system will NOT load at all if that controller is not plugged in. It simply causes the entire program to segfault. Consequently, I can only change to keyboard settings by changing plugin or by inserting a joypad first.

Does anyone know of a solution for this very strange problem, since I have not come across anything by plugging terms into Google...

---

### Post by acoustibop on 2008-05-30
> **MutualDisdain said:**
> ... Now to download Beyond the Red Line

MutualDisdain, downloading games is illegal in most countries, and you should not mention doing it in a reputable forum such as this.

@aphirst:  I would have thought your best bet would be to reset the Device in the plugin settings to None or Keyboard before removing your controller.

---


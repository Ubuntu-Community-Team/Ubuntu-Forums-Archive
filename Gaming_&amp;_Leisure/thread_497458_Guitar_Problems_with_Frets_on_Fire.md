---
title: "Guitar Problems with Frets on Fire"
date: 2007-07-10
forum: Gaming &amp; Leisure
---

### Post by GreatGariny on 2007-07-10
I'm running Ubuntu 7.04 AMD 64 and have Frets on Fire (FoF) working except for my guitar.  I have a generic Playstation 2 to USB adapter that is recognized as "Twin USB Joystick" and use a Guitar Hero Playstation guitar and it works perfectly under Windows.  

The Joystick Calibrator detects the guitar and all the buttons, including the pick (Axis 1).  Frets on Fire will map all the buttons except for the pick.  

I believe FoF wants the pick to be Axis 0 (which would probably be the joystick horizontal axis on a regular PS2 controller).   I say this because before I calibrated the guitar FoF thought the joystick's axis 0 was constantly being pushed so it mapped it to every control I tried to set.  After I calibrated it, that problem went away but the pick still didn't work.  I know Axis 0 is not the "Star Power Control" where you tilt the guitar because it is recognized as a button.  Axis 0 is also not the wammy bar because that has never functioned with the USB adapter.

I tried setting Axis 1 as a hat in the Joystick Calibrator, but FoF still wouldn't map the controls.  The simplest solution I can think of (if its possible) is to swap Axis 1 and Axis 0.  I don't need to worry about getting a regular Playstation controller to work with the adapter because I only use it to play Frets on Fire.

Thanks for the help.  
:guitar:

---

### Post by Naegling23 on 2007-07-10
hmmm... Honestly, I never remmapped the buttons.  I just plugged it in, and set all of the controls in FoF.  I would think that while messing around with joystick calibrator, something got changed.  I would try that a few more times, you mentioned that the gyro sensor was getting hit, maybe that messed things up a bit.

---

### Post by buttons on 2007-07-10
> **GreatGariny said:**
> I'm running Ubuntu 7.04 AMD 64 and have Frets on Fire (FoF) working except for my guitar.  I have a generic Playstation 2 to USB adapter that is recognized as "Twin USB Joystick" and use a Guitar Hero Playstation guitar and it works perfectly under Windows.  

The Joystick Calibrator detects the guitar and all the buttons, including the pick (Axis 1).  Frets on Fire will map all the buttons except for the pick.  

I believe FoF wants the pick to be Axis 0 (which would probably be the joystick horizontal axis on a regular PS2 controller).   I say this because before I calibrated the guitar FoF thought the joystick's axis 0 was constantly being pushed so it mapped it to every control I tried to set.  After I calibrated it, that problem went away but the pick still didn't work.  I know Axis 0 is not the "Star Power Control" where you tilt the guitar because it is recognized as a button.  Axis 0 is also not the wammy bar because that has never functioned with the USB adapter.

I tried setting Axis 1 as a hat in the Joystick Calibrator, but FoF still wouldn't map the controls.  The simplest solution I can think of (if its possible) is to swap Axis 1 and Axis 0.  I don't need to worry about getting a regular Playstation controller to work with the adapter because I only use it to play Frets on Fire.

Thanks for the help.  
:guitar:

Does jstest work?  Do you see a clearly defined event for everything? buttons, pick, white thingies?

I also never ran the calibrator.  I thought it was kinda pointless since on the PS2 guitar the first hat points left.  Always.  It's just a feature of the guitar, I guess.  Word to the wise: don't have the guitar plugged in when you start an FPS game, it can be dizzying.

---

### Post by GreatGariny on 2007-07-11
Jstest worked fine.  I saw every button defined including the pick and even got the guitar calibrated with jscal.  It was difficult becuase every button on the controller auto repeats the instant I press it.

Jscal wanted me to push a guitar button for the min, center, and max for 6 axis.  If I held it down for more than an instant the calibration utility would complete without me moving the pick to the max and min.  It was a rather amusing troubleshooting situation trying to push a key for a split second 6 times in a row. 

After it was calibrated I got Frets on Fire to recognize the up pick, but not the down.  I tried playing the game like that, but all the buttons were autorepeating in FoF (the keys would blink fast and FoF would play the miss sound 10 times a second if i tried to up pick a note.

If I can get the guitar controller working in Frets on Fire I will never need to boot into Windows again. :)

---

### Post by buttons on 2007-07-11
> **GreatGariny said:**
> Jstest worked fine.  I saw every button defined including the pick and even got the guitar calibrated with jscal.  It was difficult becuase every button on the controller auto repeats the instant I press it.

Jscal wanted me to push a guitar button for the min, center, and max for 6 axis.  If I held it down for more than an instant the calibration utility would complete without me moving the pick to the max and min.  It was a rather amusing troubleshooting situation trying to push a key for a split second 6 times in a row. 

After it was calibrated I got Frets on Fire to recognize the up pick, but not the down.  I tried playing the game like that, but all the buttons were autorepeating in FoF (the keys would blink fast and FoF would play the miss sound 10 times a second if i tried to up pick a note.

If I can get the guitar controller working in Frets on Fire I will never need to boot into Windows again. :)

Hmm.  Try [this thread]("http://ubuntuforums.org/showthread.php?t=393661") for ideas.

Or, you have the HID multi quirk bug, since you have a twin usb joystick.  This is a known issue that affects kernels 2.6.18-2.6.20 (as far as I know).  You can find the bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106622").  The thread includes a patch, though it's not guaranteed unless you actually have an EMS controller that it would fix it.  The patch itself only assigns HID_MULTI_INPUT_QUIRK to EMS adapters.

I remember another thread on here dealing with it (though I can't find it just now) that suggested upgrading to the gutsy kernel (2.6.21).  Basically you add the gutsy repositories, unselect everything in the resulting upgrade except the kernel, let it go, then put everything back to feisty again.  Several corrections were made in 2.6.21, not just the EMS one.

It's worth mentioning my twin adapter STILL didn't work in 2.6.21, though it would probably be trivial to add the line to the HID code and recompile (I have a radio shack adapter that I've been using instead).  Now that .22 is out I'll give that a shot and see if it's fixed when I get the chance.

---

### Post by GreatGariny on 2007-07-11
> Hmm. Try ,[this thread](http://ubuntuforums.org/showthread.php?t=393661) for ideas.
I tried running what Sparcman suggested from the above post
```

jscal -c /dev/input/js0
jscal -p /dev/input/js0 > joystick.cal
gedit joystick.cal

#now edit the parameters for the extra axes - the first number is the
#number of axes then each axis has a '1' with 5 more parameters after it.
#Change the 5 numbers after the one to zeros and save the changes


cat joystick.cal

#Ran the output of the edited joystick.cal

```
This did not work for me.
> 
Or, you have the HID multi quirk bug, since you have a twin usb joystick. This is a known issue that affects kernels 2.6.18-2.6.20 (as far as I know). You can find the bug report here. The thread includes a patch, though it's not guaranteed unless you actually have an EMS controller that it would fix it. The patch itself only assigns HID_MULTI_INPUT_QUIRK to EMS adapters.

I remember another thread on here dealing with it (though I can't find it just now) that suggested upgrading to the gutsy kernel (2.6.21). Basically you add the gutsy repositories, unselect everything in the resulting upgrade except the kernel, let it go, then put everything back to feisty again. Several corrections were made in 2.6.21, not just the EMS one.

It's worth mentioning my twin adapter STILL didn't work in 2.6.21, though it would probably be trivial to add the line to the HID code and recompile (I have a radio shack adapter that I've been using instead). Now that .22 is out I'll give that a shot and see if it's fixed when I get the chance.

It sound like I have the bug mentioned there.  Windows always detected each side of my adapter as a separate controller.  I found it odd the Linux detected both sides as js0.  When you get some time and get 2.6.22 running, let me know if your twin adapter is working.

Thanks for the help.

---

### Post by buttons on 2007-07-11
> **GreatGariny said:**
> I tried running what Sparcman suggested from the above post
```

jscal -c /dev/input/js0
jscal -p /dev/input/js0 > joystick.cal
gedit joystick.cal

#now edit the parameters for the extra axes - the first number is the
#number of axes then each axis has a '1' with 5 more parameters after it.
#Change the 5 numbers after the one to zeros and save the changes


cat joystick.cal

#Ran the output of the edited joystick.cal

```
This did not work for me.


It sound like I have the bug mentioned there.  Windows always detected each side of my adapter as a separate controller.  I found it odd the Linux detected both sides as js0.  When you get some time and get 2.6.22 running, let me know if your twin adapter is working.

Thanks for the help.

If you have time, I suggest trying the gutsy kernel upgrade.  You don't have to upgrade anything else, and can always force a downgrade using synaptic after.

---

### Post by 4KvRMU7Nnv on 2007-11-23
be sure you aren't trying to remap the keys over the keys of player two if your are using RF-mod.  If so, i have noticed that one or two of the keys will refuse to be recognized until player two controls are set to something else.  also, does the PS2 with adapter setup work fine for most people out of the box?  Ive been thinking of buying one of the guitars and an adapter online to try it out as the songs are just too hard for keyboard now.

---


---
title: "USB Gamepad's D-Pad won't work in GFCEU"
date: 2007-09-08
forum: Gaming &amp; Leisure
---

### Post by YAOMTC on 2007-09-08
[COLOR="Red"]**I've pretty much given up on this,** but will still check this thread on occasion.

NOTE: If you know how to "enable a kernel module", look down at the bottom of this post and tell me about that.[/COLOR]

I did a search, and found lots of topics about this very thing. However, I couldn't find any solutions that worked for me!

Today, I bought a GAMEMON USB gamepad. I can easily configure its 8 buttons (4 ABXY-esque buttons, two L and two R buttons, and a D-pad. **No analog anything.**) in GFCE Ultra, but the D-pad won't work at all. I tried various terminal commands, tried jscalibrator, tried uninstalling that and reinstalling GFCE Ultra... Nothing at all has worked.

Does anyone have a good solution for this? It seems that many people have gotten gamepads working in SNES9x, so... Does FCEU just not have support for this?

**EDIT: **It worked fine initially in jscalibrator, and in later in ZSNES after using the two "For a USB gamepad" [commands](http://ubuntuforums.org/showthread.php?t=338457). When I try to configure the gamepad in GFCE Ultra, the various button settings just flash by in a second, not allowing me to configure it. It isn't even noticed by FakeNES.

**EDIT(2):**
[img]http://img.photobucket.com/albums/v256/attack_mayo/092307_15161.jpg[/img]
I found something that might work, if someone could tell me how to do this.

See this (from [here]("http://forums.ipherswipsite.com/index.php?t=msg&S=1ea7cb3e7eed406ab8f9276eb550b806&th=58&goto=120#msg_120")): 

> To get it working with Linux, I had to enable the
kernel module for joystick and gamepad support.

[quote]Device Drivers --->
Input device support --->
<*> Joystick interface[/quote]

I have no idea what to do with that.

**EDIT(3):** qjoypad has my Axis1 as... flashing? I guess to the left?

---

### Post by YAOMTC on 2007-09-08
Oh, and here's some more info...

>The D-pad worked fine in jscalibrator.
>I'm using Feisty Fawn.
>The D-pad is 8-directional.

---

### Post by BigSilly on 2007-09-09
Is this a dual analogue pad, and you're trying to get the D-pad to work yeah? Usually on dual analogue pads there's an analogue switch or button that you can press to select and deselect analogue use. On mine there's also a little light that goes off when you deselect the analogue. I've found that on many games deselecting analogue in this way enables the D-pad use properly, such as on Secret Maryo Chronicles.

It's a simple solution, but it's so often one that's completely over-looked. Hope this helps.

---

### Post by acoustibop on 2007-09-09
You said in your first post that that you uninstalled jscalibrator, YAOMTC?  Did you put it back again (as your second post might suggest)?  If so, I do recommend that you get rid of it; it does seem to have the effect of disabling the directional controls of a number of controllers.

Does your controller work in other games?

---

### Post by YAOMTC on 2007-09-09
As I stated in the first post, the controller has 8 buttons, no analog sticks. Two L and two R buttons, four ABXY-esque buttons, "Turbo" and "Clear" buttons, and a D-pad. It's a simple gamepad for NES and SNES emulation.

I haven't tried it in any program but jscalibrator (which I did uninstall afterwards, yes) and GFCE Ultra.

---

### Post by YAOMTC on 2007-09-10
Here's to hoping we can get this to work!

---

### Post by YAOMTC on 2007-09-10
There's not anything wrong with keeping a topic on the first page, is there? You know, so people notice it. I've been on a forum before that apparently didn't like that, so if this is annoying at all, please let me know.

I hope someone has a solution that will work for me! :o

---

### Post by DoktorSeven on 2007-09-10
No idea if this is even related but I had to remove the module "analog" to get a gamepad's (not the same as you have) directional pad to work:

**sudo rmmod analog**

---

### Post by YAOMTC on 2007-09-11
ERROR: Module analog does not exist in /proc/modules

---

### Post by YAOMTC on 2007-09-11
Time to move it up, I guess.

---

### Post by YAOMTC on 2007-09-13
Should I stop trying? Could it be that this D-pad might be impossible to get working? I sure hope not.

---

### Post by DoktorSeven on 2007-09-13
You should try to find another application to test it in, to see if it's just fceu or all apps in general that can't get it right.  Even if it worked in jscalibrator, it might have problems in certain applications trying to read it.

Definately don't stop trying, since there's always some solution, but I know it can be frustrating when it doesn't work.

---

### Post by YAOMTC on 2007-09-13
There's no /dev/js1 or js2. Do I need those? Or is there another item in /dev I should use?

I tried it in both gsnes9x and snes9express, with Pac-Man (a public domain ROM). Nothing worked there.

---

### Post by DoktorSeven on 2007-09-13
No, it should be able to figure out (or you can specify in a configuration) that your joystick devices are at /dev/input/js*

---

### Post by YAOMTC on 2007-09-13
Ah, there we go. I changed it to /dev/input/js0 for the first controller, and the D-pad worked... But the buttons didn't. So I went to configure the button maps in snes9express... And it seemed to move through the buttons on its own, without giving me a chance to actually push the buttons... So that didn't work out. All that did was make it so I couldn't open the ROM at all, giving me an error whenever I did.

Oh, and in GFCE Ultra, when I click Gamepad 1, the configuration thing pops up for a moment, flies through all the buttons really fast, and disappears. That's just when I have the gamepad plugged into the USB port.

---

### Post by YAOMTC on 2007-09-13
Time to move it up.

---

### Post by YAOMTC on 2007-09-14
Again.

---

### Post by YAOMTC on 2007-09-16
And *again!* D:

---

### Post by acoustibop on 2007-09-17
I'm not familiar with your controller, YAOMTC, but there iis the possibility it's faulty.  However, it might be worth trying it in some other emulators/applications.  I've always used ZSNES rather than SNES9x and the input configuration there has always worked well for me.  There's an older version in the repositories, which should be fine for checking your contoller setup.

If it doesn't work well in any application, you have to consider that either it's using the wrong driver or it's broken.  Try this [Joystick/Gamepads under Ubuntu]("http://ubuntuforums.org/showthread.php?t=338457") thread for finding and installing a driver - worked for me installing a non-USB/gameport controller.

Otherwise, if you come to the conclusion it's broken, either take it back or, if you have soldering skills and don't mind invalidating the warranty, open it up and resolder any dodgy joints - I've done this successfully with a few cheapo controllers myself.

---

### Post by YAOMTC on 2007-09-17
Well, after using the two "For a USB gamepad" commands, the gamepad works perfectly in ZSNES (with configuration, of course). It still doesn't work in GFCE Ultra, though. It still flashes through all the button settings in a second, but only when the gamepad isn't plugged in.

---

### Post by YAOMTC on 2007-09-18
Time to move it up.

---

### Post by YAOMTC on 2007-09-19
Again.

---

### Post by YAOMTC on 2007-09-21
.

---

### Post by rossperk on 2007-09-21
Having it fly through the button mapping kind of sounds like the problem I'm having with my PS2 to USB adapted dancepad for StepMania. The buttons were able to map manually within the game because it requires a return to edit the mapping, but when you actually use the buttons, it's like "turbo" or rapid-fire is enabled on all inputs of the dancepad. 

Since snes9x doesn't require a return to go on to the next input, the rapid-fire is inputting the same button for all of the controls.

Stepmania had some sort of patch that remapped the analogue axis input to the d-pad input, or something like that, but I haven't been able to find it, and I've heard that it doesn't work for Feisty. I've also heard something about changing your kernel version, but isn't that a bit drastic to fix a joystick problem? :(

---

### Post by BigSilly on 2007-09-21
The older versions of Gens used to whizz through the input configs like this. Luckily, there are some very nice people on these forums who decided to maintain Gens and it works beautifully now. 

Alas, it sounds like this program you are having trouble with was created before the joys of dual analogue. I'll bet if you bought a cheapo digital USB pad with 6 buttons and no analogues it'd work fine. If it's a NES emu you're looking for I can recommend FakeNES. I downloaded a .deb of it from somewhere and it's a top NES emulator. If you like I'll pop it up here. I wouldn't waste any more effort on this program, that's for sure. It sounds to me as though it's not Ubuntu, and it's not your pad. It's a dated emu.

Please someone correct me if I'm wrong before the OP goes nuts!

---

### Post by YAOMTC on 2007-09-21
Guys! There's no analog! I never even implied there was any! D:

Perhaps I should have made this more clear. First post edited.

---

### Post by BigSilly on 2007-09-22
Oh right. I dunno where I got that from then...

I still reckon it'd be worth you trying FakeNES. It's a lovely emu, and works with both my pads just great. Not only that, but the interface is quite nice and customisable. There's a beta for the new version [here, ]("http://www.fbriere.net/debian/nes-emu/sid/")or you can try the .deb I have attached. I've had no bother with this. Let me know what you think.

---

### Post by acoustibop on 2007-09-22
Besides which, NES emulators (obviously) don't need analog controllers. ;)

---

### Post by YAOMTC on 2007-09-22
I'll try that out, BigSilly, thanks! Let's hope it works with it.

---

### Post by YAOMTC on 2007-09-22
Man, I don't know why this would work with ZSNES and (supposedly) not with any NES emulators. :(

---

### Post by BigSilly on 2007-09-22
Did it not work with FakeNES then? 

Honestly, I reckon for the few paltry space-credits it would cost for a decent pad, I would rather pay it than suffer like you have! I really can't understand why you're having such problems. I have two different PC pads that both work fine for the most part. I have issues with GridWars, which won't work with any pads, but otherwise all has been good. All my emu's work fine with these pads, and I have Mupen64, ZSNES, Gens, sdlmame, and FakeNES. 

Is it not possible to contact the GFCE Ultra people directly? They might be able to offer some solution for you, since we're getting nowhere here.

---

### Post by YAOMTC on 2007-09-22
Nope, didn't work with FakeNES either. It didn't even notice the controller, not any buttons. That's worse than the FCEU Ultra situation, where at least that recognized the buttons. >_>

Since it doesn't work with *either*, I think I'll pick the FakeNES people to contact, as it seems to be a nicer emulator.

And I don't have the money to go and buy a better gamepad, unfortunately. :(

(This was just ten bucks!)

---

### Post by YAOMTC on 2007-09-22
I found something that might work, if someone could tell me how to do this.

See this (from [here]("http://forums.ipherswipsite.com/index.php?t=msg&S=1ea7cb3e7eed406ab8f9276eb550b806&th=58&goto=120#msg_120")): 

> To get it working with Linux, I had to enable the
kernel module for joystick and gamepad support.

[quote]Device Drivers --->
Input device support --->
<*> Joystick interface[/quote]

I have no idea what to do with that.

---

### Post by YAOMTC on 2007-09-23
Nope, still don't.

---

### Post by acoustibop on 2007-09-23
I linked to this [Joystick/Gamepads under Ubuntu]("http://ubuntuforums.org/showthread.php?t=338457") thread earlier on, YAOMTC.  This explains installing modules/drivers for controllers.  BTW if you do install jscalibrator as the guide suggests, remove it before trying to use your controller with a game/emulator.  It seems to disable directional buttons/pads.

---

### Post by YAOMTC on 2007-09-23
Yeah, I already uninstalled jscalibrator. Unfortunately, it didn't make it work.

I think I can get this working if someone could show me how to do the thing a couple posts back.

---

### Post by acoustibop on 2007-09-23
Did you try the thread I linked to?

---

### Post by YAOMTC on 2007-09-23
> **YAOMTC said:**
> Well, after using the two "For a USB gamepad" commands, the gamepad works perfectly in ZSNES (with configuration, of course). It still doesn't work in GFCE Ultra, though. It still flashes through all the button settings in a second, but only when the gamepad isn't plugged in.
From my reply on page 2.

---

### Post by YAOMTC on 2007-09-24
Time to move it up.

---

### Post by YAOMTC on 2007-09-24
.

---

### Post by YAOMTC on 2007-09-25
.

---

### Post by YAOMTC on 2007-09-25
.

---

### Post by YAOMTC on 2007-09-26
.

---

### Post by YAOMTC on 2007-09-26
.

---

### Post by YAOMTC on 2007-09-27
.

---

### Post by YAOMTC on 2007-09-27
I hope there's someone around here who can tell me what to do with the "kernel module" thing. That's probably all I need.

---

### Post by tom61 on 2007-09-27
Install qjoypad by following these directions:
[http://ubuntuforums.org/showthread.php?t=147918](http://ubuntuforums.org/showthread.php?t=147918)

After that, you can run qjoypad to remap the directions (Axis 4 and 5 in this case) to keyboard presses. That's how I managed to get this gamepad working.

---

### Post by YAOMTC on 2007-09-28
```
chris@YAOMTC-1:~$ qjoypad
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```
I open up the GUI, and there's flashing going on. It bothers me, so I unplug the controller and plug it back in. The flashing stops. I assume that this is good.

But there is no Axis 4 or 5.

---

### Post by YAOMTC on 2007-09-28
.

---

### Post by YAOMTC on 2007-09-28
.

---

### Post by tom61 on 2007-09-28
> **YAOMTC said:**
> ```
chris@YAOMTC-1:~$ qjoypad
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```
I open up the GUI, and there's flashing going on. It bothers me, so I unplug the controller and plug it back in. The flashing stops. I assume that this is good.

But there is no Axis 4 or 5.


It should only flash when you press a button...

---

### Post by YAOMTC on 2007-09-29
Yeah, it was weird. I wasn't pushing anything.

And man, I was hoping for a helpful post... Disappointing. :(

---

### Post by YAOMTC on 2007-09-29
.

---

### Post by YAOMTC on 2007-09-30
.

---

### Post by YAOMTC on 2007-09-30
.

---

### Post by YAOMTC on 2007-09-30
.

---

### Post by lhommemagique on 2007-09-30
allright make sure your remove jscalibrator.. then go to your home folder and there may be a hidden file somthing like .joystick or similar left over from jscalibrator make sure you delet that as well.

then run:
```
cd /etc/init.d
sudo gedit joystick 
```

Paste the following lines into gedit, and save the file:
```
#! /bin/sh
# /etc/init.d/joystick
#

# Carry out specific functions when asked to by the system
case "$1" in
  start)
    echo "Enabling Joystick"
    cd /dev
    rm js*
    mknod input/js0 c 13 0
    ln -s input/js0 js0
    modprobe joydev
    modprobe analog
    echo "DONE!"
    ;;
  stop)
    rmmod joydev
    rmmod analog
    echo "DONE!"
    ;;
  *)
    echo "Usage: /etc/init.d/joystick {start|stop}"
    exit 1
    ;;
esac

exit 0
```

Now, make the file executable.
```
sudo chmod 755 joystick
```

Configure the system to run /etc/init.d/joystick on boot:
```
sudo update-rc.d joystick defaults
```

Enable the joystick:
```
sudo /etc/init.d/joystick start
```

Then try in GFCE 

tell me if it works.

---

### Post by YAOMTC on 2007-10-01
```
chris@YAOMTC-1:/etc/init.d$ sudo /etc/init.d/joystick start
Enabling Joystick
rm: cannot remove `js*': No such file or directory
DONE!
```

Things are still the same in GFCE Ultra and FakeNES, unfortunately. I'm thinking this is just a cruddy joypad that can't be made to work. Unless maybe if someone could tell me how to enable a "kernel module", as seen on the first post.

---

### Post by lhommemagique on 2007-10-01
sorry that didn't work for you
I was having the exact smae problem as you after I uinstalled that joyconfig program but then following  the steps I gave you fixed my problem.
I even got the same rm: cannot remove `js*': No such file or directory error but the next time I tried it in the emulator it worked. I don't know what to say. you could try reloading from starch and making sure not to use the joyconfig program.

---

### Post by YAOMTC on 2007-10-01
I assume by "reloading from starch" you mean "restarting from scratch"? Unless starch is some application I don't know about.

And by joyconfig, do you mean jscalibrator? Yeah, that's been uninstalled already, but I did remove that .joystick like you suggested.

---

### Post by lhommemagique on 2007-10-01
Sorry I was very tired when I made that post. and by  joyconfig, I did mean jscalibrator. And I do think reformatting and reinstalling ubuntu and making sure not to install or run jscalibrator at all would solve your problem. Sucks but it may be cheaper than buying a new gamepad.  Then again I may be wrong and then you'll have to get a new gamepad anyway and then you've wasted alot of time.   But like I said I was having the exact same problem where everything would work except the gamepad,  and running that fix I originally posted worked for me. Sorry I couldn't help anymore. good luck.

---

### Post by acoustibop on 2007-10-02
If you do reinstall Ubuntu, YAOMTC, make sure your controller is inserted when you install.

---

### Post by YAOMTC on 2007-10-02
So neither of you know anything about the enabling of a "kernel module", as mentioned on the first page? It seems like that's what should solve this problem, if anything.

And perhaps reinstalling Ubuntu would fix the problem, as well, but there's too many settings and modifications that I don't want to lose, and too many applications that I don't want to have to reinstall. And the whole process (backups, LiveCD creation, etc.) is just too much time and effort for a ~$10 gamepad.

---

### Post by YAOMTC on 2007-10-02
Hm... should I give up on this cheapie gamepad, or wait for someone who knows what a kernel module is?

---

### Post by BigSilly on 2007-10-03
I think for the three weeks of misery with this thing that you've clearly been through, I'd just bite the bullet and buy a pad that works with Ubuntu. You're lucky: my printer doesn't work with Linux, and I've not had it very long, so I'm going to have to fork out again for a compatible machine. At least a new pad's only a few quid. I don't mind too much though, because if it means I get to use Linux comfortably it's all to the good. 

I don't really know what the kernel module is that you refer to, but I'll bet you could fiddle away forever and still not get the result you want. Can I ask though, what make or manufacture is the pad you have? I want to be sure and avoid it in the future!

No matter what you do, some peripherals just won't work in Linux. Better to be sure and buy stuff that does work, than to have a miserable time like you have with this pad.

---

### Post by YAOMTC on 2007-10-03
I would mark this thread as "Apparently Unsolvable", but no, that's not possible. I wouldn't hesitate to do that if it were.

At least I only wasted $10.

---

### Post by spyd3r on 2008-03-02
i have the same gamepad with the same problem

---

### Post by amirman on 2009-04-14
i have the same gamepad and mine works fine, maybe i can help, i used jscalibrate today to figure out that the axes for horizontal and vertical on the gamepad are 3 and 4, not sure which is which though, if anyone needs help just ask me what to look at and i'll be glad to help as much as i can.

---

### Post by Statik on 2009-07-30
Well, there must be a solution to this. Here is my 'theoretical' one . . . if only someone could tell me how to make it real.

When you plug in a USB device, it announces who it is with a vendor ID and device ID. That set of IDs is linked to a database/datafile in Ubuntu that identifies which driver to associate with that device.

Is there a way to modify that file to use a different driver for that device? For instance, my PS2 USB adapter is identified as a Twin USB Joystick with 6 axis and 12 buttons. A different driver should be able to make it look like  a 10 button pad or something.

Then those 10-buttons could be setup within the game.

Is this possible?

Statik

---

### Post by RobbMeex on 2010-01-02
MY SNES PAD WAS DOING THE SAME THING, BUT NOW IT WORKS!!!

I don't know exactly what happened, I was doing quite a number of tricks, but I think it was:
Uninstall joystick and jscalibrate (jstest)
go to /home/*yourusername*/.joystick and deleted that
Restart my computer. Boom all good.

Note: I just tried to reinstall it and its not the install that kills it, its the calibration that messes it up. I have to reset now to see if it works again.

---

### Post by RobbMeex on 2010-01-02
deleting /usr/~~~/.joystick and then restarting worked for me. I could still have jscalibrator as long as I didn't run it.
Delete that file and tell me what happens.
Robbie

---

### Post by bmathis on 2010-10-30
I had the same problem with a gamepad. After playing with this thing for a good 20 mins or so, I accidently hit the Mode button which switched the gamepad from thumb stick to d-pad.

Just thought I'd throw this out in case anyone had the same issue.

---

### Post by theophiles on 2011-02-14
I have the same game pad and it didn't work then I tried lhommemagique's fix and it worked. Thank You

---

### Post by alchemagus on 2011-07-10
Hey guys,

Found a solution to the D-pad issues. Install "qjoypad" from the software repository. Qjoypad will simply assign keyboard keys to each button of your gamepad. 
This is different from a typical joypad configuration utility in that it emulates keyboard button presses via the pad rather than giving the joypad buttons their own designators. 
Simply assign each joypad/joystick button to a keyboard letter/symbol and you're good to go.

[http://qjoypad.sourceforge.net](http://qjoypad.sourceforge.net)

Thanks to Nathan Gaylinn and John Toman.

If you're having installation issues see: [http://ubuntuforums.org/showthread.php?t=147918](http://ubuntuforums.org/showthread.php?t=147918)

Cheers,

---


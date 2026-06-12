---
title: "xbox 360 wireless controller with Steam"
date: 2013-08-21
forum: Gaming &amp; Leisure
---

### Post by keith-k on 2013-08-21
Not sure if this should go under hardware issues but I'll start here. Just found the same solutions I've tried by Google-ing.

M$ Xbox 360 wireless controller is picked up automatically by xpad module in kernel; In L4D2 it almost works correctly with the exception of the joy sticks do nothing and no remapping works.

and so I installed xboxdrv did:

sudo rmmod xpad (I'll permanently remove the module if I get this working right.)sudo xboxdrv (I'll run it with --silent if I ever get it recognized by Steam)

and Ubuntu/xboxdrv picks up controller and all the correct output is shown in terminal; even the LED on controller is lit correctly for controller one. But in Steam L4D2 or any other games I have controller does nothing, and yes gamepad turned on under keyboard options. 

Any suggestions? Wired M$ xbox360 works out of box with Steam via xpad (except all LEDs blink) but would like to get wireless controller working since my game rig connected to big LED TV.

Thanks for any consideration. -Keith

(on Raring 64 bit) ... WT havent posted in a long time looks like I lost give me the beans.

---

### Post by Ranko Kohime on 2013-08-22
Just so we're clear on this...  You are using the "Xbox 360 Wireless Gaming Receiver for Windows", i.e. [THIS]("http://www.amazon.com/gp/product/B000HZFCT2/ref=oh_details_o01_s00_i00?ie=UTF8&psc=1"), correct?  Otherwise, the wireless controller will not work.

The xpad driver will pick up that too, and even assign 4 joystick slots to it.  (/dev/input/js0, js1, js2, and js3)  Sometimes this works with Steam, and sometimes not.  The issue comes to down to permissions.  By default, the input event devices (/dev/input/event*) are not readable or writable except by the root user.  This is to prevent key logging programs from capturing your password, and the like.  /dev/input/js* is read-only (i.e., a command cannot be sent to the controller to activate the vibration), and is considered by some to be deprecated, in favor of /dev/input/event*, which is what Steam uses.

[This thread]("http://steamcommunity.com/app/221410/discussions/0/864959809809029907/#c864969953355091680") contains one user's fix, although you may want to think long and hard about the security implications.  Also read post #14 in that same thread for a better explanation than I have provided here.

---

### Post by DarkAmbient on 2013-08-22
I had the same issue with Dungeon Defenders some weeks ago. Worked otherwise, just not in DD (and Trine). I don't think you need to uninstall xpad, you can use the flag **-d** or **--detach-kernel-driver** when launching xboxdrv to detach it temporarily.

Can't promise this will make the controllers work for you in L4D2, but could be worth a shot? I don't have my wireless reciever here, jogging my memory i recall this, but most likely wrong somewhere, try this:

```
xboxdrv --list-controller
```

to get the id/wid (hopefully VENDOR and PRODUCT id of your wireless reciever, can't remember?) of the controllers?

Now, I THINK it did something like this and then it worked for me, to be able to play DD and Trine 1 using my wireless controllers(s):

```
sudo xboxdrv --detach-kernel-driver --device-by-id VENDOR:PRODUCT --type xbox360-wireless  --wid 0 --led 2 --mimic-xpad-wireless
```

The value of --device-by-id needs to match you'r wireless reciever. If --list-controllers does not give you the values/usb-adress then you could try find it with **lsusb**.

The --wid should be the wireless controllers id/slot-place, 0 is the first controller, 3 is the last.

--led # controls the led, value 0-15 is possible.

So to get 4 controllers working, you could use the same command and just increase --wid by 1 and --led by 1 on each, I didn't test it a lot so this was my solution. I'm sure there are smoother ways though. I just opened as many terminals needed to to start xboxdrv for each controllers.

You'll notice when you get the controller to work as there will be a lot of input-information in the terminal when running xboxdrv. When you're pleased with your setup, use the **--silent** flag with xboxdrv to skip all that output... 

Used this to try my way forth:
[http://pingus.seul.org/~grumbel/xboxdrv/xboxdrv.html]("http://pingus.seul.org/~grumbel/xboxdrv/xboxdrv.html")

---

### Post by texaswriter on 2013-08-22
Interesting. I'll have to consider picking up the receiver.

---

### Post by xREDEMPTIONx on 2013-08-23
Just wanted to mention that for L4D2 there has been controller issues for a while now. Every report I've seen in their forums mentions the same thing, all buttons work but joysticks do nothing. Also, I have a logitech f710 wireless gamepad and use xboxdrv so games pick it up as xbox360 wireless controller and most steam games I have tried the controller does not work using xboxdrv. However, if I turn off xboxdrv and flip the little switch on top of the controller from (X)input to (D)input, some steam games such as Portal and Half Life 2 will pick up the controller and work perfectly. Weirdest thing of all is that while using the controller with xboxdrv, Steam seems to pick it up perfectly in Big Picture Mode. So I believe there are bugs or just some non-implemented code that is keeping everything from working right.

---


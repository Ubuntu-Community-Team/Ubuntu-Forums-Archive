---
title: "Random USB mouse death! Please help! :("
date: 2010-02-03
forum: Desktop Environments
---

### Post by pmj85 on 2010-02-03
Hi guys,

I'm a little disappointed tonight because I just ordered a shiny new 1TB HDD with the intention of going fully Ubuntu (I work with Windows so I know it pretty much like the back of my hand and am therefore bored of it / want a change). So, I installed Ubuntu and everything was going fantastically! Then, a very ugly problem reared its head:

My mouse completely died. It is lit up as normal but there's no input for it at all (USB). I plugged another USB mouse in to a different port and lo, it worked just fine... until it died only moments later with the exact same symptoms. 

For some weird reason, it would appear that browsing menus in Ubuntu (software centre, for arguments sake) causes my mouse to fail completely. Unplugging / replugging the mouse does absolutely nothing - it requires a computer reboot to get working again... and that only lasts a few minutes until it dies completely. 

Please tell me there is someone out there that knows how to fix this! I've looked around on Google but the only things I can find relate to HAL issues (which seem to differ) and LMB not working. This seems to be different - I can't find anybody else that has experienced complete mouse death. Please help :( I'm a complete newbie to Ubuntu and I'm very keen to overcome this problem and continue learning!

Many thanks,

- Paul

---

### Post by Orlando84 on 2010-02-03
Ok, I'll try to help you with your issue.
Unplug your USB mouse, then boot. When system has completely loaded, you are in your Gnome environment plug your mouse and then from Konsole or another terminal run```
dmesg | tail
``` Write the output here. After mouse crashes press "CTRL + ALT + F1" login on the black screen and then again run ```
dmesg | tail
``` and write the output here.

---

### Post by pmj85 on 2010-02-03
Thanks, I will do! I'm posting this from my laptop at the moment as I'm re-installing Ubuntu (I mucked the partitions up in my eagerness :redface:) so as soon as I'm back up and running I'll do that.

Thankyou very much :)

---

### Post by Orlando84 on 2010-02-03
Ok, I'll wait. I remember that times when I had configured YAWERTY layout for russian support in KDE and my russian layout lied a bit (symbols were not on their places). Had to reconfigure layout with hands.

---

### Post by pmj85 on 2010-02-03
Ok, here we go (sorry for the delay, I've been really busy tonight!)

```
paul@paul-desktop:~$ dmesg | tail
[   18.791341]  domain 0: span 0-1 level MC
[   18.791344]   groups: 0 1
[   18.791349] CPU1 attaching sched-domain:
[   18.791351]  domain 0: span 0-1 level MC
[   18.791353]   groups: 1 0
[   23.420068] eth0: no IPv6 routers present
[   46.480022] usb 2-8: new low speed USB device using ohci_hcd and address 3
[   46.709121] usb 2-8: configuration #1 chosen from 1 choice
[   46.720371] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-8/2-8:1.0/input/input5
[   46.720444] generic-usb 0003:046D:C01E.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-8/input0
paul@paul-desktop:~$ 


```

I'll update it again when it crashes :) The above was the output from booting without mouse plugged in, then plugging in after OS had fully loaded.

---

### Post by pmj85 on 2010-02-03
Ah! Very strange; when my mouse crashed, so did my keyboard! Usually my keyboard remains active and usable, this time however it completely died along with my mouse.

That also means I couldn't get the other console thingy pasted in here :( Man, I'm really struggling here! I was under the impression Ubuntu was good to go straight out of the box; I didn't think I'd be having problems with peripherals! 

Still, not to worry - it's all a learning curve :)

---

### Post by pmj85 on 2010-02-04
Still no luck, I can't find anything even remotely relating to the subject :( 

Perhaps it's best to downgrade to the earlier version - I had no problems with that!

---

### Post by pmj85 on 2010-02-04
Would it help at all if I mentioned I was using 64bit?

---

### Post by Orlando84 on 2010-02-06
I unforunantly can't help you because don't see the reason your USB mouse is crashing. Seems to be bad implementation of USB in your newer version, because two devices are diyng at once. Try to downgrade. Good luck!

---

### Post by pmj85 on 2010-02-06
I've defected to Linux Mint now :p

Unfortunately, my mouse still dies occasionally but far less frequently - after about 3 hours usage it has only died twice. It's an incredibly irritating problem but I'm constantly on the look out for a solution. Besides, I went in to Mint fully expecting the problem to rear its head because after all, the latest build *is* based on Ubuntu 9.10 :)

I appreciate your efforts, thank you :KS

---

### Post by herelder on 2010-02-06
> **pmj85 said:**
> Hi guys,

I'm a little disappointed tonight because I just ordered a shiny new 1TB HDD with the intention of going fully Ubuntu (I work with Windows so I know it pretty much like the back of my hand and am therefore bored of it / want a change). So, I installed Ubuntu and everything was going fantastically! Then, a very ugly problem reared its head:

My mouse completely died. It is lit up as normal but there's no input for it at all (USB). I plugged another USB mouse in to a different port and lo, it worked just fine... until it died only moments later with the exact same symptoms. 

For some weird reason, it would appear that browsing menus in Ubuntu (software centre, for arguments sake) causes my mouse to fail completely. Unplugging / replugging the mouse does absolutely nothing - it requires a computer reboot to get working again... and that only lasts a few minutes until it dies completely. 

Please tell me there is someone out there that knows how to fix this! I've looked around on Google but the only things I can find relate to HAL issues (which seem to differ) and LMB not working. This seems to be different - I can't find anybody else that has experienced complete mouse death. Please help :( I'm a complete newbie to Ubuntu and I'm very keen to overcome this problem and continue learning!


My mouse problem may be related to this one. I'm running Ubuntu on a Dell E5500 laptop, with a Dell mouse. 
After working for a while, the mouse starts misbehaving. It will move the arrow normally, but only part of the screen will respond normally on mouse-over and mouse clicks. 
As I'm typing this text, the mouose behaves normally within the browser tab I'm in, but outside the tab space window (even the tab title doesn't respond) nothing happens. Randomly clicking right/left at various locations on the screen sometimes switches the behaviour, then the inside of the window is untouchable and only the world outside of it responds. Sometimes nothing will respond to the mouse anymore, sometimes a mouseclick will only repeat the previous mouseclick.

This behaviour started a few weeks ago, and seens to get worse by the day.

Maybe the switching behaviour is an indication of the problem area?


-- 
Herelder

---

### Post by herelder on 2010-02-06
I just discovered I am able to control the part in which the mouse responds within a Firefox browser window. To switch, I need to rightclick the bar with the tab-titles, and then the area the mouse has to respond in. The rightclick seems to unlock both area's, as mouse-over then works all over the window (but not outside the window), but as soon as I click in an area, the others get locked.

Weird.


I should point out this is not per se a mouse or USB issue. The behaviour described actually started when using the pad on the laptop, no mouse connected at all. 

I also should mention the keyboard (on the laptop itself) generally keeps working, but sometimes also crashes, that is, it's only active in some parts of the screen.


-- 
Herelder

---

### Post by sskroeder on 2010-02-13
> **herelder said:**
> I just discovered I am able to control the part in which the mouse responds within a Firefox browser window. To switch, I need to rightclick the bar with the tab-titles, and then the area the mouse has to respond in. The rightclick seems to unlock both area's, as mouse-over then works all over the window (but not outside the window), but as soon as I click in an area, the others get locked.
Thanks so much for that workaround... I was on the verge of reinstalling Ubuntu 9.10 again... 

I'm have no idea why it suddenly started acting strange (which was annoying especially since I was in the middle of showing "how rock-stable Linux seem to be" to a friend of mine)... Just out of the blue, mouse events went unresponsive... ;-(

I hope that the smart guys figure out soon what is wrong, so I can get back to the stable and quicks-free Ubuntu, that I'm used to use... :P

---

### Post by jim77 on 2010-02-14
I also am experiencing random mouse/keyboard "sleepiness". Essentially, when it happens, I can move my mouse but clicking doesn't work, mouse-over doesn't work and the keyboard doesn't work. When this happens, I have to reboot.

I first noticed the problem when I upgraded to 2.6.31-16. I am currently running older version, 2.6.28-17 and it seems to not have the problem. All subsequent 2.6.31 versions have the same problem. (16, 17 and 19). I think the HAL conversion took place around this time (between 2.6.28 and 2.6.31). I'm hoping on the next upgrade, the issue will be resolved.

---

### Post by herelder on 2010-03-07
> **sskroeder said:**
> Thanks so much for that workaround... I was on the verge of reinstalling Ubuntu 9.10 again... 

I'm have no idea why it suddenly started acting strange (which was annoying especially since I was in the middle of showing "how rock-stable Linux seem to be" to a friend of mine)... Just out of the blue, mouse events went unresponsive... ;-(

I hope that the smart guys figure out soon what is wrong, so I can get back to the stable and quicks-free Ubuntu, that I'm used to use... :P

I discovered some things during the past weeks.

First, let me fill you in on some details about my configuration.

I'm using a laptop Dell Latitude E5500. The internal hard-disk has Windows Vista installed, which I cannot touch. I'm booting Ubuntu 9.10 from a Plextor 160GB USB harddisk.

Now, I have been booting Ubuntu on another laptop, NEC Versa P150, and I have no trouble whatsoever.

I also discovered that if I only use the mouse and leave the touch pad alone, the problem does not seem to occur. Whenever I touch, knowingly, the touchpad I get into trouble.

What's the conclusion? Well, it seems to be related to the computer hardware, and not at all to the mouse, maybe the touch pad.

If I use the Windows startup, sometimes the pointer/cursor get stuck also. In Windows I can reset the stuff by starting the task manager and cancelling it, and all is normal again.

It's weird.

What would be helpful, is knowing how to reset the scope of pointer and cursor behaviour, this would make it more easy to recover from the situation.

update 18-3-2010: This morning I got into trouble with the Windows part of the laptop. The cursor was stuck in the scroll mode, and this mode was unescapable, even after rebooting...
So, I called user support and had my laptop replaced. Same brand, same type. Problems gone, on Windows Vista, on Ubuntu.
I guess in my case it is a combination of hardware problem and the O.S.'s sensitivity.

---


---
title: "Left mouse button stops working in 10.10"
date: 2010-09-15
forum: Desktop Environments
---

### Post by tthomas48 on 2010-09-15
I'm having a problem with gnome. When I press a multimedia key on my keyboard (or obstensibly other hotkeys although I haven't figured out exactly what). My left-mouse button stops responding. The right mouse button works fine and the mouse tracks fine. I can go into the mouse control panel and switch it to a left handed mouse and the left mouse button works, but not the right.

I ran 'xinput test "HP Mouse"', and I can see the left mouse clicks coming through. So X11 at least thinks it's coming through. I've got nothing interesting that I can find in /var/log.

This is really generic USB hardware. HP Mouse and Microsoft Digital Media Keyboard.

I'm really stumped as to where to continue with my troubleshooting. Any thoughts?

---

### Post by corristo on 2010-09-29
updated to 10.10 today. Same problem, but left button stops working after keyboard layout switching (through hotkeys or indicator) =\

---

### Post by tthomas48 on 2010-09-29
I have fixed it temporarily by alt tabbing to a terminal and running:

sudo rmmod usbhid; sudo mobprobe usbhid

I'd like to be able to use my hotkeys again though.

---

### Post by ungzd on 2010-10-01
Have the same problem.
Stops working when switching keyboard layouts.
"sudo rmmod usbhid; sudo mobprobe usbhid" does not help. Restarting xorg helps. xinput test also shows events when button is clicked.

---

### Post by ungzd on 2010-10-01
Is mouse from A4Tech?

Here is issue in bug tracker: [https://bugs.launchpad.net/udev/+bug/637208](https://bugs.launchpad.net/udev/+bug/637208) that also contains temporary workaround:

[INDENT]Some solution, that solve our problem.
1) xinput --list
It will show you your input devices, our A4Tech mouse have id, for example, there are
&#9116;   &#8627; A4TECH USB Device                       	id=11	[slave  pointer  (2)]
&#9116;   &#8627; A4TECH USB Device                       	id=10	[slave  pointer  (2)]
2) xinput set-int-prop %id% "Device Enabled" 8 0
, where %id% is one of id's of your mouse. In my case it was 10.  Generally, this is the second id of list. This command will disable  advanced built-in keyboard of A4Tech mouse.
If you want to enable back, use
xinput set-int-prop %id% "Device Enabled" 8 1.
[/INDENT]Workaround works for me. My mouse is A4Tech K3-230.

---

### Post by tthomas48 on 2010-10-01
My mouse is a pretty generic HP USB Mouse. Disabling and re-enabling via xinput does not work for me. Xinput does show the left mouse button being clicked. Only thing that works so far is restarting X or rmmod-ing usbhid (which I'm guessing is not so much a solution as taking a sledgehammer to the problem).

---

### Post by Dolfhin01 on 2010-10-02
Same problem here, I think Ubuntu thinks that I keep my left mouse button pressed down all the time.

I can't use Ubuntu now :(

---

### Post by sendblink23 on 2010-10-03
I haven't experienced any mouse issues on mines, using latest updates from the RC - I'm on a fresh install

---

### Post by randomf on 2010-10-03
Same problem on Chicony wireless mouse & keyboard. It acts like the mouse button is pressed down all the time. Very annoying

---

### Post by randomf on 2010-10-05
sudo rmmod usbhid; sudo mobprobe usbhid

helps, but sometimes the mouse button stucks even 3 - 4 times a minute.

---

### Post by pawloch on 2010-10-06
same problem - Microsoft Wireless Mouse 500 and keyboard

---

### Post by ysakaed on 2010-10-10
This also happening to my 10.10, It was working without a problem in 10.04 and after upgrade to 10.10 sometimes it stopped working after listening to music or youtube.

I thought it has something to do with upgrade so I have performed a clean reinstall. Same problem.

I am using Microsoft Wireless Desktop 3000

---

### Post by ysakaed on 2010-10-10
I found its caused by the quick media buttons on the keyboard. Once its pressed, but left button on the mouse will stopped working.

---

### Post by pushkin22 on 2010-10-10
Same problem here. I installed 10.10 and some minutes later the left click stoped working, same happend while the installation. This makes 10.10 unusable...

Edit: Ok, now all buttons are dead, but I can still move the mouse. :) The keyboard also doesnt work properly.

Edit 2: Ok, here is the solution: Deactivating Num-Lock helps. I hate this... :D

---

### Post by Tanshaydar on 2010-10-10
I've installed stable release and still my mouse left button stucks.

---

### Post by Iscander on 2010-10-10
Have same problem after install stable release.
Stop left click after keyboard layout switch.

---

### Post by MinionTech on 2010-10-10
I'm having this problem as well and am using a Microsoft Arc Keyboard with a Logitech Trackball Optical.

---

### Post by MinionTech on 2010-10-10
Thanks for tracking that down!  The workaround may have killed my multimedia keys, but having a working left-click is more than worth it.  Hopefully we'll get a real fix sometime soon.

> **ungzd said:**
> Is mouse from A4Tech?

Here is issue in bug tracker: [https://bugs.launchpad.net/udev/+bug/637208](https://bugs.launchpad.net/udev/+bug/637208) that also contains temporary workaround:

[INDENT]Some solution, that solve our problem.
1) xinput --list
It will show you your input devices, our A4Tech mouse have id, for example, there are
&#9116;   &#8627; A4TECH USB Device                       	id=11	[slave  pointer  (2)]
&#9116;   &#8627; A4TECH USB Device                       	id=10	[slave  pointer  (2)]
2) xinput set-int-prop %id% "Device Enabled" 8 0
, where %id% is one of id's of your mouse. In my case it was 10.  Generally, this is the second id of list. This command will disable  advanced built-in keyboard of A4Tech mouse.
If you want to enable back, use
xinput set-int-prop %id% "Device Enabled" 8 1.
[/INDENT]Workaround works for me. My mouse is A4Tech K3-230.

---

### Post by Iscander on 2010-10-11
I noticed that the bug does not apear for a new created user.

---

### Post by pbvijay on 2010-10-11
I changed my keyborad layout from USA to usa alternative international and keyboard model to Microsoft office keyboard.
its working up to now.

---

### Post by pushkin22 on 2010-10-11
So...

Here is a little script, which you can let start with Ubuntu, but with deactivated numlock the mouse works better.

```
#!/bin/sh

xinput set-int-prop ID "Device Enabled" 8 0
```

ID should be a number...

> **ungzd said:**
> Is mouse from A4Tech?

Here is issue in bug tracker: [https://bugs.launchpad.net/udev/+bug/637208](https://bugs.launchpad.net/udev/+bug/637208) that also contains temporary workaround:

[INDENT]Some solution, that solve our problem.
1) xinput --list
It will show you your input devices, our A4Tech mouse have id, for example, there are
&#9116;   &#8627; A4TECH USB Device                       	id=11	[slave  pointer  (2)]
&#9116;   &#8627; A4TECH USB Device                       	id=10	[slave  pointer  (2)]
2) xinput set-int-prop %id% "Device Enabled" 8 0
, where %id% is one of id's of your mouse. In my case it was 10.  Generally, this is the second id of list. This command will disable  advanced built-in keyboard of A4Tech mouse.
If you want to enable back, use
xinput set-int-prop %id% "Device Enabled" 8 1.
[/INDENT]Workaround works for me. My mouse is A4Tech K3-230.

---

### Post by ricky11 on 2010-10-11
Have the same problem.Stops working when switching keyboard layouts."sudo rmmod usbhid; sudo mobprobe usbhid" does not help. Restarting xorg helps. xinput test also shows events when button is clicked








[Wordpress Newsletter Plugin]("http://**************/plugins/view/1/wordpress-newsletter-plugin")

---

### Post by glazs on 2010-10-11
[COLOR="Green"][SIZE="3"][FONT="Trebuchet MS"]**Tried [this]("https://bugs.launchpad.net/udev/+bug/637208/comments/40"). Maybe works, if not help i post here. Looks like solution :).**[/FONT][/SIZE][/COLOR]

Sry for text style, its important.

---

### Post by glazs on 2010-10-11
Still working. I think it's solution.

FCK YEA!

---

### Post by nmr on 2010-10-11
glazs,

thank you, that package worked for.

I ianstalled it and restarted, now it's fine.

I have a 4Tech Ka-3D

Thanks, again.

---

### Post by Iscander on 2010-10-11
> **glazs said:**
> [COLOR="Green"][SIZE="3"][FONT="Trebuchet MS"]**Tried [this]("https://bugs.launchpad.net/udev/+bug/637208/comments/40"). Maybe works, if not help i post here. Looks like solution :).**[/FONT][/SIZE][/COLOR]

Sry for text style, its important.

Thanks its work for me too.

---

### Post by brunjes on 2010-10-11
Re: Left mouse button stops working in 10.10
Quote:
Originally Posted by glazs View Post
Tried this. Maybe works, if not help i post here. Looks like solution .

Sry for text style, its important.
Thanks its work for me too.




Is there a 64-bit version of this somewhere? I don't think the i386 version will work for a 64-bit Ubuntu 10.10 system.

Thanks,

Roy

---

### Post by TmanP on 2010-10-12
I changed my keyboard ( microsoft digital media pro usb) to a generic usb keyboard (yes keyboard) and now my mouse works perfectly 

I also tried another mouse and the left button stopped working as well.

---

### Post by pawloch on 2010-10-12
[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.5.0+git20100822.990540fa-0ubuntu0sarvatt_amd64.deb](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.5.0+git20100822.990540fa-0ubuntu0sarvatt_amd64.deb) - works for 64 bit version

[http://launchpadlibrarian.net/54205518/xserver-xorg-input-evdev_2.5.0%2Bgit20100822.990540fa-0ubuntu0sarvatt_i386.deb](http://launchpadlibrarian.net/54205518/xserver-xorg-input-evdev_2.5.0%2Bgit20100822.990540fa-0ubuntu0sarvatt_i386.deb) - worsk for 32 bit version

(by [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311) and [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/637208?comments=all](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/637208?comments=all))

---

### Post by Abanabanana on 2010-10-13
I just cannot understand how this typ of problems appear by upgrading if it was working perfectly in earlier version.

Well, I'll try the solutions proposed above.

---

### Post by brunjes on 2010-10-13
Thanks for the tips here, but none of this works for me. I'm going back to 10.04.

---

### Post by JoaoCunha on 2010-10-13
> **pawloch said:**
> [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.5.0+git20100822.990540fa-0ubuntu0sarvatt_amd64.deb](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.5.0+git20100822.990540fa-0ubuntu0sarvatt_amd64.deb) - works for 64 bit version

[http://launchpadlibrarian.net/54205518/xserver-xorg-input-evdev_2.5.0%2Bgit20100822.990540fa-0ubuntu0sarvatt_i386.deb](http://launchpadlibrarian.net/54205518/xserver-xorg-input-evdev_2.5.0%2Bgit20100822.990540fa-0ubuntu0sarvatt_i386.deb) - worsk for 32 bit version

(by [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311) and [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/637208?comments=all](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/637208?comments=all))

Thank You Very Much!

I'm using Ubuntu 10.10 64bits and finally my problem is solved.

---

### Post by kord123 on 2010-10-13
brunjes, did you reboot after installing that .deb? For me worked fine after rebooting.

---

### Post by brunjes on 2010-10-13
When I tried to install it, there were complaints that the kernel version that the .deb package did not match what I was currently running. I just reinstalled 10.04 and will sit tight for a few months while these kinks get worked out. Maybe by Dec 2010 this upgrade process will be smoother...

---

### Post by brunjes on 2010-10-13
And one further note:

I did a fresh install of 10.10 64-bit on my Sony Vaio desktop with wireless keyboard and wireless mouse. All of this hardware worked normally on Ubuntu 10.04. A fresh install of 10.10 saw the same issue. I applied the 64-bit version of the ppa file mentioned above, rebooted, and the exact same problem remained. 10.10 is broken somewhere. I'm now running 10.04 for good (till 2011 anyway). By then, someone will realize where the problem really lies and will have fixed it ...

---

### Post by konkor on 2010-10-15
>Thanks for the tips here, but none of this works for me.

    Mouse left/right buttons stop working after opening some new programm (terminal,firefox...).
    Reconecting mouse to usb port helps for next opening some programm window (or sudo modprobe -r usbhid; sudo modprobe usbhid).
    When this happends, system can't lock user screen. Other mices working fine, im tryed Logitech, Razer Imperator...

PS: Mouse A4Tech (Model:X6-90D)

---

### Post by oopsie on 2010-10-15
> **pawloch said:**
> [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.5.0+git20100822.990540fa-0ubuntu0sarvatt_amd64.deb](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.5.0+git20100822.990540fa-0ubuntu0sarvatt_amd64.deb) - works for 64 bit version

[http://launchpadlibrarian.net/54205518/xserver-xorg-input-evdev_2.5.0%2Bgit20100822.990540fa-0ubuntu0sarvatt_i386.deb](http://launchpadlibrarian.net/54205518/xserver-xorg-input-evdev_2.5.0%2Bgit20100822.990540fa-0ubuntu0sarvatt_i386.deb) - worsk for 32 bit version

(by [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311) and [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/637208?comments=all](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/637208?comments=all))

This worked for me, thank you!!!

I tell you though, 10.10 isn't winning any prizes for reliability. Less than a week and I've had an install problem, ffmpeg has a bug and now my left mouse button failed =\

---

### Post by Lucky75 on 2010-10-17
> **glazs said:**
> [COLOR="Green"][SIZE="3"][FONT="Trebuchet MS"]**Tried [this]("https://bugs.launchpad.net/udev/+bug/637208/comments/40"). Maybe works, if not help i post here. Looks like solution :).**[/FONT][/SIZE][/COLOR]

Sry for text style, its important.

SWEET! Thanks mate! For those of you who can't get it to work, remember you need to logout first.

No idea why there was an issue with this. Gotta love stability...

Keyboard: Microsoft Digital Media Pro
Mouse: Logitech S510 Cordless desktop (mouse)

---

### Post by Sunflower1970 on 2010-10-17
I'm glad I found this. I was having this same problem in 10.04 which I had upgraded to about two months ago, but I thought it was just me needing a new mouse and keyboard. A battery exploded in my mouse so I thought it was shorting out. I had just upgraded to 10.10 thinking maybe it would fix the problem, but it didn't

I was getting ready to go out and get a new keyboard and mouse today....but I think the posted fix has worked for me, too. *crosses fingers.*

---

### Post by Gnorrogh on 2010-10-18
> **ungzd said:**
> Is mouse from A4Tech?

Here is issue in bug tracker: [https://bugs.launchpad.net/udev/+bug/637208](https://bugs.launchpad.net/udev/+bug/637208) that also contains temporary workaround:

[INDENT]Some solution, that solve our problem.
1) xinput --list
It will show you your input devices, our A4Tech mouse have id, for example, there are
&#9116;   &#8627; A4TECH USB Device                       	id=11	[slave  pointer  (2)]
&#9116;   &#8627; A4TECH USB Device                       	id=10	[slave  pointer  (2)]
2) xinput set-int-prop %id% "Device Enabled" 8 0
, where %id% is one of id's of your mouse. In my case it was 10.  Generally, this is the second id of list. This command will disable  advanced built-in keyboard of A4Tech mouse.
If you want to enable back, use
xinput set-int-prop %id% "Device Enabled" 8 1.
[/INDENT]Workaround works for me. My mouse is A4Tech K3-230.

This one worked for me. Thanks. Seems to be a driver-problem with the A4Tech devices?

---

### Post by krcolwell on 2010-10-19
> **JoaoCunha said:**
> Thank You Very Much!

I'm using Ubuntu 10.10 64bits and finally my problem is solved.

Works PERFECTLY!!

---

### Post by rakete on 2010-10-20
> **glazs said:**
> [COLOR=Green][SIZE=3][FONT=Trebuchet MS]**Tried [this]("https://bugs.launchpad.net/udev/+bug/637208/comments/40"). Maybe works, if not help i post here. Looks like solution :).**[/FONT][/SIZE][/COLOR]

Sry for text style, its important.

worked for me after rebooting with Microsoft Arc Keyboard (wireless) and 10.10 32bit..

thx, guys...

---

### Post by rkues on 2010-10-22
That worked for both my wireless and wired usb keyboard / mouse. After many problems with nvidia drivers + 2.6.35 kernel + custom edid + usb input, things are finally (as it seems) working smooth with my 10.10 amd64 install :)

Many thanks again.

---

### Post by BJNK on 2010-10-23
The 64 bit version goes to an invalid link. Looking at the launchpad, I cannot find an update.  Any possibility of helping a brotha out?

---

### Post by digbysellers on 2010-10-24
What a disgrace. This happened to me before when upgrading from 9.04 to 9.10. This time I have not even, to my knowledge, installed or upgraded any software for at least one month...

---

### Post by diazdiego86 on 2010-10-24
people... i'm running ubuntu 1.10 64 version. This link seems to be broken. Anyone could attach this .deb file? This is really annoying.


Thanks!

---

### Post by jnylen on 2010-10-24
For those of you who can't find the package, try this:

[https://edge.launchpad.net/~raof/+archive/aubergine](https://edge.launchpad.net/~raof/+archive/aubergine)

To install:

```
sudo apt-add-repository ppa:raof/aubergine && sudo apt-get update && sudo apt-get upgrade
```

After that you'll probably need to reboot.  I'm on 64 bit and it works for me.

---

### Post by BJNK on 2010-10-25
Thanks for that. I ran the commands, and it seemed to install successfully, but it did not fix the problem.  In fact it may have gotten worse.

Now as soon as I touch my trackpad, it acts as if I've left clicked and not released.  So if I am typing it will try and select all the text, wherever the pointer goes.

> **jnylen said:**
> For those of you who can't find the package, try this:

[https://edge.launchpad.net/~raof/+archive/aubergine](https://edge.launchpad.net/~raof/+archive/aubergine)

To install:

```
sudo apt-add-repository ppa:raof/aubergine && sudo apt-get update && sudo apt-get upgrade
```

After that you'll probably need to reboot.  I'm on 64 bit and it works for me.

---

### Post by Myoga- on 2010-10-27
> **jnylen said:**
> For those of you who can't find the package, try this:

[https://edge.launchpad.net/~raof/+archive/aubergine]("https://edge.launchpad.net/%7Eraof/+archive/aubergine")

To install:

```
sudo apt-add-repository ppa:raof/aubergine && sudo apt-get update && sudo apt-get upgrade
```After that you'll probably need to reboot.  I'm on 64 bit and it works for me.

Thanks! Worked wonderfully ^^

---

### Post by DoneRightI.T. on 2010-10-29
> **pawloch said:**
> [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.5.0+git20100822.990540fa-0ubuntu0sarvatt_amd64.deb](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.5.0+git20100822.990540fa-0ubuntu0sarvatt_amd64.deb) - works for 64 bit version

[http://launchpadlibrarian.net/54205518/xserver-xorg-input-evdev_2.5.0%2Bgit20100822.990540fa-0ubuntu0sarvatt_i386.deb](http://launchpadlibrarian.net/54205518/xserver-xorg-input-evdev_2.5.0%2Bgit20100822.990540fa-0ubuntu0sarvatt_i386.deb) - worsk for 32 bit version

(by [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311) and [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/637208?comments=all](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/637208?comments=all))

the 64 bit version is a broken link...

---

### Post by Mokurai on 2010-10-31
I have had similar but more complex problems through several versions of Ubuntu. Some left mouse functions don't work, while others are fine, and there are other symptoms. Right now, I can't use the Application menu on the toolbar. Now I can. Now I can't again. 

I just played a game of Mines. Everything works, except the final mouse click to start a new game or quit. (Workaround: tab between buttons, and use Return to activate one.)

I most often get the problem in Firefox, where I spend most of my time writing (at FLOSS Manuals and various blogs) and researching.

Previously, I could escape this problem temporarily by creating a new user and moving all my files over. Not this time in Meerkat. Or maybe there is a way. In my experiment, I reused an old account name. What if I use a completely new name? I have to restart now, but I'll let you know.

---

### Post by Mokurai on 2010-10-31
> **randomf said:**
> sudo rmmod usbhid; sudo mobprobe usbhid

helps, but sometimes the mouse button stucks even 3 - 4 times a minute.

s/mobprobe/modprobe

sudo rmmod usbhid; sudo modprobe usbhid

---

### Post by Mokurai on 2010-10-31
> **Mokurai said:**
> Previously, I could escape this problem temporarily by creating a new user and moving all my files over. Not this time in Meerkat. Or maybe there is a way. In my experiment, I reused an old account name. What if I use a completely new name? I have to restart now, but I'll let you know.

It's working better so far, but only time will tell. Now I have to get my bookmarks and passwords, fix up my menus, and twiddle a few other things, while not copying over anything that could bring the mouse problem back.

More when I know more.

---

### Post by Mokurai on 2010-11-02
Nope, the problem came back in the new account, too.

---

### Post by cake nom nom on 2010-11-04
> **glazs said:**
> [COLOR="Green"][SIZE="3"][FONT="Trebuchet MS"]**Tried [this]("https://bugs.launchpad.net/udev/+bug/637208/comments/40"). Maybe works, if not help i post here. Looks like solution :).**[/FONT][/SIZE][/COLOR]

Sry for text style, its important.

 the link is dead now

---

### Post by spodesabode on 2010-11-05
Those links are dead now and I'm suffering from the same problem. Is there a fix?

---

### Post by bgenc on 2010-11-06
> **spodesabode said:**
> Those links are dead now and I'm suffering from the same problem. Is there a fix?

```
sudo apt-add-repository ppa:raof/aubergine && sudo apt-get update && sudo apt-get upgrade
```

this worked for me on my Sony VAIO, 64 bit with A4Tech usb wireless mouse.

---

### Post by kwiatu5 on 2010-11-07
> **cake nom nom said:**
> the link is dead now
yep. this link is dead now but here is a mirror of [http://launchpadlibrarian.net/54205518/xserver-xorg-input-evdev_2.5.0%2Bgit20100822.990540fa-0ubuntu0sarvatt_i386.deb:](http://launchpadlibrarian.net/54205518/xserver-xorg-input-evdev_2.5.0%2Bgit20100822.990540fa-0ubuntu0sarvatt_i386.deb:)
```
http://dl.dropbox.com/u/2552069/trash/xserver.deb
```

---

### Post by nagaraj on 2010-11-22
> **glazs said:**
> [COLOR="Green"][SIZE="3"][FONT="Trebuchet MS"]**Tried [this]("https://bugs.launchpad.net/udev/+bug/637208/comments/40"). Maybe works, if not help i post here. Looks like solution :).**[/FONT][/SIZE][/COLOR]

Sry for text style, its important.

hi, finally found somethimg on this nagging issue. but the link seems to have disintegrated.can anybody repost wjere the .deb patch is?
thanks

---

### Post by beosound on 2010-11-22
> **bgenc said:**
> ```
sudo apt-add-repository ppa:raof/aubergine && sudo apt-get update && sudo apt-get upgrade
```

this worked for me on my Sony VAIO, 64 bit with A4Tech usb wireless mouse.

I've tried this solution, but it doesn't work. I was wondering, if somebody would upload the x64-xserver-package again?

---

### Post by grant.pirie on 2010-11-22
I have had the same problem but it has also contaminated my vista os - I have re-installed both ubuntu and vista and it keeps following me now, it works for a short time then stops - I can only use vista now as I don't know how to use ubuntu without the mouse.

Running out of options, can anyone help??

---

### Post by nagaraj on 2010-11-22
always wondered why meerkats are called so ('meerkat' in dutch means 'lake cat'). now i know why.    ?????   
obvious isn't it? meerkat hates MOUSE - atleast this one does. 
i have 5 pcs and 2 laptops with maverick meerkat - 2 pcs and 2 laptops are upgraded from 10.04 and 3 are clean new installations. all new installations are having problems with mouse but all upgraded ones are working fine!!! 
is this the case with others? 
found this ppa link in another forum. 
[https://edge.launchpad.net/~raof/+archive/aubergine]("https://edge.launchpad.net/~raof/+archive/aubergine")
tried it. worked fine on one pc but did not work on other 2 pcs. planning to revert to 10.04 if no solution turns up in another week

---

### Post by foo-nix on 2010-11-25
In my case all the previous suggestions FAILED.

But one worked after some googling, the one with the green font. The link was broken. So I searched for the evdev package, and the one with version 2.5 or higher. I found a package for DEBIAN, installed it in UBUNTU and restarted gdm (you can simply restart the whole machine if you don know how to restart gdm).

I found the package here:

[http://packages.debian.org/search?keywords=xserver-xorg-input-evdev](http://packages.debian.org/search?keywords=xserver-xorg-input-evdev)

But if you **google** for "**xserver-xorg-input-evdev 2.5.0**" you might find something else too.

You can install the deb file using:

**dpkg -i <debfile>**

and restart gdm using:

**/etc/init.d/gdm restart**

**which will terminate and restart your gnome session.**

Doing this is hacky and has consequences, the package is experimental and not meant for ubuntu. So, this is not a nice solution. It could cause data loss.

But I preffer it against the tedious solution someone in the #ubuntu irc channel gave me:

<foo-nix> My left mousebutton fails to work after I press a mediabutton. I found a forumpost on this suggesting that installing evdev would work. I did, but this didn help.
<foo-nix> any suggestions?
<foo-nix> I completely updated my software
<foo-nix> and rebooted afterwards because also the kernel was updated
<foo-nix> but still, my left mb fails after pressing a media key like volume up
<nomtv80> ***stop using media keys*** k
<nomtv80> jk
<foo-nix> nomtv80, are you seriously suggesting to stop using media keys? btw, these problems were posted on the forum in August. Given the popularity of the bug, I would think someone has a fix

---

### Post by nitroprdez on 2010-12-12
I had exactly the same problem and here's how to solve it.
 Open terminal and type:
```


     sudo apt-get repository ppa:raof/aubergine
     sudo apt-get update
     sudo apt-get upgrade

``` ...and when update/upgrade is complete,reboot your system and VOILA! mouse (including left click) works. :)
 

 as seen on
 [https://launchpad.net/~raof/+archive/aubergine]("https://launchpad.net/%7Eraof/+archive/aubergine")
 

 Another possible solution (I didn't try it out,but it's said to be working) is to download and install .dab files from these locations:
 
[COLOR=Red]
[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.5.99.901+git20101204.31ba99e9-0ubuntu0sarvatt_i386.deb](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.5.99.901+git20101204.31ba99e9-0ubuntu0sarvatt_i386.deb)[/COLOR]  [COLOR=Red] for x86 version[/COLOR]
 
[COLOR=Red]
[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.5.99.901+git20101204.31ba99e9-0ubuntu0sarvatt_amd64.deb](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.5.99.901+git20101204.31ba99e9-0ubuntu0sarvatt_amd64.deb)[/COLOR]  [COLOR=Red] x64 version.[/COLOR]


I'm glad if anyone find this usable,because I googled so hard to find the solution for this (not so small) problem.

---

### Post by JoaoCunha on 2011-03-14
Hello. I re-installed my ubuntu 10.10 64 bits. And again, i faced this problem. Only this time, the link for 64 bits was broken!! :o

But i found all the versions here \\:D/: 
[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-input-evdev/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-input-evdev/)

For people who has the same system as me, i used this one (second choice i guess): 
[xserver-xorg-input-evdev-dev_2.5.99.901+git20101204.31ba99e9-0ubuntu0sarvatt~maverick_all.deb]("http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev-dev_2.5.99.901+git20101204.31ba99e9-0ubuntu0sarvatt%7Emaverick_all.deb")

Problem solved.

---

### Post by Drengur on 2011-03-20
I have a similar problem after installing 10.10 on my desktop. I have tried two different USB mice but to no avail. I installed the aforementioned .deb package but that did not help.

My problem is that sometimes the mouse buttons work and sometimes they do not. It seems that, more than not, clicking the window-bars or the gnome-panels has the effect of suspending my mouse buttons. Sometimes the keyboard to. (The keyboard is a PS2 keyboard). 

I have not pressed any media-buttons or such. ```
:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Gaming Mouse1600 Gaming Mouse1600       	id=8	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
```

---

### Post by Teddibear on 2012-05-03
I recently experienced something very similar to this bug. I've upgraded to 12.04 (all the way from 10.10) a few days and changed to KDE desktop (this never happened with Gnome). As I was clicking on the taskbar, the mouse cursor suddenly turned into a 'stop' sign and stopped responding to any mouse event, other than moving. Clicking and scrolling no longer did anything. Alt-tab and alt+F2 worked just fine, so I was able to start a konsole window and see that mouse did still generate events (with xinput), but for whatever reason the events were not propagated upwards to KDE, or it was somehow 'stuck'.

I tried just about anything I could think of, disabled and re-enabled the mouse, unplugged it, and tried to restart kwin, but to no avail. Finally I did manage to find a workaround. By installing xdotool, ```
sudo apt-get install xdotool
``` I was able to switch to another desktop ```
xdotool set_desktop 1
``` and like magic, the mouse worked perfectly again. The strange thing is, I found a stray window on the other desktop, one that I had never moved there in the first place!

Since there haven't been any replies to this thread in roughly a year, I'm not sure this is the same bug (I cannot seem to be able to reproduce it at will), but hopefully my workaround/fix will help someone.

---

### Post by soyatti on 2012-12-19
i've faced the same issue in Ubuntu 12.04 too.
after disabling my bluetooth mouse touchpad begins to work normally.

---

### Post by oldos2er on 2012-12-19
Old thread closed.

---


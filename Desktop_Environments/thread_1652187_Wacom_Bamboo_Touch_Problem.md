---
title: "Wacom Bamboo Touch Problem"
date: 2010-12-24
forum: Desktop Environments
---

### Post by RodrigoRodrigues on 2010-12-24
Hi,
I am running Kubuntu 10.10 x64, using a Wacom Bamboo (CTH-460), I installed it by compiling the driver and moving the file as in every tutorial I could find in the Internet.

The pen works perfectly, except by the fact I use TwinView and the tablet uses all the width, too sensitive. but this is something I plan to fix later... (pressure is OK)

the problem is the touch..

It almost works,
right click, zoom and scroll support is ok, I believe there is no support to rotation but I can live without it...
The problem is the cursor movement, seems to be a sensitivity issue.
If I move very slow there is no problem, but if i move a little faster the cursor stops as if I had removed the finger from the sensor.
When I try to scroll or zoom I have a similar problem, it moves an inch before it start to scroll as if it wasn't sensing the second finger, but right click is perfect so I don't think this is the problem.

Would this be a bug?

Is there a way to calibrate the touch sensor? I remember editing the xorg.conf to make the touch fit the screen size in a HP Tx2510us, and to make two finger scroll on to touch pad but it was in 8.10 I believe, I cant find something like it for this problem.

wacomcpl cant see the device, xsetwacom list returns nothing...
xinput list returns this:


&#9121; Virtual core pointer                    id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer          id=4    [slave  pointer  (2)]
&#9116;   &#8627; A4Tech PS/2+USB Mouse               id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Pen eraser  id=10   [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Pen stylus  id=11   [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Finger pad  id=12   [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 4x5 Finger touch id=13  [slave  pointer  (2)]
&#9123; Virtual core keyboard                   id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard         id=5    [slave  keyboard (3)]
    &#8627; Power Button                        id=6    [slave  keyboard (3)]
    &#8627; Power Button                        id=7    [slave  keyboard (3)]
    &#8627; Digital_Camera                      id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard        id=14   [slave  keyboard (3)]



My /usr/share/X11/xorg.conf.d/50-wacom.conf is this:
Section InputClass"
        Identifier "Wacom class"
        MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection                                                                                                                                    Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"                        
        Driver "wacom"
EndSection                                                                                                     
Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection                                                                                                     
# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001|N-Trig Pen"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        Option "Button3" "2"
EndSection

I got so used to this device I dont use a mouse anymore, So I really miss the touch.

Any ideas? what should I try?

---

### Post by Favux on 2010-12-24
Hi RodrigoRodrigues,

Right now touch is a little wonky.  They are changing the original linuxwacom MT code over the new Xorg MT specifications in both the X driver and the kernel.  You can play with the settings like I suggest in "Touch & Gesture Tips for the Bamboo in Linux" at the bottom of the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

There are fairly frequent updates to xf86-input-wacom for MT and filtering logic and so on.  But things probably won't settle until the MT kernel code starts coming through.  It was just accepted recently to linux-input for the 2.6.37 kernel.

---

### Post by RodrigoRodrigues on 2010-12-24
Hi Favux, Thanks for the quick reply,
I tried the instructions on the link but xsetwacom cant see any device

Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'Wacom BambooFun 2FG 4x5 Pen Finger touch'

probably because of the frequent changes you said.
I'll have to wait for the next kernel, if I fix it now it will probably stop working when I update.

---

### Post by Favux on 2010-12-24
You may be using the wrong device name in the xsetwacom commands.  Are you using the ones from your 'xinput --list' in quotes?  It's possible another driver has your touch.  We could check out your Xorg.0.log in /var/log.  Also if you've managed to put two versions of xsetwacom on your system there may be a conflict.

I don't think you need to wait to the next kernel to get some useful function.

---

### Post by RodrigoRodrigues on 2010-12-24
Favux,
The device name was wrong, but xsetwacom was not working... I tried to set Touch "off" in every device and nothing happened.. so I tried your tutorial from the begin, wich was a lot bigger than the one I used before, at the end of Step 2 it was working perfectly!

Thanks a lot!

---

### Post by FrankyG on 2011-01-09
Hi Folks,

I just bought a Bamboo T&P CTH-460 and am having trouble to get it up and running on my Lucid system. I followed the link to Favux' Tutorial above and just stumbled across the comment that 2 of 5 new models aren't supported yet.

The following command on a terminal gives:
```
$ lsusb | grep Wacom
Bus 006 Device 003: ID 056a:00d6 Wacom Co., Ltd
```I know that "056a" is the manufacturer id. So, is "00d6" the device id then? This would mean, that my device is not supported yet, right? (see table and comment on tutorial page)

If so, are there any plans on when this device will be added? How can I help?

Regards, Frank

---

### Post by Favux on 2011-01-09
Hi Frank,

Yes the oxd6 is a new model.  Turn your tablet over.  What does the label call it?  Mine says:

Model:  CTH-460

Does yours say:

Model:  CTH-460/K?

Right below the model box near the top of the Bamboo HOW TO is (blue) text which explains and links you to instructions to add your model.

I guess I need to rewrite the instructions.  I think I'll post them in post #2 on the HOW TO.

---

### Post by FrankyG on 2011-01-10
Hi Favux,

thanks for your quick reply. Really appreciated.

My label on the back reads: CTH-460/K(A)
(see attached scan of the label)

So, should I exactly follow the instructions in Post [#309]("http://ubuntuforums.org/showpost.php?p=10090630&postcount=309") or do I need to modify some identifiers/values first?

---

### Post by Favux on 2011-01-10
Hi Frank,

I pulled the separate posts together and made a mini-HOW TO for the new models and put it in post #2 on the thread.  Changed the instructions in the model box in the HOW TO.  Hopefully the mini HOW TO is clear.

---

### Post by Favux on 2011-01-10
Awesome!  The most duplicate posts ever!  Something wrong with the Ubuntu Server.

---

### Post by Favux on 2011-01-10
Hi Frank,

I pulled the separate posts together and made a mini-HOW TO for the new models and put it in post #2 on the thread.  Changed the instructions in the model box in the HOW TO.  Hopefully the mini HOW TO is clear.

---

### Post by Favux on 2011-01-10
Hi Frank,

I pulled the separate posts together and made a mini-HOW TO for the new models and put it in post #2 on the thread.  Changed the instructions in the model box in the HOW TO.  Hopefully the mini HOW TO is clear.

---

### Post by Favux on 2011-01-10
Hi Frank,

I pulled the separate posts together and made a mini-HOW TO for the new models and put it in post #2 on the thread.  Changed the instructions in the model box in the HOW TO.  Hopefully the mini HOW TO is clear.

---

### Post by FrankyG on 2011-01-10
Hmm, weird server... :P

I guess with mini-HOW TO you mean this post here:
[http://ubuntuforums.org/showpost.php?p=9496756&postcount=2](http://ubuntuforums.org/showpost.php?p=9496756&postcount=2)

I'lll try your instructions later...

Thank you,
Frank

---

### Post by sanso on 2011-01-11
> **FrankyG said:**
> 
I guess with mini-HOW TO you mean this post here:
[http://ubuntuforums.org/showpost.php?p=9496756&postcount=2](http://ubuntuforums.org/showpost.php?p=9496756&postcount=2)

I'lll try your instructions later...

That just worked for me and my CTH-460/K.
Thank you so much! Touch is _very_ wonky still (essentially it just moves the cursor to the left edge of the screen) but stylus/eraser work beautifully.

Much appreciated,

Richard

---

### Post by Favux on 2011-01-11
Hi Sanso,

Good.  Yes, touch is broken right now due to some major changes they made.  The LWP knows that and are working on it.  Hopefully it will be fixed shortly and better than ever.  When that happens you'll just redo part II.

---


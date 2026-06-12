---
title: "Using PS3 Controller?"
date: 2010-05-15
forum: Gaming &amp; Leisure
---

### Post by Cam! on 2010-05-15
I have a PS3 controller that I want to use to play with Emulators and regular games. I have 64-bit 10.04. How would I go about doing this?

---

### Post by Sockerdrickan on 2010-05-15
> **Cam! said:**
> I have a PS3 controller that I want to use to play with Emulators and regular games. I have 64-bit 10.04. How would I go about doing this?
[http://tinyurl.com/26yb3a7](http://tinyurl.com/26yb3a7)

---

### Post by kiddykoff on 2010-05-15
i've looked into this myself and followed the documentation here, [https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis)

I came across some difficulty with using the tools downloaded, but i'm fine with using a usb cable, which just works. I'll look into it again when i upgrade to lucid.

---

### Post by ZereoX on 2010-05-15
Download QtSixA. It allows you to use a PS3 controller by USB or Bluetooth.

[http://sourceforge.net/projects/qtsixa/](http://sourceforge.net/projects/qtsixa/)

Works really well. I'm currently using it under 10.04.

---

### Post by grondinmf on 2010-05-18
i was following this guide

[https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis)

i followed all to the letter but when i got to this part

Go into the bluez-utils-x.xx directory and run

$ mv <path_where_you_saved_it>patch-hidd-3.19-pabr3 .
$ patch -p1 < patch-hidd-3.19-pabr3

i got this in response:
patching file hidd/main.c
Hunk #1 FAILED at 87.
Hunk #2 FAILED at 128.
Hunk #3 FAILED at 240.
3 out of 3 hunks FAILED -- saving rejects to file hidd/main.c.rej

is this info outdated or what did i do wrong?

---

### Post by Cam! on 2010-07-02
> **ZereoX said:**
> Download QtSixA. It allows you to use a PS3 controller by USB or Bluetooth.

[http://sourceforge.net/projects/qtsixa/](http://sourceforge.net/projects/qtsixa/)

Works really well. I'm currently using it under 10.04.

How do I use this via USB? It only seems to have Bluetooth settings.

---

### Post by Cam! on 2010-07-02
**Double Post**

---

### Post by TxRxBuffer on 2010-07-06
i'm also interested in getting the sixaxis working under ubuntu 10.04.

---

### Post by benmoran on 2010-07-06
This thread contains the most up to date information:
[http://ubuntuforums.org/showthread.php?t=1190061&highlight=qtsixa](http://ubuntuforums.org/showthread.php?t=1190061&highlight=qtsixa)
You no longer have to modify anything to do with the bluetooth stack.

---

### Post by efikkan on 2010-07-06
Does force feedback/vibration work?

---

### Post by metalf8801 on 2010-07-07
another good program is QjoyPad 

to install QyoyPad first your going to need to add the playdeb repository
[http://www.playdeb.net/updates/ubuntu/10.04/#how_to_install](http://www.playdeb.net/updates/ubuntu/10.04/#how_to_install)

then you can install QjoyPad using [http://www.playdeb.net/](http://www.playdeb.net/) or you can use Synaptic (Cam! because you are using Ubuntu 64 bit I would use Synaptic to install QjoyPad you might not need to but thats what I would do) 

after you install QjoyPad I think it will be in 
Applications > Accessories 
you maybe able to get it to work using bluetooth but I never tried so I can't help you with that but it does work just fine using the USB cable 

Your going to need to plug in your controller before opening QjoyPad then once you do just use "Quick Set" its the second button from the bottom on the right side 
you use Quick Set by pressing a button on your gamepad which in this case is a PS3 controller then press the key on your keyboard or mouse that you want to assign to it
Then when your done you will want to Add the new layout to the drop down menu on the top so that you don't need to create a new layout every time 

for example the layout I use to play Opensonic is 
Button 1: Return 
Button 4: Return 
Button 5: up 
Button 6: Right
Button 7: Down 
Button 8: Left 
Button 9: L Control 
Button 13: Space 
Button 14: Space
Button 15: Space
Button 16: Space

You can also use QjoyPad to configure the Axis so the motion of the controller can be used to control a game but this is also something I haven't tried yet 

for more info on [http://qjoypad.sourceforge.net/](http://qjoypad.sourceforge.net/) 

PS there is also a Rejoystick but it doesn't look nearly as good as QjoyPad in fact it just looks like a stripped down version of QjoyPad 

one problem I ran into with QjoyPad was that it wouldn't fit on the my desktops monitor no matter what resolution I used as a simple work around I just had to hold Alt then click on QjoyPad drag it up so that the top of it was off the screen but could still click on Quick Set then when I was done use Alt and the Mouse again to drag it back down to so I could click on Add 

Good luck 
Dan

---


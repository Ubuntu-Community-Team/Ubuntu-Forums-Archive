---
title: "Microsoft Wireless Notebook Laser Mouse 6000"
date: 2006-04-23
forum: Desktop Environments
---

### Post by firecrotch on 2006-04-23
Hello,

I just bought a Microsoft Wireless Notebook Laser Mouse 6000.  It has an extra button on the left side of it, which normally acts like the right mouse button.  Is there any way in which I can change the behavior of this button?  Thanks in advance.

---

### Post by firecrotch on 2006-05-11
I did a little bit of reading about configuring your mouse in X11, but I'm completely lost.  I can't even figure out what buttons are mapped to which button codes.  If it helps, the mouse has the two normal buttons, a tilt wheel (which doubles as a middle mouse button) and a thumb button, which currently acts the exact same as the right button.  The up-down scrolling works, as does the middle mouse button functionality of the wheel, but the left-right tilt does not.  I'd really love to get at least the thumb button working properly.  Thanks in advance.

---

### Post by vidak on 2006-05-13
Not a real help, but there is a tool named xev - maybe you could figure out the codes produced by your mouse...

---

### Post by firecrotch on 2006-05-17
Actually, that was quite helpful! It turns out that the thumb button is registering as "button 3", which is the same as the right mouse button.  Is there a way I can change this behavior and set it to "button 6" perhaps?

---

### Post by vidak on 2006-05-17
I tried xev with my mouse, and all the buttons produce different events, from 1 to button7, so it looks like a very mean situation...
But since it's linux we are speaking about there should be a solution.. :)
...
After some search I found this in an other forum:
Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "IMPS/2"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "no"
        Option      "Buttons" "10"
EndSection

This is a part of the config file /etc/X11/xorg.conf.
Make a backup of this file, and look in it... You shouldn't care about the whole file, but maybe the "Buttons 10" line can be helpful, however I am not sure about it. 
Tell me whether it works or not...

---

### Post by firecrotch on 2006-05-17
I tried playing around with that, but xev still shows the thumb button as button3.  Also, the tilt wheel does not register (scrolling up and down work fine, as button4 and button 5, but left and right do not give me anything in xev.).

---

### Post by vidak on 2006-05-17
after hacking xorg.conf, and putting "Button" "10" in?
In that case I got no idea... :( but there surely is a solution

---


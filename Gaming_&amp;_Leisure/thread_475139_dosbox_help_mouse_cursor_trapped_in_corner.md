---
title: "dosbox help mouse cursor trapped in corner"
date: 2007-06-15
forum: Gaming &amp; Leisure
---

### Post by cor2y on 2007-06-15
Hi i am in Feisty Fawn with the repo version of dosbox installed.
Its been in a while since i used it.
But when i tried it today my mouse cursor for all my games vanished it was only after going full screen that i discovered it was in the lower right corner of the screen.
It seems disabled and only the keyboard inputs work.
As for other inputs like joysticks etc. they work but they have now become super sensitive just a nudge to the left or right sends sprites moving forever until you pull the opposite direction.
When i was in Dapper i didn't experience this problem.

Any ideas on what could be causing this?

---

### Post by dli8ilb on 2008-10-05
i am having the same problem you decribe when playing cretain games like super maryo chronicles, and tremulous etc.

found some bugs that describe the problem:
[https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/189958](https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/189958)
[https://bugs.launchpad.net/ubuntu/hardy/+source/xserver-xorg-input-evdev/+bug/205480](https://bugs.launchpad.net/ubuntu/hardy/+source/xserver-xorg-input-evdev/+bug/205480)

it seems that starting the game/program with for example:

```
tremulous - export SDL_VIDEO_X11_DGAMOUSE=0
```

works around the problem..i'll be investigating this further and report back

EDIT

adding this to xorg conf seems to fix it altogether:
```
Section "Module"
    SubSection "extmod"
        Option "omit xfree86-dga" # don't initialise the DGA extension
    EndSubSection
```

hope this helps.

---

### Post by Meow27 on 2008-10-05
well, the same thing happens in windows, the difference is you can alt+tab out of it in windows while in linux you cannot

best way i know how to get access back is to do alt+enter (full screen) twice in order to get ur mouse to move again (which you ahve mentioned)

you can disable the mouse lock somewhere in the _dosbox .conf file_ but if ur running games, i highly recommend you to NOT deactivate it...... it will be like running a flash game that was written in flash player 6

---

### Post by cantormath on 2009-04-27
[http://www.dosbox.com/wiki/FAQ](http://www.dosbox.com/wiki/FAQ)

DOSBox will capture your mouse when you click inside the display window (and you have **autolock=true** set in the Dosbox.conf).  Simply press **CTRL-F10** to release the mouse.

---

### Post by Jesperai on 2009-12-17
> **dli8ilb said:**
> 
```
Section "Module"
    SubSection "extmod"
        Option "omit xfree86-dga" # don't initialise the DGA extension
    EndSubSection
```

hope this helps.

This worked perfectly in 8 LTS

Thanks!

---


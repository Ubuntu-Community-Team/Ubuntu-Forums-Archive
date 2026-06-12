---
title: "HOWTO: make usb mouse better in fps games"
date: 2007-01-01
forum: Gaming &amp; Leisure
---

### Post by kvonb on 2007-01-01
* This works for my USB MS wheelmouse optical, I don't know if it works with any other mice but it should *

I've being playing Wolfenstein ET for a few weeks now and sucked big time!

I couldn't hit a damn thing and didn't know why, surely I'm not THAT bad?

Well I found out that mouse resolution is a BIG factor, and this little trick improved my game by leaps and bounds.

* This was taken from [http://www.linux-gamers.net/](http://www.linux-gamers.net/), and my thanks go to them *

Open a terminal and type the following:

```
sudo gedit /etc/modprobe.d/options
```

....add this to the end of the file:

```
options usbhid mousepoll=1
```

....save and exit the editor.

There is a fancy way to re-initialise the usb module, but I can't remember what it is so I'll just take the easy way out and tell you to reboot now :rolleyes:.


Try your game new and see the difference, I tried it again with the normal setting and was shocked at how bad it was, so I know that this definately works.

All I've got to do now is practice!

Regards, Kev (aka ubuntu-42 in ET land).

---

### Post by handy on 2007-01-02
One of the very few niggles I have with Ubuntu (linux) is the slow response of the mouse when playing Guild Wars, it is irritating, not a biggie.  The mouse sticks, when using Ubuntu for other things too but that doesn't really worry me.

So I have edited as you suggest, but am unable to shut the machine down for a couple of days, so I don't know if it works for me or not.  I expect it will, I had a look on linuX-gamers & read the how-to there as well.

Thanks for passing it on, when I test it I'll post my findings here.

If anyone knows the command to reintitialise the USB I'd be most grateful... :KS

---

### Post by po0f on 2007-01-02
handy,

```
[FONT="Courier New"]$ sudo modprobe -r usbhid && sudo modprobe usbhid[/FONT]
```
should work.

[EDIT]

Added 'sudo' to last modprobe command.

---

### Post by flargen on 2007-01-02
> **po0f said:**
> handy,

```
[FONT="Courier New"]$ sudo modprobe -r usbhid && modprobe usbhid[/FONT]
```
should work.

Unless I am much mistaken this command will not be able the insert the module because the "modprobe usbhid" is not running as root. It should be:
```
sudo modprobe -r usbhid && sudo modprobe usbhid
```

---

### Post by po0f on 2007-01-02
flargen,

Silly typo, thanks for pointing it out.  :rolleyes:

---

### Post by handy on 2007-01-03
My mouse still sticks... :( 

Using **mousepoll=1** caused some strange things to happen on the desktop.

Changing it to **mousepoll=2** fixed it, but I still have a sticky mouse?

---

### Post by kvonb on 2007-01-03
> **handy said:**
> My mouse still sticks... :( 

Using **mousepoll=1** caused some strange things to happen on the desktop.

Changing it to **mousepoll=2** fixed it, but I still have a sticky mouse?

That's sad, what type of mouse is it, and can you describe the "sticking"?  Not that I can be much  help, but you never know :).

---

### Post by handy on 2007-01-04
M$ intellimouse explorer,

It is not everytime I moove the mouse, but often if sits still for a bit then when I go to move the mouse it doesn't move straight away.

Particularly noticeable when playing Guild Wars & you are selecting (using) items in your skill bar, it can take a bit of wobbling around of the mouse before you get your pointer free...

I don't think it has directly cost me lives, but it surely does cost HP from time to time! :)

---

### Post by kvonb on 2007-01-04
> **handy said:**
> M$ intellimouse explorer,

It is not everytime I moove the mouse, but often if sits still for a bit then when I go to move the mouse it doesn't move straight away.

Particularly noticeable when playing Guild Wars & you are selecting (using) items in your skill bar, it can take a bit of wobbling around of the mouse before you get your pointer free...

I don't think it has directly cost me lives, but it surely does cost HP from time to time! :)

Maybe look at power management, in Linux and also in your BIOS.  I always had that problem before, but it doesn't happen in Edgy anymore.  Although I am on a new mainboard!  Also I now have usb2, maybe that is the difference?  Give it a go and see.

Regards, KEv :)

---

### Post by handy on 2007-01-04
I'm on USB2 too... I have power management turned off in BIOS too?

---

### Post by kvonb on 2007-01-05
Hmm, maybe turn on the power management in BIOS and try toggling the USB interrupt, ie if it is on then turn it off, I think mine is off.  If you can download and burn a copy of the Edgy CD, maybe try it under that.  Another thought, I ALWAYS disable my onboard serial and parallel ports mainly because it frees up some interrupt lines, maybe try that if you aren't using them!  It may be the mouse itself, that is the ball mouse isn't it?  Maybe see if you can borrow another one and try that or see if you can find a newer one at a good price :).

Regards, KEv :)

---

### Post by kvonb on 2007-01-05
I just noticed that in the file /etc/modprobe.d/blacklist it has this:

```
# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

```

Maybe have a look at yours to see if that is present!

```
sudo gedit /etc/modprobe.d/blacklist
```

If not, try it and see :)

---

### Post by handy on 2007-01-05
Thanks for your input :) 

I tried not using my dark coloured mouse pad, & guess what, it seems to have been the trouble all along!

My mouse is an optical mouse, & it obviously likes a more reflective surface.

*This is a Ubuntu (linux) associated problem, because it didn't, doesn't & won't lag, if I put a windoze drive in my machine & boot it?!*

Easy fix though, it has only taken me a little over a year to find it! :KS

To be honest I haven't ***really*** looked at it until your thread came along... :-)

---

### Post by kvonb on 2007-01-06
Glad to hear you got it sorted :cool:.  I should have mentioned that, I use a table place setting mat as my mouse "pad", laser mice don't like plain surfaces it seems :rolleyes:.

---


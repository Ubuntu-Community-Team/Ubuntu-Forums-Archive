---
title: "Two-Finger Scrolling with Inspiron 1545 - 9.10 Karmic"
date: 2009-11-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dshan on 2009-11-18
I've got a brand new Inspiron 1545 (ALPS touchpad) running 9.10 64-bit and when I enable two-finger scrolling (vertical & horizontal) in System>Preferences>Mouse>Touchpad it does not scroll, but if I set edge scrolling instead it works fine.

I also have an old Inspiron 1300 running 32-bit 9.10 and both two-finger and edge scrolling works fine on that system when configured using the mouse>touchpad preference pane. I guess the difference is due to different touchpad hardware?

I've read threads about using gsynaptics, setting shared mem parameters, etc. but as far as I can see gsynaptics doesn't support two-finger scrolling, only edge scrolling, and it isn't really applicable to 9.10 anyway as the touchpad scrolling options are now included in the mouse pane. From what I can make out the available synaptics configuration info is applicable to 9.04 and earlier only, there seems to be nothing for 9.10? 

Does anyone have any idea why two-finger works on the 1300 but not on the 1545 and if anything can be done to fix it on the 1545?

---

### Post by crpenaherrera on 2009-11-28
> **dshan said:**
> Does anyone have any idea why two-finger works on the 1300 but not on the 1545 and if anything can be done to fix it on the 1545?

It does not work in a Toshiba Satellite A305 either. Comments are suggestion are very welcome!

---

### Post by dshan on 2009-11-29
I've done a bunch of testing since my original post and have had no luck getting this to work. Interestingly, looking at the Dell touchpad utility under Win7 shows that it doesn't support *any *multifinger gestures. Even zooming is performed by leftside scrolling rather than pinching or whatever. I suspect this is because the Alps touchpad simply doesn't support multifinger operations.

If anyone knows differently I'm certainly interested to hear about it, but for now it looks like the difference between the Inspiron 1300 and the 1545 is that the 1300 has a genuine Synaptics touchpad (I checked and it does) which supports two-finger gestures whereas the 1545 uses an Alps touchpad which doesn't.

---

### Post by Jeremy Jackins on 2009-11-29
[this]("http://pages.cpsc.ucalgary.ca/~jnjackin/docs/two_finger_scrolling-linux.html") method worked well for 2 synaptics touchpads that I tested (that don't support two finger scrolling out of the box), but didn't work on my alps touchpad. I would be grateful if people tried it out and told me their results.

---

### Post by dshan on 2009-11-29
> **Jeremy Jackins said:**
> [this]("http://pages.cpsc.ucalgary.ca/~jnjackin/docs/two_finger_scrolling-linux.html") method worked well for 2 synaptics touchpads that I tested (that don't support two finger scrolling out of the box), but didn't work on my alps touchpad. I would be grateful if people tried it out and told me their results.

Jeremy, thanks for that link, it's most interesting. Setting TwoFingerMinZ and TwoFingerMinW makes no difference to two finger scrolling on my 1545, it still doesn't work. But the interesting part is when I run synclient -m 300, f is always 0 (not touching the pad) or 1 (one or more fingers on the pad) and w *never* goes above 0 no matter how close or far apart my fingers are on the pad (z does register changes in pressure from one or more fingers). 

It seems I was correct, the Alps touchpad does not support multi-finger detection or operations. It cannot even be emulated as it doesn't  register w (width).

---

### Post by Marco A. on 2009-12-03
you flippin rock! I have a 1005ha and it works perfectly. thanks a lot

---

### Post by ludwigbaum on 2009-12-09
Karmic, fresh installation on Acer timeline 1810tz:

Two-finger-scrolling does not work, by no means. I wrote a fdi-file for hal, no luck.
The same problem with Mandriva 2010 and gnome-desktop.
In both cases, kernel >=2.6.31-14.

---

### Post by dshan on 2009-12-09
> **ludwigbaum said:**
> Karmic, fresh installation on Acer timeline 1810tz:

Two-finger-scrolling does not work, by no means. I wrote a fdi-file for hal, no luck.
The same problem with Mandriva 2010 and gnome-desktop.
In both cases, kernel >=2.6.31-14.

It seems to depend on what touchpad hardware you have - if it's a Synaptics touchpad it either works out of the box or can be made to work via fdi mods, etc., but if it's an Alps touchpad it seems it simply cannot recognise more than one finger at a time and cannot be made to two-finger scroll. 

I don't know if there are different models of Synaptics and Alps touchpads that might complicate the situation further but so far it seems to be a binary scenario - Synaptics = yes and Alps = no.

---

### Post by milesfromnowhere121 on 2010-01-28
> **Jeremy Jackins said:**
> [this]("http://pages.cpsc.ucalgary.ca/%7Ejnjackin/docs/two_finger_scrolling-linux.html") method worked well for 2 synaptics touchpads that I tested (that don't support two finger scrolling out of the box), but didn't work on my alps touchpad. I would be grateful if people tried it out and told me their results.

YOU ROCK!! Touchpad double-scrolling working on Toshiba Satellite A505 S6980.

---

### Post by sirgogo on 2010-02-09
This is legit.

Works on Dell XPS 1640. Nice job man, thanks.

---

### Post by wankel786 on 2010-02-20
> **sirgogo said:**
> This is legit.

Works on Dell XPS 1640. Nice job man, thanks.

Do you mind sharing your touchpad settings? I also have an xps 1640 and I cannot get two touch scrolling to work at all.

---

### Post by Kulgan on 2010-03-06
Could all of the people who got two-finger scrolling to work please state the hardware they are using - have we confirmed that nobody has it working with an Alps pad yet?

---

### Post by Kulgan on 2010-03-06
Scrap that. We can't emulate multitouch on the touchpad, as has been stated. However, because we can register pressure (and pressure is also a function of the area being touched) we can fool the pad into generating a two finger gesture by messing with the conditions. On:

```
I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input18
U: Uniq=
H: Handlers=mouse3 event17 
B: EV=f
B: KEY=420 70000 0 0 0 0
B: REL=3
B: ABS=1000003
```

Because, as previously stated, W never goes above 0:
```
synclient EmulateTwoFingerMinW=0
```

Then run
```
synclient -m 15
```
and see the difference between your average 1 finger touch and 2 finger touch. For me the boundary is at around 80. 

```

synclient EmulateTwoFingerMinZ=80
synclient VertEdgeScroll=1

```

This means that there is no requirement to have any width between the touch points. I am using pressure as the only means of differentiating between one or more fingers - it's sketchy but it works. Unfortunately this means that I don't think three-finger stuff will be possible using this method; the difference in pressure between two- and three-finger touches is not large enough, at least on my touchpad. 
Additionally, horisontal scrolling doesn't work... but on the other hand, it means you can scroll with one finger - if you press hard enough :)

I'm also having trouble settings some values in /etc/hal/fdi/policy/11-x11-synaptics.fdi:
```

<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>

	<merge key="input.x11_options.SHMConfig" type="string">On</merge>
        <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">80</merge>
	<merge key="input.x11_options.EmulateTwoFingerMinW" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
[...]

```
Where VertTwoFingerScroll is not set. I took this from elsewhere - should it in fact be ...type="bool">true...?

Edit:
Have been able to get two-finger click working using the same technique. However, it doesn't work properly - because you can't generate get enough pressure in without moving the fingers, thereby making it a scroll, the pressure has to go down to ~40, effectively turning the touchpad into a scrollpad. The alternative is to set SingleTapTimeout to ~600 and wiggle the fingers about a little. But that means you have to wait for ever for a normal tap to have effect, and it's easier to use the button >_>

---

### Post by capleton on 2010-03-11
Hey, I just wanted to say that I created a short tutorial on how to get multi-touch working.  It took me awhile before I could finally get it working, so I thought I would post in case anyone else finds themselves in my predicament.  [You can find it here.]("http://ubuntuforums.org/showthread.php?t=1426782#3")

---


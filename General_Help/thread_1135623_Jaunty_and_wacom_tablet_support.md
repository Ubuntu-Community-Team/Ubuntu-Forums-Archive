---
title: "Jaunty and wacom tablet support"
date: 2009-04-24
forum: General Help
---

### Post by ProhetOfDoom on 2009-04-24
Hi all,

I'm tempted to upgrade from intrepid to jaunty but I really need confidence that my wacom intuos 3 will still work.

I've heard you need to comment out the relevant bits in xorg.conf. That being the case can anyone confirm whether a wacom tablet works well under jaunty? By 'works well' I mean:

    * pressure sensitivty OK?
    * buttons on stylus OK?
    * stylus and eraser both work - ie both ends of the pen can have independent functions?
    * Buttons and touchstrip on actual tablet work ok?


Thanks in advance

---

### Post by El Zoido on 2009-04-24
Ok, I've got only an Bamboo Fun, but I testet it a bit using Gimp yesterday.

I had to set it up in Gimp first but then it worked.
So far the sensitivity seems to be ok to me, Eraser and Pen are working independently (though Eraser isn't fixed on an eraser, it's using whatever you used last with it).
The keys on the tablet are doing something, though not yet what I would like them to, so I'm not sure here.

All this worked out of the box, no modification of Xorg.conf or manual installation of drivers.
So far seems to work better than with Intrepid.

---

### Post by ajy0852 on 2009-04-24
I have a Bamboo fun too.

> **El Zoido said:**
> 
So far the sensitivity seems to be ok to me, Eraser and Pen are working independently (though Eraser isn't fixed on an eraser, it's using whatever you used last with it).

Yeah, it works great out of the box, way better than any other Ubuntu release so far

> **El Zoido said:**
> 
The keys on the tablet are doing something, though not yet what I would like them to, so I'm not sure here.

The keys on my tablet do not work, and the scroll wheel only seems to work one direction. Odd.

Any ideas? I hope we aren´t hijacking this... sorry...

---

### Post by solar george on 2009-04-25
Can I just point people to 
[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/355340](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/355340)
and
[https://launchpad.net/~tjaalton/+archive/ppa](https://launchpad.net/~tjaalton/+archive/ppa)

(Haven't tried it myself yet but it sounds good)

---

### Post by ProhetOfDoom on 2009-04-25
Thanks for the responses which were encouraging so I took the plunge and updated to Jaunty this morning. Here's my experience so far which might help others.

The upgrade itself was simple and seemed to work except that Jaunty was treating my Intuos 3 like a mouse, not a tablet. Tried rebooting, unplugiing the tablet etc but no change. So I reinstalled the hal packages and my wacom tablet sprang to life.

After setting the input devices in Gimp, I can confirm that pressure sensitivy is ok. The buttons on the stylus work. Both ends of the stylus can be used independently.

The buttons on the tablet itself no longer work. Furthermore xsetwacom commands no longer work. I'm guessing this is because it can no longer reference the old xorg.conf labels like 'eraser', 'stylus' and 'pad'. This means I can't limit my tablet to just one screen in a dual screen setup and presscurve etc won't work.

So thus far - enough functionality to keep me going but a backward step from Intrepid, unless I can get xsetwacom working

Not sure that the bug reference/link in the previous post refers to this issue but I'll check it out (thanks). Meanwhile - anyone managed to get xsetwacom working?


Thanks again

---

### Post by Favux on 2009-04-25
Hi everyone,

What I think Solar George (nice find!) is pointing to is rec's script that translates the HAL/D-BUS names into names linuxwacom understands so that xsetwacom works again.  This is the thread where he figured it out and first posted his script:  [http://ubuntuforums.org/showthread.php?t=1122952](http://ubuntuforums.org/showthread.php?t=1122952)  Then he posted it on the launchpad bug report site where Timo Aaltonen wanted feed back on his patched linuxwacom 0.8.2-2 packages.  We have a HOW TO on how to use the script on post #104 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)  If you aren't having any problems with your tablet other than xsetwacom then I don't think you need to compile the 0.8.3-2 wacom.ko kernel driver.  I'm guessing that since Timo posted the modified xorg ppa 2 days after rec posted his script it fixes things in xorg.xserver.  At least that's my guess as to what "* Add 176_remove_device_from_inputinfo.devices.diff." means.  Maybe Solar George could comment.

---

### Post by solar george on 2009-04-25
> What I think Solar George (nice find!) is pointing to is rec's script that translates the HAL/D-BUS names into names linuxwacom understands so that xsetwacom works again. This is the thread where he figured it out and first posted his script: [http://ubuntuforums.org/showthread.php?t=1122952](http://ubuntuforums.org/showthread.php?t=1122952) Then he posted it on the launchpad bug report site where Timo Aaltonen wanted feed back on his patched linuxwacom 0.8.2-2 packages. We have a HOW TO on how to use the script on post #104 here: [http://ubuntuforums.org/showthread.p...038949&page=11](http://ubuntuforums.org/showthread.p...038949&page=11) If you aren't having any problems with your tablet other than xsetwacom then I don't think you need to compile the 0.8.3-2 wacom.ko kernel driver. I'm guessing that since Timo posted the modified xorg ppa 2 days after rec posted his script it fixes things in xorg.xserver. At least that's my guess as to what "* Add 176_remove_device_from_inputinfo.devices.diff." means. Maybe Solar George could comment.
Yes thats what I was trying to point to - I was in a bit of a hurry as I was about to reboot to install jaunty to my spare partition so I failed to explain myself (or it appears find the exact link).

---

### Post by ProhetOfDoom on 2009-04-25
I really value your help here but I've actually got a far simpler fix to get xsetwacom working that doesn't require anything complicated at all with no aditional software updates. This was recommended from the linuxwacom forum:

Basically instead of using 'pad', 'stylus' etc in the xsetwacom command you use the device name instead which you can find by running:
 xinput --list

at the command line. Look for things like:

"Wacom Intuos3 6x8 pad"
"Wacom Intuos3 6x8 eraser"
"Wacom Intuos3 6x8"  <- seems to be stylus

(obviously I've got an intuos3)

and insert these in the xsetwacom commands like so:
xsetwacom set "Wacom Intuos3 6x8 pad" Button5 "core key n"
xsetwacom set "Wacom Intuos3 6x8" "PressCurve" 25 0 100 75


And that's it - works a treat

---

### Post by Favux on 2009-04-25
Hi ProhetOfDoom, 	

That looks interesting.  It must have been posted recently.  And everything is working for you doing this?

---

### Post by ProhetOfDoom on 2009-04-25
Well - it looks good so far. Using this method I have been able to change the pressure curve, map the tablet to just one of my two monitors and assign all of the pad buttons and touchstrips to emulate Gimp keyboard shortcuts.

I'm happy :) 

(If I hit any issues I will of course post back here)

---

### Post by Newfoundlander on 2009-04-25
My Wacom tablet worked great with Ubuntu 8.10.  Now after upgrading to 9.04, it does not work at all!

---

### Post by ProphetOfDoom on 2009-04-25
In what way? Mine didn't work either - initially it behaved like a mouse. But I went to the synaptic package manager, reinstalled the hal packages, rebooted and it all started working just fine.

---

### Post by benmoran on 2009-04-25
I just picked up a Bamboo the other day. It half-worked in Intrepid, but the eraser didn't function. I tried modifying xorg with no luck, so I went ahead and did a fresh Jaunty install (which I planned on doing anyway). 

With Jaunty, it works perfect. I havn't configured the buttons yet, but its just plug in and go. A few second to configure Gimp is all I needed.

---

### Post by Newfoundlander on 2009-04-26
> **ProphetOfDoom said:**
> In what way? Mine didn't work either - initially it behaved like a mouse.

Well, it's a Graphite CTE-430 and in Ubuntu 8.10 everything worked except for the eraser.

Now in 9.04 I get no cursor movement with either the mouse or stylus.  When I click mouse or stylus buttons, the light on the tablet does change from yellow to green.

I'll try downloading a driver from [http://linuxwacom.sourceforge.net/index.php/dl](http://linuxwacom.sourceforge.net/index.php/dl) and see if that works.

Update: I followed cywhale's instructions at [http://ubuntuforums.org/showthread.php?t=1122952](http://ubuntuforums.org/showthread.php?t=1122952) and now it is working again! Thanks, everyone. :)

---

### Post by mallow on 2009-04-27
> **ProhetOfDoom said:**
> I really value your help here but I've actually got a far simpler fix to get xsetwacom working that doesn't require anything complicated at all with no aditional software updates. This was recommended from the linuxwacom forum:

Basically instead of using 'pad', 'stylus' etc in the xsetwacom command you use the device name instead which you can find by running:
 xinput --list

at the command line. Look for things like:

"Wacom Intuos3 6x8 pad"
"Wacom Intuos3 6x8 eraser"
"Wacom Intuos3 6x8"  <- seems to be stylus

(obviously I've got an intuos3)

and insert these in the xsetwacom commands like so:
xsetwacom set "Wacom Intuos3 6x8 pad" Button5 "core key n"
xsetwacom set "Wacom Intuos3 6x8" "PressCurve" 25 0 100 75


And that's it - works a treat

Thank you so much! After upgrading ro jaunty my Intuos` express keys stopped working, but now it`s all OK thanks to you. Cheers!

---

### Post by dogooder on 2009-04-28
> **ProhetOfDoom said:**
> I really value your help here but I've actually got a far simpler fix to get xsetwacom working that doesn't require anything complicated at all with no aditional software updates. This was recommended from the linuxwacom forum:

Basically instead of using 'pad', 'stylus' etc in the xsetwacom command you use the device name instead which you can find by running:
 xinput --list

at the command line. Look for things like:

"Wacom Intuos3 6x8 pad"
"Wacom Intuos3 6x8 eraser"
"Wacom Intuos3 6x8"  <- seems to be stylus

(obviously I've got an intuos3)

and insert these in the xsetwacom commands like so:
xsetwacom set "Wacom Intuos3 6x8 pad" Button5 "core key n"
xsetwacom set "Wacom Intuos3 6x8" "PressCurve" 25 0 100 75


And that's it - works a treat

Works perfectly, thanks.

---

### Post by K0h4n on 2009-06-08
> **ProhetOfDoom said:**
> I really value your help here but I've actually got a far simpler fix to get xsetwacom working that doesn't require anything complicated at all with no aditional software updates. This was recommended from the linuxwacom forum:

Basically instead of using 'pad', 'stylus' etc in the xsetwacom command you use the device name instead which you can find by running:
 xinput --list

at the command line. Look for things like:

"Wacom Intuos3 6x8 pad"
"Wacom Intuos3 6x8 eraser"
"Wacom Intuos3 6x8"  <- seems to be stylus

(obviously I've got an intuos3)

and insert these in the xsetwacom commands like so:
xsetwacom set "Wacom Intuos3 6x8 pad" Button5 "core key n"
xsetwacom set "Wacom Intuos3 6x8" "PressCurve" 25 0 100 75


And that's it - works a treat

Works like a charm... ;)
Thank you...

---

### Post by SaintDanBert on 2010-04-07
> **ProhetOfDoom said:**
> 
...

Basically instead of using 'pad', 'stylus' etc in the xsetwacom command you use the device name instead which you can find by running:
 xinput --list

at the command line. Look for things like:

"Wacom Intuos3 6x8 pad"
"Wacom Intuos3 6x8 eraser"
"Wacom Intuos3 6x8"  <- seems to be stylus

(obviously I've got an intuos3)

and insert these in the xsetwacom commands like so:
```

xsetwacom set "Wacom Intuos3 6x8 pad" Button5 "core key n"
xsetwacom set "Wacom Intuos3 6x8" "PressCurve" 25 0 100 75

```

And that's it - works a treat

I get the following from **xinput --list**
```

"Wacom Serial Tablet PC Pen Tablet/Digitizer"   id=4    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
        Num_buttons is 32
        Num_axes is 6
        Mode is Absolute
        Motion_buffer is 256
...
"Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"    id=5    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
        Num_buttons is 32
        Num_axes is 6
        Mode is Absolute
        Motion_buffer is 256
...
"ThinkPad Extra Buttons"        id=3    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
...

```

So do I use the huge string "Wacom ... /Digitizer" or "Wacom ... /Digitizer eraser" for my xsetwacom command?

What are all of the various things I need to **xsetwacom set** so that wacom-tools will work?

Sorry if I'm thick as a stump here,
~~~ 0;-Dan

---


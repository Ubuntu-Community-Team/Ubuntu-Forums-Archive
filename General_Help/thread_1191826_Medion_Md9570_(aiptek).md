---
title: "Medion Md9570 (aiptek)"
date: 2009-06-19
forum: General Help
---

### Post by sheffield on 2009-06-19
hi all
I dont know if this is the right place to post this query, so sorry if I have got it wrong!

I Have an Medion 9570 tablet (because I hate mice when using gimp).  I have managed to install the Aiptek package from synaptic and read through the aiptek thread on this forum, but it still makes no sense to me (being a new linux user).

Can anyone help?

PS The pen moves the cursor on screen but none of the buttons on the pen works.

---

### Post by DeMus on 2009-06-19
> **sheffield said:**
> hi all
I dont know if this is the right place to post this query, so sorry if I have got it wrong!

I Have an Medion 9570 tablet (because I hate mice when using gimp).  I have managed to install the Aiptek package from synaptic and read through the aiptek thread on this forum, but it still makes no sense to me (being a new linux user).

Can anyone help?

PS The pen moves the cursor on screen but none of the buttons on the pen works.

Can you find a program to make settings for these buttons? Maybe in menu Applications, maybe under System.
I can imagine there is something like that to allow you to make your own settings.

---

### Post by sheffield on 2009-06-21
> **DeMus said:**
> Can you find a program to make settings for these buttons? Maybe in menu Applications, maybe under System.
I can imagine there is something like that to allow you to make your own settings.

HI All I have managed to get it working in 9.04 and it works great in inkscape but all i get to do in GImp is draw a limited straight line

Anyone got any ideas?

---

### Post by Favux on 2009-06-21
Hi sheffield,

Did you follow 9.1 for Gimp here?:  [http://ubuntuforums.org/showthread.php?t=122735&highlight=tablet](http://ubuntuforums.org/showthread.php?t=122735&highlight=tablet)  A similar description of enabling the Extended Input Devices is near the bottom here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

How many buttons on the stylus are there?  Which version of Ubuntu are you using?  Jaunty (9.04) or another?  If Jaunty maybe we can add the stylus buttons to the "99-x11-wizardpen.fdi" located in "/etc/hal/fdi/policy/" if you have it.  It is described here:  [http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html](http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html)  And some more stuff about your tablet in Jaunty:  [http://digitalbluewave.blogspot.com/2009/03/wizardpen-ubuntu-904-and-everchanging.html](http://digitalbluewave.blogspot.com/2009/03/wizardpen-ubuntu-904-and-everchanging.html)

Anyway for a Wacom stylus with two buttons you'd add something like:
```
<merge key="input.x11_options.Button2" type="string">2</merge>
<merge key="input.x11_options.Button3" type="string">3</merge>
```
Which would make the first stylus button (Button2 because the stylus tip is Button1) a middle mouse click (2) and the second button (Button3) a right mouse click (3).  That may also work for your aiptek tablet since they're general x11 options.

---

### Post by sheffield on 2009-06-22
> **Favux said:**
> Hi sheffield,

Did you follow 9.1 for Gimp here?:  [http://ubuntuforums.org/showthread.php?t=122735&highlight=tablet](http://ubuntuforums.org/showthread.php?t=122735&highlight=tablet)  A similar description of enabling the Extended Input Devices is near the bottom here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

How many buttons on the stylus are there?  Which version of Ubuntu are you using?  Jaunty (9.04) or another?  If Jaunty maybe we can add the stylus buttons to the "99-x11-wizardpen.fdi" located in "/etc/hal/fdi/policy/" if you have it.  It is described here:  [http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html](http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html)  And some more stuff about your tablet in Jaunty:  [http://digitalbluewave.blogspot.com/2009/03/wizardpen-ubuntu-904-and-everchanging.html](http://digitalbluewave.blogspot.com/2009/03/wizardpen-ubuntu-904-and-everchanging.html)

Anyway for a Wacom stylus with two buttons you'd add something like:
```
<merge key="input.x11_options.Button2" type="string">2</merge>
<merge key="input.x11_options.Button3" type="string">3</merge>
```
Which would make the first stylus button (Button2 because the stylus tip is Button1) a middle mouse click (2) and the second button (Button3) a right mouse click (3).  That may also work for your aiptek tablet since they're general x11 options.

HI I am using Jaunty, and everything seems ok on the surface, but I get no Pen option in Gimp.

There are 2 buttons on the pen and I think an eraser on the end of it, it is a badged MEDION 9570 oversize pad.

I have followed some of the threads and read as much as I can, but it all seems a little lost on me, I have created an FDI file in policy but when I come to edit it in gedit, all my changes seems to be lost.

Any help would be gratefully accepeted.  You will have to excuse my stupidity, but only changed to linux last year and due to illness not had a chance to really get under the hood so to speak.

John

---

### Post by Favux on 2009-06-22
Hi sheffield,

OK you are using Ubuntu Jaunty (9.04).  Your Medion Md9570 now works after installing the Aiptek input driver xserver-xorg-input-aiptek 1.1.1 with Synaptic Package Manager.

You have a stylus with 2 buttons.  An eraser is like a button on the back end of the stylus.  When you depress it it should slide into the stylus barrel.

When you say you created a .fdi in "/etc/hal/fdi/policy/" do you mean the Aiptek package from Synaptic installed it?  Could you post what's in it.  And it's name.

In Gimp what options are you seeing?  How is it different from what you saw in Inkscape?

---

### Post by sheffield on 2009-06-22
> **Favux said:**
> Hi sheffield,

OK you are using Ubuntu Jaunty (9.04).  Your Medion Md9570 now works after installing the Aiptek input driver xserver-xorg-input-aiptek 1.1.1 with Synaptic Package Manager.

You have a stylus with 2 buttons.  An eraser is like a button on the back end of the stylus.  When you depress it it should slide into the stylus barrel.

When you say you created a .fdi in "/etc/hal/fdi/policy/" do you mean the Aiptek package from Synaptic installed it?  Could you post what's in it.  And it's name.

In Gimp what options are you seeing?  How is it different from what you saw in Inkscape?


Right I installed the Aiptek through synaptics, so that seems ok on the surface.
after reading the threads, I created a file called 10-aiptek.fdi in /etc/hal/fdi/policy

but when i come to edit I cant save the file back the command I use is

sudo gedit 10-aiptek.fdi /etc/hal/fdi/policy

not sure if this is right.

In GIMP in the extended input devices all, I see is Microsoft mouse options and thats all.

So I dont know where I am going wrong

MTIA

---

### Post by Favux on 2009-06-22
Hi sheffield,

Got you.  The command should be:
```
gksudo gedit /etc/hal/fdi/policy/10-aiptek.fdi
```

I'm not sure "/etc/hal/fdi/policy/" is the right place but it should work.  And since they are saying it works, OK.

What I'd like to see is the contents of "10-aiptek.fdi" or a link that takes me to it.  Also have you run across any links describing setting up your stylus buttons or eraser?

Regarding Gimp let's see what names HAL is returning.  Let's look at the output of:
```
xinput --list
```
in a terminal.

---

### Post by sheffield on 2009-06-23
The output from XINPUT --LIST is as follows

"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Aiptek"	id=2	[XExtensionPointer]
	Num_buttons is 6
	Num_axes is 3
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 1440
		Resolution is 1000
	Axis 1 :
		Min_value is 0
		Max_value is 900
		Resolution is 1000
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1000
"Macintosh mouse button emulation"	id=3	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"AT Translated Set 2 keyboard"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Microsoft Microsoft USB Wireless Mouse"	id=5	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1


The contents of the fdi is 

<?xml version="1.0" encoding="UTF-8"?> 
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
      <merge key="input.x11_options.USB" type="string">On</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
      <merge key="input.x11_options.zMin" type="string">0</merge>
      <merge key="input.x11_options.zMax" type="string">1023</merge>
    </match>
  </device>
</deviceinfo>


Thanks for all your help and advice.

John

---

### Post by sheffield on 2009-06-23
Right after a fashion I have managed to get Jaunty to recognise pressure but it only draws in a straight line up and down.  The buttons do not work, so I am wondering whether it could be a conflict with the mouse and its still not appearing in the GIMP

John

---

### Post by Favux on 2009-06-23
Hi John,

Well HAL is calling your stylus:

stylus = "Aiptek"

from the "xinput --list" line:

"Aiptek" id=2 [XExtensionPointer]

Is anything like that showing up in Extended Input Devices in Gimp?  If so in Edit -> Preferences -> Input Devices -> Configure Extended Input Devices change it from "Disabled" to "Screen".

Hopefully this 10-aiptek.fdi will give you buttons.  Replace the current one (after backing it up) at "/etc/hal/fdi/policy/10-aiptek.fdi" with this one:
```
<?xml version="1.0" encoding="UTF-8"?>

    <!-- Medion Md9570 (aiptek) -->
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
      <merge key="input.x11_options.USB" type="string">On</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
        <merge key="input.x11_options.Button2" type="string">2</merge>
        <merge key="input.x11_options.Button3" type="string">3</merge>
        <merge key="input.x11_options.zMin" type="string">0</merge>
        <merge key="input.x11_options.zMax" type="string">1023</merge>
    </match>
  </device>
</deviceinfo>
```

I don't know why it is moving only in a vertical line.  Wacom stuff in "xinput --list" shows up as [XExtensionKeyboard] rather than [XExtensionPointer].  I don't know what that means.  Maybe you're right and there is some conflict with the mouse.

It also could be a calibration issue.  Have you seen any posts with coordinates for Aiptek?  For the Wizardpen I've seen:
```
<merge key="input.x11_options.TopX" type="string">5619</merge>
<merge key="input.x11_options.TopY" type="string">6554</merge>
<merge key="input.x11_options.BottomX" type="string">29405</merge>
<merge key="input.x11_options.BottomY" type="string">29671</merge>
<merge key="input.x11_options.MaxX" type="string">29405</merge>
<merge key="input.x11_options.MaxY" type="string">29671</merge>
```

---

### Post by Favux on 2009-06-23
Hi John,

With the caveat that I'm not quite sure what I'm doing I took another look at your "xinput --list" Aiptek output.  Given what you've done for pressure I wonder if your coordinates would be something like:
```
<merge key="input.x11_options.TopX" type="string">0</merge>
<merge key="input.x11_options.TopY" type="string">0</merge>
<merge key="input.x11_options.BottomX" type="string">1440</merge>
<merge key="input.x11_options.BottomY" type="string">900</merge>
```
Which might mean the .fdi should look like this:
```
<?xml version="1.0" encoding="UTF-8"?>

    <!-- Medion Md9570 (aiptek) -->
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
      <merge key="input.x11_options.USB" type="string">On</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
        <merge key="input.x11_options.Button2" type="string">2</merge>
        <merge key="input.x11_options.Button3" type="string">3</merge>
        <merge key="input.x11_options.zMin" type="string">0</merge>
        <merge key="input.x11_options.zMax" type="string">1023</merge>
        <merge key="input.x11_options.TopX" type="string">0</merge>
        <merge key="input.x11_options.TopY" type="string">0</merge>
        <merge key="input.x11_options.BottomX" type="string">1440</merge>
        <merge key="input.x11_options.BottomY" type="string">900</merge>
    </match>
  </device>
</deviceinfo>
```
Again no guarentees and be sure to back up your current .fdi if you want to try it.

---

### Post by sheffield on 2009-06-23
HI Favux
I am going to try this tomorrow, otherwise it will have to wait till next week as the wife is dragging me off to the lake district, shes going to a knitting convention I am going to take some landscapes.

But much appreciation and many thanks for all your hardwork and patience

John

---

### Post by sheffield on 2009-06-28
Favux
thanks for all your hard work, and expertise, I am trying this tomorrow after a few days away.

John

---

### Post by sheffield on 2009-06-29
hi tried the newly put together fdi, but nothing all i get when i put pen to tablet is it hides itself on the right hand side of the screen.


Gimp sees it as Aiptek, so thats ok, we know the HAL sees it, so I am not sure, will do some further digging

john

---

### Post by Favux on 2009-06-29
Hi sheffield,

Disappointing but not too surprising.  When the pointer runs off to a corner it usually means Xinput isn't getting any input.  So remove the coordinate entries to the .fdi.  They must have broken something.

You might want to see if there is a newer aiptek driver you can install.  As near as I can figure out HAL is treating your tablet as a mouse.

---

### Post by sheffield on 2009-06-29
Hi Favux
the names john, ok I will try that in the morning, how could I remap the input from the mouse? I assume it would be fairly simple to do, will look it up and let you know the outcome

Thnaks again

---

### Post by Favux on 2009-06-29
Hi John,

I don't know, I've never tried it before.
> You can check the XInput pointer status by using xsetpointer as below. The man page states that calling xsetpointer with the name of a particular device will set it as the primary pointing device. 
```
xsetpointer -l
```
So I think you are just picking which mouse is the primary pointing device.

When I use "xsetpointer -l" I get the following output:
```
0: "Virtual core keyboard"	[XKeyboard]
1: "Virtual core pointer"	[XPointer]
2: "stylus"	[XExtensionKeyboard]
3: "eraser"	[XExtensionKeyboard]
4: "touch"	[XExtensionKeyboard]
5: "Macintosh mouse button emulation"	[XExtensionPointer]
6: "SynPS/2 Synaptics TouchPad"	[XExtensionPointer]
7: "AT Translated Set 2 keyboard"	[XExtensionKeyboard]
8: "Video Bus"	[XExtensionKeyboard]

```
It looks like your trackpad is:
```
"Macintosh mouse button emulation" id=3 [XExtensionPointer]
```
and your usb wireless mouse:
```
"Microsoft Microsoft USB Wireless Mouse" id=5 [XExtensionPointer]
```
Since the tablet is also showing up as a "[XExtensionPointer]":
```
"Aiptek" id=2 [XExtensionPointer]
```
Could one of them be interfering?  Maybe try unplugging the usb wireless mouse and reboot and see if that changes things?

---

### Post by sheffield on 2009-07-09
hi Favux 
when I do a xsetpointer -l I get the following output

0: "Virtual core pointer"	[XPointer]
1: "Virtual core keyboard"	[XKeyboard]
2: "Aiptek"	[XExtensionPointer]
3: "Macintosh mouse button emulation"	[XExtensionPointer]
4: "AT Translated Set 2 keyboard"	[XExtensionKeyboard]
5: "Microsoft Microsoft USB Wireless Mouse"	[XExtensionPointer]


so obviously 2 is the aiptek, and it seems to be colliding with the mouse on some level

Many thanks

JOhn

---

### Post by sheffield on 2009-07-09
I have replaced the usb mouse with the keyboard, and what I get now is 

xsetpointer -l

0: "Virtual core pointer"	[XPointer]
1: "Virtual core keyboard"	[XKeyboard]
2: "ImPS/2 Logitech Wheel Mouse"	[XExtensionPointer]
3: "Aiptek"	[XExtensionPointer]
4: "Macintosh mouse button emulation"	[XExtensionPointer]
5: "AT Translated Set 2 keyboard"	[XExtensionKeyboard]


so obviously i am going wrong somwhere, but I am not so sure where, have altered the fdi so now it looks like this 

<?xml version="1.0" encoding="UTF-8"?>

    <!-- Medion Md9570 (aiptek) -->
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
      <merge key="input.x11_options.USB" type="string">On</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
        <merge key="input.x11_options.Button2" type="string">2</merge>
        <merge key="input.x11_options.Button3" type="string">3</merge>
        <merge key="input.x11_options.zMin" type="string">0</merge>
        <merge key="input.x11_options.zMax" type="string">1023</merge>
    </match>
  </device>
</deviceinfo>


I think the line 

<merge key ="input.X11_options.USB" type ="string">ON</merge>

will need to come out as its running the the ps/2 port

---

### Post by Favux on 2009-07-09
Hi John,

Well try it, but I think usb on is necessary for the usb tablet to send info.  But experiment.  Either we're looking at a driver problem or a .fdi problem.  And the .fdi is easier to play with.  What I've done is reorder things as to how they would/should be in an xorg.conf.  Let's see if that makes a difference.
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

    <!-- Aiptek:  Medion Md9570; -->
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="info.product" type="string">stylus</merge>
      <merge key="input.x11_options.USB" type="string">on</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
        <merge key="input.x11_options.Button2" type="string">2</merge>
        <merge key="input.x11_options.Button3" type="string">3</merge>
        <merge key="input.x11_options.zMin" type="string">0</merge>
        <merge key="input.x11_options.zMax" type="string">1023</merge>
    </match>
  </device>
</deviceinfo>
```
And I added the line:
```
      <merge key="info.product" type="string">stylus</merge>
```
Hopefully that line won't break anything and adds something.  If it's a problem remove it.  So just play with the .fdi.  Any difference with or without the Button lines?  Like that.  If you see a working xorg.conf for your tablet on an earlier version of Ubuntu let's look at that.

One other thing we could do would be to look at the lshal output.  That's "traditionally" how you construct a .fdi.  But it's huge so you want it in text form so in gedit you can use find to search for aiptek, etc.  It is a pain to comb through, but doable.  The idea is to see if we can find some match lines that just specify the tablet so that there isn't an overlap with the "mouse" or whatever.  Probably want one without the aiptek .fdi and one with, so:
```
lshal > sheffield_before_lshal.txt
```
and
```
lshal > sheffield_after_lshal.tst
```

Failing finding someone with your tablet or a close twin who posted a success story that's what we've got.  Maybe some more research on the driver is in order.

---

### Post by Jan Alleman on 2009-07-11
Favux, I have an MD9570 as well and have pressure levels working, so I think sheffields problem might be in his Gimp configuration. You need to configure input devices' extended settings (under Edit->Preferences) to get pressure levels working.  There may be a driver issue in the button handling though. I traced the state of the buttons with xinput, and saw that the button states 2 and 3 are not very stable (button1, the pen is).  Regards, Marc

---

### Post by Favux on 2009-07-11
Hi Marc,

Welcome to Ubuntu!

Great!  I really appreciate you pitching in.

I hope you're saying that the .fdi above worked for you.  Which would be great.  That's the reason I added the extra line, I was hoping it would get the stylus to identify itself as "stylus" rather than "Aiptek" in Gimp (and xinput --list) in case that made a difference with Gimp recognizing it.

Some drivers I've seen required something like Buttons=2, or whatever, to help define the buttons.  I guess in a .fdi it would look something like:
```
<merge key="input.x11_options.Buttons" type="string">2</merge>
```
I'm not sure of the syntax, but I hope that's close.  And it would probably go between the Mode and SendCoreEvents lines.  We could see if that "stabilizes" the buttons.

Now to get really speculative.  Are there some buttons on the tablet itself?  I haven't seen anything that indicates the driver has a "pad" section like the linuxwacom drivers.  But since the "xinput --list" said the "Num_buttons is 6" if there are up to 4 buttons on the tablet, we may be able to change the above line (assuming it worked) from 2 to up to 6 and add the additional buttons as Button4 etc.

---

### Post by sheffield on 2009-07-11
HI Everyone
firstly can I say thank you for your fine help.

right the fdi seems to work ok, so no major problem there, I have pressure but no button, so thats no great loss.

The main issue at present is that all it will do is draw in a constricted horizontal line about a 1/3rd of the way up the image.

Am looking at lshal


MAny thanks

---

### Post by Jan Alleman on 2009-07-11
Favux, the extra line is not required; it just changes the device name to be chosen in a program like gimp (without it, 'Aiptek', with the line included 'stylus').
For completness' sake, here my fdi:

```

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
      <merge key="input.x11_options.USB" type="string">On</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
      <merge key="input.x11_options.Button2" type="string">2</merge>
      <merge key="input.x11_options.Button3" type="string">3</merge>
      <merge key="input.x11_options.ZMin" type="string">0</merge>
      <merge key="input.x11_options.ZMax" type="string">511</merge>
      <merge key="input.x11_options.ZThreshold" type="string">5</merge>
      <merge key="input.x11_options.Pressure" type="string">linear</merge>
    </match>
  </device>
</deviceinfo>

```Undoubtedly, there's more in it then necessary; I just filled in everything I found on the 'aiptek' man page (man aiptek).

The tablet itself does not have hardware buttons; it has 24 areas on top that can be bound to applications in windows.
The buttons on the pen seem to be recognized in some fashion. The second button f.i. gets state 'true', if  only button 1 is not pressed (the pen doesn't touch the pad); button 3 gets state true when pressed, but remains true unless button 1 gets pressed.

I don't seem to have the problem of drawing straight lines as sheffield does.
I forgot: I work in Jaunty. O, and when I unplug the panel, X restarts. Is this a feature ;-)?

For those working in vista: the driver that came with the tablet is said to not work (even without driver, the pen draws; probably no pressure levels). On the net, references can be found to the Aiptek hyperpen 6000 driver ([http://www.bleepingcomputer.com/forums/topic111466.html](http://www.bleepingcomputer.com/forums/topic111466.html)). This is actually incorrect; the tablet is clearly a rebranded 12000U, but the driver is the same. It did not work out for me: the pen stops drawing completely, although configuration for a tablet pc recognised the pen and let it calibrate.
I found a 3.10 version of the driver however that works perfectly (and as a bonus, you get a control panel where you can actually adjust things).
One more pecularity: in gimp on windows, configuration of the input devices is unnecessary and even impossible: there are only options 1 and 2 for the axis; everything works though.
On linux, the z-axis in gimp must be bound to 4.

---

### Post by Favux on 2009-07-11
Hi John,

What I'd suggest you try is go into Synaptic Package Manager and tell it to do a total uninstall of the Aiptek driver.  Reboot.  Go back to Synaptic and tell it to install the Aiptek driver.  Reboot.  From what Marc's saying the driver should work.  At least I think he's saying he's using the default repository driver.

And then look again near the bottom here for setting up in Gimp:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)  And notice what Marc says on the bottom of his last post.

Hi Marc,

Wow!  Some seriously valuable information.  Thank you.

> I work in Jaunty. O, and when I unplug the panel, X restarts. Is this a feature?
Ha!  Sounds like something is not quite right with the driver.

Since there is no configuration or calibration gui for Aiptek (is there?), putting everything in the .fdi makes sense to me.  Maybe it could be reorganized and cleaned up a tad, but so what.  What is the file name you are using for the .fdi and where are you installing it?

If the line does make the stylus identify as stylus (as you are saying) instead of aiptek, I'd leave it in.  I think some software is hardcoded to require the stylus as stylus, so that gets around that problem.  Cool, it worked!

---

### Post by Jan Alleman on 2009-07-11
You're welcome Favux.

> Ha! Sounds like something is not quite right with the driver.It does neatly so ;-) I wondered whether it was a crash or not, but there is no notice, so probably it is ;-)

> Since there is no configuration or calibration gui for Aiptek (is there?), putting everything in the .fdi makes sense to me. Maybe it could be reorganized and cleaned up a tad, but so what. What is the file name you are using for the .fdi and where are you installing it?It was more a leftover of the experimental phase ;-) The file name is the regular /etc/hal/fdi/policy/10-aiptek.fdi. I use the repository driver indeed.
As I read from your posts, sheffield, is that you're configuration is no different from mine; the basic functionality seems to work. Maybe have a look whether you have not incidently set some margin values in your fdi? As you see, I have not specified value for XTop, Xbottom, YTop and YBottom. Maybe you just hit one of those.

> If the line does make the stylus identify as stylus (as you are saying) instead of aiptek, I'd leave it in. I think some software is hardcoded to require the stylus as stylus, so that gets around that problem. Cool, it worked!Seems reasonable. I saw elsewhere that blender f.i. expects 'stylus'.

Just when you think you're settled, things screw up: as I wanted to be more specific about the button behaviour as I think I was not completely clear, I see new things. The buttons do not work anymore at all, and valuator[2] (the z-axis) starts off at 50. I will experiment a little more and tell the results later.
I even had a straight line once as I understand sheffield has, but I think that I touched the touchpad of my laptop at the same time that I was drawing.

A hint for sheffield: the behaviour of gimp f.i. gets a lot clearer if you start tracing the xinput query-state <device> in a terminal window first. I do it in a loop:

while true
do
  xinput query-state Aiptek
done

If this hogs your machine too much, you could add a 'sleep 1' within the loop, but probably you want to track fast. Replace the 'Aiptek' with the device string you're using.
If you use the terminal window as your 'drawing app', draw imaginary lines and watch the valuator[0] and valuator[1] values, you may see what happens under the hood.

---

### Post by Favux on 2009-07-11
Hi Marc,

Blender is exactly what I was thinking of.  FYI wacomcpl also, but not relevant.  Must be others.

More good info., thanks yet again.  It would be sweet to get the stylus buttons working.  I guess you could look at "man xorg.conf" since that should mostly still apply in HAL/.fdi.  And here is the 5.1 HAL spec.:  [http://people.freedesktop.org/~david/hal-spec/hal-spec.html](http://people.freedesktop.org/~david/hal-spec/hal-spec.html)  Hope something in there is useful.

---

### Post by Jan Alleman on 2009-07-11
Well, let me quickly correct myself about the 'bind the z-axis to 4' on linux and change it in 'your mileage may vary, experiment'; after applying the info.product=stylus again (may not be related), I have to use 3.
The pressure level still starts at about 54 to 58. I thought it could be a mechanical defect of the pen, but it also happens without battery in the pen. The buttons still do not work anymore.
That's the bad news, but maybe there is some good news as well. When I press button 2, nothing happens to the button states, but proximity goes from In to Out, and it seems stable. So maybe this can be used to detect button 2 presses.

Experimented some more: replaced the battery (was using a rechargeable one); now the default z-axis value drops to 42 and the button behaviour is back! Tried some other rechargeable batteries at different amounts of charge; believe it or not; we can use this device to test the charge of the batteries! The lower the charge, the higher the default z-axis value. One thing is common for all rechargeable batteries I tried: no buttons.

---

### Post by Favux on 2009-07-11
That's just weird.

---

### Post by Jan Alleman on 2009-07-11
Ok, on to the buttons with a fresh battery.

button1: down when the pen touches the tablet; up when it does not. If button1 is down and you press button2 or 3, the state becomes up.

button2: goes to down if button1 is up and button2 is pressed. If button1 is down and button2 is pressed, things are unpredictable. Sometimes button2 goes down, sometimes button3. Button1 does not seem to be affected (as I told earlier, so better forget that)

button3: goes to down as long as button1 is not down. When button1 is down, button3 does not react.
button3 sometimes stays down after having been pressed unless button1 goes down, but not always.

Looks like this battery is not 100% as well... Too late to go out and buy a new one ;-)

Forget about the proximity changing at button presses as well; this only seems to work with the rechargeable battery.

---

### Post by Favux on 2009-07-11
Hi Marc,

In wacomcpl you're offered two options for the stylus button(s).  One is an event when the stylus tip (Button1) is in contact with the screen.  The other is hover mode where the stylus button is recognized without the stylus tip touching the screen,  as long as the proximity is close enough.  There's also a bunch of settings like:  ClickForce, Threshold, Suppress, CursorProx.  I have no idea which are driver specific and which might be "general" xorg settings.  Does man aiptek provide any guidance?

Edit:  A thought occurs.  Would adding to the .fdi before the Button2 line Button1 as 1 (stylus tip as left click) stabilize things?  Maybe the Aiptek driver doesn't set that as the default when the other buttons are invoked?

---

### Post by Jan Alleman on 2009-07-11
> **Favux said:**
> Hi Marc,

In wacomcpl you're offered two options for the stylus button(s).  One is an event when the stylus tip (Button1) is in contact with the screen.  The other is hover mode where the stylus button is recognized without the stylus tip touching the screen,  as long as the proximity is close enough.  There's also a bunch of settings like:  ClickForce, Threshold, Suppress, CursorProx.  I have no idea which are driver specific and which might be "general" xorg settings.  Does man aiptek provide any guidance?

No, man aiptek does not have anything about buttons, neither does man xorg.conf. I wonder where the settings you mention come from. I'll try the button1 setting.
Btw: I edited a prior post as a hint for sheffield came to mind; couldn't it be that his x- and y- values hit a specified clipping area?

---

### Post by Jan Alleman on 2009-07-11
Nope, no change.

---

### Post by Jan Alleman on 2009-07-11
This may be of interest also; I had not noticed yet, but my xinput --list is a little different from the other one (as a result of fiddling with the .fdi?)

```

"stylus"    id=3    [XExtensionPointer]
    Num_keys is 32
    Min_keycode is 8
    Max_keycode is 39
    Num_buttons is 5
    Num_axes is 5
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 5999
        Resolution is 14763
    Axis 1 :
        Min_value is 0
        Max_value is 4499
        Resolution is 14763
    Axis 2 :
        Min_value is 0
        Max_value is 511
        Resolution is 512
    Axis 3 :
        Min_value is -128
        Max_value is 127
        Resolution is 256
    Axis 4 :
        Min_value is -128
        Max_value is 127
        Resolution is 256

```The corresponding valuators 3 and 4 remain zero though.
Just in case, lsusb gives ID 08ca:0010 Aiptek International, Inc. Tablet

---

### Post by Favux on 2009-07-11
Hi Marc,

The clipping sounds possible.  Yes the .fdi will change things.  I'll have to look at it later.

The settings come from the LWP's HOWTO here:  [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)  And section 9.0.

Another thought even less likely.  Could the button mapping have changed, either due to Xserver 1.6 or Aiptek?  Might Button2 be Button1, etc.

Edit:  I guess I figure some of the LWP settings might apply because after all they're all interfacing with the same Xinput/Xserver.  At some point they have to share some code (api's?) from Xorg or each other.

---

### Post by Favux on 2009-07-12
Hi John and Marc,

John hopefully the driver reinstall helped.  If not I may have spotted something.  Marc's zMax is set at 511.

So here is the current 10-aiptek.fdi (in "/etc/hal/fdi/policy/") as I understand it:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

    <!-- Aiptek:  Medion Md9570; -->
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="info.product" type="string">stylus</merge>
      <merge key="input.x11_options.USB" type="string">on</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
      <merge key="input.xorg.options.Buttons" type="string">2</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
        <merge key="input.x11_options.Button1" type="string">1</merge>
        <merge key="input.x11_options.Button2" type="string">2</merge>
        <merge key="input.x11_options.Button3" type="string">3</merge>
        <merge key="input.x11_options.zMin" type="string">0</merge>
        <merge key="input.x11_options.zMax" type="string">511</merge>
        <merge key="input.x11_options.ZThreshold" type="string">5</merge>
        <merge key="input.x11_options.Pressure" type="string">linear</merge>
    </match>
  </device>
</deviceinfo>
```
I don't know if Marc's other two lines at the bottom will make a difference or not.  If it starts working after changing zMax to 511 my bet would be on the zMax.  ;)

Although the buttons aren't "working" right now I like them like that for now because that's the way they appear in a default wacomcpl .xinitrc.  Marc did you try the Buttons = 2 (or 3?) line?

As an exercise in history I thought I'd show you what the folks using the finepoint driver had to do with Xserver 1.4 (?).
> Hints if you are having problems (Thanks to Aron Hsiao):

Problem 1:  Side switch being reported as wild button numbers
	   (like 249 instead of 3): 

Solution:  Add the following to your xinitrc: 

	xsetpointer TOUCHSCREEN
	xmodmap -e 'pointer = 1 2 3'

This should be re-stating the defaults, but Aron Hsiao agrees that it appears
to be an XFree86 4.x bug. 
The xinitrc they are talking about is in "/etc/X11/xinit/".

---

### Post by Jan Alleman on 2009-07-12
> **Favux said:**
> 
Marc's zMax is set at 511.


The tablet has 512 pressure levels, so that must be correct.

> 
I don't know if Marc's other two lines at the bottom will make a difference or not.  If it starts working after changing zMax to 511 my bet would be on the zMax.  ;)
I guess not. My pressure level starts way above 5, so if it is to be used it would have to be larger than this. But I have the impression that button1 and/or proximity are already used to detect a minimal pressure. The 'linear' is default;you have a choice between that, 'hard' and 'soft' which is like exponential and reverse exponential respectively.
But I understand that pressure is not sheffields problem.

> 
Although the buttons aren't "working" right now I like them like that for now because that's the way they appear in a default wacomcpl .xinitrc.  Marc did you try the Buttons = 2 (or 3?) line?
It looks like adding
```

<merge key="input.xorg.options.Buttons" type="string">2</merge>

```improves the stability of button2. It is a bit hard to say, as pressing the buttons pop up menus, create empty directories and such ;-) and the two buttons are physically tied together (I don't know the word in English for it, but they work like a light swich) and so close, but I think I'll leave this one in.
For button3: it seems to work ok, only you have to lift the pen from the tablet (but stay within proximity), which may be normal behaviour if it is to act as a right mouse button. For me, it was always difficult to work with the buttons, also on windows (so definitely not a big issue, but a nice to have all features working).

The xinit setting looks like an ugly thing; wouldn't that interfere with mouse and touchpad?

---

### Post by Favux on 2009-07-12
Hi Marc,

Ok, I'll add the line.  We could try some of the fancy stuff from LWP HOWTO's Section 9 re xsetwacom commands.  But I suspect that's driver specific stuff and not generic X11 (mouse) stuff.  In other words try to change the first stylus button (Button2) from a middle mouse click to something else.  But...

Great!  I can't believe we achieved pressure and buttons.  Awesome.

Edit:  It may.  Have to proceed carefully.  It's possible to get a "loop" going.  We've learned that with wacomcpl's .xinitrc which calls it.  There's a chain of scripts, which I guess is being deprecated, but is still there.

---

### Post by Jan Alleman on 2009-07-12
I swapped values 2 and 3 for the buttons, but it doesn't change anything. Does that mean something?

(Favux, do you get sleep sometimes? You seem to be here all day ;-) Or we must be in the same timezone (gmt+1)).

A bold question: I tried the 24 top row 'buttons' on the tablet, but they are not recognized. Any idea how to get input of these?
These could be really handy if it were possible to link functions to them.
In this button area, button1 stays up, so apparently, the tablet knows it is not part of the drawing area.

---

### Post by Favux on 2009-07-12
Hi Marc,

That must mean something, because they should swap middle click and right click, so something is wrong.

Keeping weird hours.  Little old doggie is sick.  I indulge her.

Oh, I should have said to avoid the loop see Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

Edit:  I'm pretty sure that row of buttons would require driver specific code.  Someone would have to figure out the packets and add it to Aiptek.  That's why I was hoping there were just a few.

---

### Post by Jan Alleman on 2009-07-12
Poor doggie. My knowledge of English lacks; Ivorian 'Yacko' would fit best.

---

### Post by Jan Alleman on 2009-07-12
Lots of reading to do. The wacom howto led me to xsetpointer -l; I see a strange thing there.
To get the synaptics control panel working, I had to add an InputDevice setting in my xorg.conf; now I understand this should be done by hal, but I'm not into that. As a result, I see the touchpad listed twice in the xsetpointer -l output:

```

0: "Virtual core pointer"    [XPointer]
1: "Virtual core keyboard"    [XKeyboard]
2: "touchpad"    [XExtensionPointer]
3: "stylus"    [XExtensionPointer]
4: "AT Translated Set 2 keyboard"    [XExtensionKeyboard]
5: "Video Bus"    [XExtensionKeyboard]
6: "Macintosh mouse button emulation"    [XExtensionPointer]
7: "PS/2+USB Mouse"    [XExtensionPointer]
8: "SynPS/2 Synaptics TouchPad"    [XExtensionPointer]

```The Identifier of my synaptics InputDevice section is 'touchpad'.
And I have a usb mouse attached.

---

### Post by Favux on 2009-07-12
Hi Marc,

Well the late night "walkies" are done.  Better than the alternative when I sleep through her attempts to wake me.  But now I'm revved up and won't be able to get to sleep for a few minutes.

Right.  All you have to do is comment out the touchpad section and it's line in "ServerLayout" in xorg.conf and HAL/synaptic.fdi will take over in Intrepid and Jaunty.

And [XExtensionPointer] is for a mouse and [XExtensionKeyboard] is how our Wacom digitizers are identified.  That's why I suspect the Aiptek driver is using usb mouse support to work.  Perhaps a "proper" aiptek digitizer driver would identify as [XExtensionKeyboard] also.  So that's why I'm thinking we should concentrate on what Xinput/X11 expects from a mouse input.  But I could be wrong.

By the way your English is excellent.

---

### Post by Jan Alleman on 2009-07-12
Just discovered wacdump. This is a great tool. It shows the button behaviour better. When button2 is pressed, it shows like STYLUS2=DOWN. When I release it, a STYLUS=DOWN gets through though. This may just be a mechanical issue; as I said already, the buttons are not very practical.
What may be nice is, that the packages of the top row buttons are shown as well. It seems to know that there are 24 of them, but they are not interpreted.

It looks like the first byte (lets for clarity say byte0) in the package is just a counter.
byte1: seems to increment slowly in time
byte2: always 59
byte3: always 4A

byte5, 6 and 7 change when I press one of the buttons, but the value changes all the time. Maybe it's coordinate data, but it is really tied to the button; when I press next to a button (but within the top row), the values do not change.

All other bytes are zeroes.

---

### Post by Jan Alleman on 2009-07-12
> **Favux said:**
> 
Right.  All you have to do is comment out the touchpad section and it's line in "ServerLayout" in xorg.conf and HAL/synaptic.fdi will take over in Intrepid and Jaunty.

Well the touchpad works without it, but the control panel does not. I was not totally pleased with the tapping behaviour, so tried the control panel. It seemed to improve things.

---

### Post by Favux on 2009-07-12
Hi Marc,

This isn't very useful.  But because I can't find my link to the "quirk" site I'll link it.  At least it shows some more elaborate .fdi syntax with button mapping:  [http://cgit.freedesktop.org/hal-info/commit/?id=1b40bdf002a95d8cc4b1641776146e62f86c726b](http://cgit.freedesktop.org/hal-info/commit/?id=1b40bdf002a95d8cc4b1641776146e62f86c726b)

---

### Post by Jan Alleman on 2009-07-12
I've got the synaptic thing out of the way by a shmconfig.fdi.

---

### Post by Jan Alleman on 2009-07-12
I think I must conclude that all the button settings in the fdi have no effect. With or without, it works as it does; that is, I can't detect a systematic thing in it.

---

### Post by Favux on 2009-07-12
Hi Marc and John,

Thanks for trying Marc.  I appreciate all of your work.

In summary we don't know how to configure the stylus buttons.  They sort of work, maybe they are hard coded into the Aiptek driver.  The tablet "buttons" don't work, although they send out a signal.

So here is our current 10-aiptek.fdi (in "/etc/hal/fdi/policy/"):
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

    <!-- Aiptek:  Medion Md9570; Trust Wireless Tablet TB-3100 -->
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="info.product" type="string">stylus</merge>
      <merge key="input.x11_options.USB" type="string">on</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
        <merge key="input.x11_options.zMin" type="string">0</merge>
        <merge key="input.x11_options.zMax" type="string">511</merge>
        <merge key="input.x11_options.ZThreshold" type="string">5</merge>
        <merge key="input.x11_options.Pressure" type="string">linear</merge>
    </match>
  </device>
</deviceinfo>
```
This should give you a working stylus with pressure in Gimp etc.  Whether the stylus buttons work or not seems partly dependent on the battery charge.  And also the switches in the buttons may not mechanically be the best according to Marc, which might be partly responsible for confusing the issue somewhat.

---

### Post by Favux on 2009-07-12
Hi Marc,

I looked at the xinput --list output.  I'm not sure what .fdi you were using.  It's interesting that:
```
    Num_keys is 32
    Min_keycode is 8
    Max_keycode is 39
```
appeared.  I'm going to interpret it as meaning that our .fdi is getting closer to "correct" for the Medion tablet.  ;)  Other values changed of course.  That's probably telling us things, if we were smart enough to figure out what.

One thing I noticed is that Resolution is always larger than Max_value.  Except in John's Axis 2 (z?).  There the Max_value was 1023 while the Resolution was 1000.  So John I think this is more evidence that Marc was right and you were getting some "clipping" because you specified too many levels of pressure.  I'm hoping when you use the .fdi (post #50 above) with 511 like we talked about before things will work you.  Fingers crossed.

Edit:  Marc on this link they're kind of trying to do similar things with the n-trig digizer.  It might have some techniques that will interest you.  Maybe start looking at 3. in post #38:  [http://ubuntuforums.org/showthread.php?t=1162477&page=4](http://ubuntuforums.org/showthread.php?t=1162477&page=4)

---

### Post by Favux on 2009-07-13
Hi Marc, and John,

Since the Aiptek tablet is being seen as a "mouse" by Xinput I thought I'd link some stuff about setting up mouse keys/button mapping.  In case it's possible to get around the Aiptek driver.

The Xinput Device configuring wiki:  [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

And a practical application:  [http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

And the HAL version:  [http://people.freedesktop.org/~hughsient/quirk/](http://people.freedesktop.org/~hughsient/quirk/)

And as coCoKNIght points out "this is interesting":  [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)
```
<merge key="input.x11_options.ButtonMapping" type="string">1 2 3 4 5 6 7 8 9</merge>
```

---

### Post by Jan Alleman on 2009-07-14
Ok, thanks, some reading to do.
You've summarized the results so far exact.
For the tablet button output: I noticed that bytes 5, 6 and 7 in the wacdump output also change when just moving the stylus in the drawing area, so that maybe indicates further that it is coordinate data. But it is hard to decipher as such, as making small movements change all bytes, not just the least significant.

---

### Post by Jan Alleman on 2009-07-14
I tried
```
xev | grep -i button
```My finding is that only button 2 is misbehaving and only when it touches the panel. Button three will aparently only work when the pen does not touch the panel (is I noticed earlier already).
More precisely about button 2 touching the panel: sometimes it sends a button1 and a button3 event right after another (not lifting the pen, so I had already received a button1 event), both when the button is pressed and when the button is released. It is either that, a button2 event or nothing at all.

---

### Post by Favux on 2009-07-14
Hi Marc,

I'm getting confused.

From what you are saying:

Button3 (second stylus button) is hard coded into the Aiptek driver in "hover" mode and is set as a (buttonx 2; middle mouse click?)

Button2 (first stylus button) may be hard coded into the Aiptek driver in "stylus tip + button press" mode and is set as a (buttonx 3; right mouse click-when it works)?  Or sometimes it gives off a 2 or middle mouse click?

Could that mean Button2 is suppose to be configurable?  Or just that it's switch is broken?

---

### Post by Jan Alleman on 2009-07-14
I don't think the button is broken, as it works ok when the tip does not touch the panel.
I think xev has more to tell. Take a look at the state:

```
ButtonPress event, serial 32, synthetic NO, window 0x3a00001,
    state 0x0, button 1, same_screen YES
ButtonRelease event, serial 32, synthetic NO, window 0x3a00001,
    state 0x100, button 1, same_screen YES
ButtonPress event, serial 32, synthetic NO, window 0x3a00001,
    state 0x0, button 1, same_screen YES
ButtonRelease event, serial 32, synthetic NO, window 0x3a00001,
    state 0x100, button 1, same_screen YES
ButtonPress event, serial 32, synthetic NO, window 0x3a00001,
    state 0x0, button 1, same_screen YES
ButtonPress event, serial 32, synthetic NO, window 0x3a00001,
    state 0x100, button 2, same_screen YES
ButtonRelease event, serial 32, synthetic NO, window 0x3a00001,
    state 0x300, button 2, same_screen YES
ButtonPress event, serial 32, synthetic NO, window 0x3a00001,
    state 0x100, button 2, same_screen YES
ButtonRelease event, serial 32, synthetic NO, window 0x3a00001,
    state 0x300, button 2, same_screen YES
ButtonPress event, serial 32, synthetic NO, window 0x3a00001,
    state 0x100, button 2, same_screen YES
ButtonRelease event, serial 32, synthetic NO, window 0x3a00001,
    state 0x300, button 1, same_screen YES
ButtonRelease event, serial 32, synthetic NO, window 0x3a00001,
    state 0x200, button 2, same_screen YES
ButtonPress event, serial 32, synthetic NO, window 0x3a00001,
    state 0x0, button 3, same_screen YES
ButtonPress event, serial 32, synthetic NO, window 0x3a00001,
    state 0x400, button 1, same_screen YES
ButtonRelease event, serial 32, synthetic NO, window 0x3a00001,
    state 0x500, button 3, same_screen YES
ButtonPress event, serial 32, synthetic NO, window 0x3a00001,
    state 0x100, button 2, same_screen YES
ButtonRelease event, serial 32, synthetic NO, window 0x3a00001,
    state 0x300, button 2, same_screen YES
ButtonRelease event, serial 32, synthetic NO, window 0x3a00001,
    state 0x100, button 1, same_screen YES
ButtonPress event, serial 32, synthetic NO, window 0x3a00001,
    state 0x0, button 3, same_screen YES
ButtonRelease event, serial 32, synthetic NO, window 0x3a00001,
    state 0x400, button 3, same_screen YES
ButtonPress event, serial 32, synthetic NO, window 0x3a00001,
    state 0x0, button 2, same_screen YES
ButtonRelease event, serial 32, synthetic NO, window 0x3a00001,
    state 0x200, button 2, same_screen YES
ButtonPress event, serial 32, synthetic NO, window 0x3a00001,
    state 0x0, button 2, same_screen YES
ButtonRelease event, serial 32, synthetic NO, window 0x3a00001,
    state 0x200, button 2, same_screen YES
ButtonPress event, serial 32, synthetic NO, window 0x3a00001,
    state 0x0, button 2, same_screen YES
ButtonRelease event, serial 32, synthetic NO, window 0x3a00001,
    state 0x200, button 2, same_screen YES
ButtonPress event, serial 32, synthetic NO, window 0x3a00001,
    state 0x0, button 2, same_screen YES
ButtonRelease event, serial 32, synthetic NO, window 0x3a00001,
    state 0x200, button 2, same_screen YES
ButtonPress event, serial 32, synthetic NO, window 0x3a00001,
    state 0x0, button 2, same_screen YES
ButtonRelease event, serial 32, synthetic NO, window 0x3a00001,
    state 0x200, button 2, same_screen YES
ButtonPress event, serial 32, synthetic NO, window 0x3a00001,
    state 0x0, button 2, same_screen YES
ButtonRelease event, serial 32, synthetic NO, window 0x3a00001,
    state 0x200, button 2, same_screen YES
```Respectively, I did the following: touched the panel; pressed button 2 several times; lifted the tip and pressed button 2 again several times.
You see the 0x400 and 0x500 states? I think I saw 0x700 also.
I guess that's a byte mask. Any idea what the bit values mean?

---

### Post by Favux on 2009-07-14
Hi Marc,

No I don't I don't know what the bit values mean.

Do you know why the ButtonPress event and ButtonRelease event states aren't consistent?

Edit:  For comparison from my wacom stylus:
> Full cycle, Button1 (sylus tip) configured as left mouse click (1), touched to screen and removed

ConfigureNotify event, serial 31, synthetic NO, window 0x4600001,
    event 0x4600001, window 0x4600001, (741,56), width 178, height 178,
    border_width 2, above 0x4407def, override NO

ButtonPress event, serial 31, synthetic NO, window 0x4600001,
    root 0x1a6, subw 0x0, time 89807538, (138,125), root:(881,183),
    state 0x0, button 1, same_screen YES

ConfigureNotify event, serial 31, synthetic YES, window 0x4600001,
    event 0x4600001, window 0x4600001, (741,56), width 178, height 178,
    border_width 2, above 0x13421ca, override NO

ButtonRelease event, serial 31, synthetic NO, window 0x4600001,
    root 0x1a6, subw 0x0, time 89807862, (136,125), root:(879,183),
    state 0x100, button 1, same_screen YES


Full cycle, Button2 (sylus button) configured as right mouse click (3), pressed and released with stylus tip on screen

ButtonPress event, serial 34, synthetic NO, window 0x4600001,
    root 0x1a6, subw 0x4600002, time 89184998, (45,36), root:(788,654),
    state 0x0, button 3, same_screen YES

EnterNotify event, serial 34, synthetic NO, window 0x4600001,
    root 0x1a6, subw 0x0, time 89184998, (45,36), root:(788,654),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 1024

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ConfigureNotify event, serial 34, synthetic YES, window 0x4600001,
    event 0x4600001, window 0x4600001, (741,616), width 178, height 178,
    border_width 2, above 0x133f702, override NO

ButtonRelease event, serial 34, synthetic NO, window 0x4600001,
    root 0x1a6, subw 0x4600002, time 89185289, (45,38), root:(788,656),
    state 0x400, button 3, same_screen YES

---

### Post by Favux on 2009-07-14
So using:
```
xsetwacom set stylus Button2 "Button 3"
```
or
```
xsetwacom set stylus Button2 "3"
```
invokes the Keymap.

Although it is very silly why not try:
```
xsetaiptek list
```
and
```
xsetwacom list
```
and see if there is any output?

---

### Post by Jan Alleman on 2009-07-15
Here is a reference to the Button events: [http://tronche.com/gui/x/xlib/events/keyboard-pointer/keyboard-pointer.html#XButtonEvent](http://tronche.com/gui/x/xlib/events/keyboard-pointer/keyboard-pointer.html#XButtonEvent)

In hexadecimal notation:

0x0100: Button1Mask
0x0200: Button2Mask
0x0400: Button3Mask

Now the xev output makes sense; the state field shows the current state, after the button event it changes into the state reported in the next event. So xev tells that (altough I thought I didn't) I lifted the tip, released button2, pressed button3 and touched the panel.
**[FONT=monospace][/FONT]**[FONT=monospace][/FONT]

---

### Post by Jan Alleman on 2009-07-15
There doesn't seem to be a xsetaiptek; xsetwacom gives
```
stylus stylus
```I also tried several xsetwacom get stylus <param> commands, but they all return X error 2 (Bad value (integer parameter out of range for operation))

---

### Post by Favux on 2009-07-15
Hi Marc,

OK, weird.  Since linuxwacom is installed (wacom-tools too?) and it sees the stylus, let's see if we can map the stylus buttons through it.  In a terminal:
```
xsetwacom set stylus Button2 "Button 2"
xsetwacom set stylus Button3 "Button 3"
```
or could it just be:
```
xsetwacom set stylus Button2 "2"
xsetwacom set stylus Button3 "3"
```

---

### Post by Jan Alleman on 2009-07-15
No, xsetwacom commands are not accepted (neither get or set).
X error 2: BadValue.

---

### Post by Favux on 2009-07-15
Hi Marc,

It was worth a try.  Some of these tablets could kind of be set up on earlier versions of Ubuntu with earlier versions of linuxwacom.

By the way the Xlib Programming Manual and XButtonEvent page are seriously good finds.  I'm starting to vaguely understand some of this stuff.

---

### Post by Jan Alleman on 2009-07-15
Another experiment: pressing button3 and then touching the tablet fires a button1, button2 and button3 event respectively. Lifting the tip fires them again, in the same order, but the button 3 event seems to be a press rather than a release. The behaviour of button2 depends on the pressure; if the tip touches only slightly the tablet, button events are fired; when I raise the pressure, no button events come through any more.

---

### Post by Jan Alleman on 2009-07-15
Ok, for what it's worth: I found a way to make button two always fire button2 and button3 events together and silence button3 completely ;-)

```

cd /sys/bus/usb/drivers/aiptek/<your usb identifier here>
echo lower > stylus_upper
echo blah > execute

```

(from the aiptek sourceforge page)

Read the source of the linux and x drivers; it should be possible to increase the baud rate from 9600 to 19200 ;-)
And a jitter delay can be programmed with the jitter file in the above directory (checked it, but couldn't see the difference) or by means of a jitterDelay module option on the aiptek kernel module.
The macro keys seem to be handled in the kernel module; it looks like the x driver does not know what to do with them.

---

### Post by Favux on 2009-07-15
Hi Marc,

Wow!  Serious progress.

I'm pretty sure I've seen baud rate for serial tablet's set upstream in some of the configuring .fdi's, maybe the TabletPC.fdi (or whatever it is called).  Maybe a specific "quirk" for a particular brand.

So you're saying the macros would have to be coded into the aiptek kernel module?

Edit:  Another thought.  The linuxwacom drivers xserver-xorg-input-wacom sound like they're installed.  Maybe to get the xsetwacom commands to work you also need wacom-tools installed.  Probably not, because X should have complained about missing xsetwacom rather than integer 2.

---

### Post by Jan Alleman on 2009-07-15
> **Favux said:**
> 
I'm pretty sure I've seen baud rate for serial tablet's set upstream in some of the configuring .fdi's, maybe the TabletPC.fdi (or whatever it is called).  Maybe a specific "quirk" for a particular brand.


Not the most important thing ;-)

> So you're saying the macros would have to be coded into the aiptek kernel module?No, I think it has to be done in the X module. Xev for instance sees movement events (not sure about the button 1 press) in the macro areas; someone (and to me that is the X module) fails to translate them into key events though.

> Edit:  Another thought.  The linuxwacom drivers xserver-xorg-input-wacom sound like they're installed.  Maybe to get the xsetwacom commands to work you also need wacom-tools installed.  Probably not, because X should have complained about missing xsetwacom rather than integer 2.xserver-xorg-input-wacom is installed indeed. I tried to remove it, but then apt wants to remove xorg-input-all and that sounded like a bad idea. Besides that, I have the xserver-org-input-aiptek also.
I have wacom-tools installed as well, indeed for things like xsetwacom and wacdump. Wacdump seems to be the only of the tools that works.

---

### Post by sheffield on 2009-07-16
HI All
sorry for not being around but not been too well, you will all be glad to know that the tablet is being picked up by GIMP.

I have pressure, and it seems to work great, I would just like to say thanks for all your wonderful help, time efforts and energies.  I am reading through the extra posts re the buttons and will let everyone know the outcomes.


Many many thanks

John
Newbie

---

### Post by Jan Alleman on 2009-07-16
That's nice John.
Not kidding: it looks like our situation had swapped today.I wanted to try a new battery in my pen, so began experimenting and found out that I had no pressure. Tried gimp: did not paint at all, or, if it did: first a straigt line, apparently starting from the left corner of the screen to the cursor, and from there on I was able to paint, just until the moment I lifted the tip. Some of the straight lines had a gradient all from the upper left corner to the tip.

I think I know how to reproduce it (at least for this session): I used to have Mode set to relative (for playing brain training on the ds emulator ;-)) and it used to work fine. Today it doesn't. Only when I have set the Mode to absolute, I have pressure and no drawing artifacts. Relative is apparently relative to 0,0 today.

Weird stuff. I tried to change from absolute to relative within x:

```

echo relative > coordinate_mode
echo blah >execute

```and yes, the cursor works in relative mode now, also within gimp, but pressure is completely lost. Everything drawn is nearly invisible. Changed back to absolute: everything is normal again.

Btw: the battery, straight from the shop, didn't wash out the button problems.

---

### Post by Favux on 2009-08-03
Hi Marc and John,

How about trying this?:
```
xinput set-button-map "name" 1 2 3
```
where you got the name from:
```
xinput list | grep 'id='
```
and to view current button map:
```
xinput get-button-map "name"
```
Of course you can change the button map to what you want.  Say the first button a right click and the second a middle click:
```
xinput set-button-map "name" 1 3  2
```
And then plug the line into plug that line into ~/.xstartup or other init file.

From [https://wiki.ubuntu.com/X/Config/Input#Example:%20Disabling%20middle-mouse%20button%20paste%20on%20a%20scrollwheel%20mouse](https://wiki.ubuntu.com/X/Config/Input#Example:%20Disabling%20middle-mouse%20button%20paste%20on%20a%20scrollwheel%20mouse)

And if it works we can add it to the .fdi.

---

### Post by gawryl77 on 2010-04-04
hi All,
this is my first post (and i am happy for that)

so let me introduce in a few words: i am from Poland and i am a teacher assistant of one of polish university (physics department) . anyway - i've using Gentoo distro for some time and now i want to introduce something simpler to my students - so i've chosen Ubuntu 9.10. 

unfortunately - after installing Ubuntu 9.10 (on my own computer) i cant go with my SpyDee tablet ([http://www.spydee.eu/products/graphic_tablets/spydee_painter_sp_2000](http://www.spydee.eu/products/graphic_tablets/spydee_painter_sp_2000)) witch is a clone of an Aiptek tablets. the problem is that Ubuntu cant recognize 'clics' - since mouse cursor works (moves )nice when i am operating with my tablet (i have installed xserver-xorg-input-aiptek)

here is my lsusb results:

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 005 Device 005: ID 08ca:0021 Aiptek International, Inc. APT-2 Tablet**
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 1241:1503 Belkin Keyboard
Bus 003 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

here is my xiniput list results:
....
"Aiptek"    id=8    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 7

and i am **worry about it is recognized as a Keyboard** type?!

cat /var/log/Xorg.0.log:
....
(**) Aiptek: always reports core events
(**) Aiptek: Device: "/dev/input/event6"
(II) Aiptek: Found 3 mouse buttons
(II) Aiptek: Found x and y relative axes
(II) Aiptek: Found scroll wheel(s)
(II) Aiptek: Found x and y absolute axes
(II) Aiptek: Found absolute touchpad
(II) Aiptek: Found keys
[B](II) Aiptek: Configuring as touchpad
(II) Aiptek: Configuring as keyboard[/B]
(**) Aiptek: YAxisMapping: buttons 4 and 5
(**) Aiptek: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Aiptek" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "pl"
(WW) Aiptek: touchpads and touchscreens ignore relative axes.
(**) Aiptek: (accel) keeping acceleration scheme 1
(**) Aiptek: (accel) filter chain progression: 2.00
(**) Aiptek: (accel) filter stage 0: 20.00 ms
(**) Aiptek: (accel) set acceleration profile 0
(II) Aiptek: initialized for absolute axes.

here is my /etc/hal/fdi/policy 
<?xml version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
      <merge key="input.x11_options.USB" type="string">On</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.Mode" type="string">relative</merge>
      <merge key="input.x11_options.zMin" type="string">0</merge>
      <merge key="input.x11_options.zMax" type="string">511</merge>
      <merge key="input.x11_options.KeepShape" type="string">On</merge>
    </match>
  </device>
</deviceinfo>

so i try to do xev and i can see:
[I]MotionNotify event, serial 33, synthetic NO, window 0x4800001,
    root 0x13c, subw 0x0, time 3546236, (128,99), root:(1386,792),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 33, synthetic NO, window 0x4800001,
    root 0x13c, subw 0x0, time 3546268, (127,99), root:(1385,792),
    state 0x0, is_hint 0, same_screen YES

ButtonPress event, serial 33, synthetic NO, window 0x4800001,
    root 0x13c, subw 0x0, time 3546396, (127,99), root:(1385,792),
    state 0x0, button 1, same_screen YES

ButtonRelease event, serial 33, synthetic NO, window 0x4800001,
    root 0x13c, subw 0x0, time 3546508, (127,99), root:(1385,792),
    state 0x100, button 1, same_screen YES

[/I]when i am using my mouse (Logitech, BTW)
but _when_ i am using my tablet then i can see _only_:
[I]
MotionNotify event, serial 36, synthetic NO, window 0x4800001,
    root 0x13c, subw 0x4800002, time 3617207, (53,33), root:(1311,726),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 36, synthetic NO, window 0x4800001,
    root 0x13c, subw 0x4800002, time 3617223, (54,33), root:(1312,726),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 36, synthetic NO, window 0x4800001,
    root 0x13c, subw 0x4800002, time 3617231, (54,33), root:(1312,726),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 36, synthetic NO, window 0x4800001,
    root 0x13c, subw 0x4800002, time 3617271, (53,33), root:(1311,726),
    state 0x0, is_hint 0, same_screen YES

[/I]i cant see any message about pressing my 512'pressing levels buttons or any 'mouse 1' or 'mouse 2' butoons. however - a 'special keys' called F1 - F12 are working! so 'clicks' are recorded and interpreted as real events (for ex. - after pressing F1 i can see new help window).

so,
how to make it works??? any ideas?

i am waitnig for any suggestions. i am not interested in using that 12-special keys, only first 'mouse button' and 'second mouse button' is what ia need.

best,
gawryl

---

### Post by rchorda on 2010-04-06
Have you tried following instructions... 
[https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet)

The text is in spanish, but the comands are the same :P

The only thing I did diferent than the previous link is to place the fdi file in /etc:

/etc/hal/fdi/policy/preferences.fdi

I supposse this is a solved problem but as this is the first post I found when I was looking information to my own I thougt I sould point to the solution that it works for me.

Good luck!

---


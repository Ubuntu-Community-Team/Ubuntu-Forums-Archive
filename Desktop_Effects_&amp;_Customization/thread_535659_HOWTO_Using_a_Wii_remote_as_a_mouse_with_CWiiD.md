---
title: "HOWTO: Using a Wii remote as a mouse with CWiiD"
date: 2007-08-26
forum: Desktop Effects &amp; Customization
---

### Post by leffect on 2007-08-26
This howto is now also available on the Ubuntu Community Documentation wiki at [https://help.ubuntu.com/community/CWiiD](https://help.ubuntu.com/community/CWiiD) so this version may become out of date. I shall try to keep an eye on them both, however I might miss something!

Following a mash up of other howtos, man pages and help from forum posts (thanks to Babazoid for pointing out a couple of things that should've been obvious, and Rycuda for showing me where I was going wrong with Autoconf) I've got my Wii remotes working nicely as mice in Ubuntu. These instructions have been tested in both Edgy and Feisty. So, without further ado:

[SIZE="4"]HOWTO: Wii Remote as a mouse
[/SIZE]

First things first, there're a handful of packages that need installing:

```

sudo apt-get install libbluetooth2 bluez-utils original-awk bison flex libbluetooth2-dev autoconf mouseemu  libgtk2.0-dev

```

At this point, you can (optionally!) turn on the Wii remote to scan by pressing 1 and 2 simultaneously (all the lights will flash) then running:
```

#hcitool scan

```
If the remote is picked up, something like the following will be displayed:

Scanning ...
        00:19:1D:A8:44:AB       Nintendo RVL-CNT-01

Next, downloading and installing the Wii remote library:
```

mkdir Wii
cd Wii/
wget http://downloads.sourceforge.net/libwiimote/libwiimote-0.4.tgz?modtime=1173542681&big_mirror=0
tar -xf libwiimote-0.4.tgz 
cd libwiimote-0.4/
autoconf
./configure
make
sudo make install

```

And CWiiD - the program for actually using the library:
```

wget http://abstrakraft.org/cwiid/downloads/cwiid-0.5.03.tgz
tar -xf cwiid-0.5.03.tgz
cd cwiid-0.5.03/
./configure 
make
sudo make install
sudo ldconfig /usr/local/lib/

```

At this point, I needed to update my libraries database (I think...) by running
```

sudo ldconfig /usr/local/lib/

```

I seem to need to do this fairly frequently before being able to load wminput - I think it might be after reboots. Does anyone know why, and how to fix that?

Now it's possible to load a gui which shows what the Wiimote is doing:
```

wmgui

```
Select "connect" from the file menu, press 1+2 when prompted then OK. Lights and rumble can be turned on and off from the controls menu, and which inputs are displayed from the settings menu.

Next up is the mouse "emulator" which allows you to control the mouse with the Wiimote. At this point, it can be run with default settings (tilting the Wiimote moves the pointer, A and B work as left and right click).

Press 1 and 2 to enter discoverable mode then type:
```

sudo wminput

```

In order to get it working with the sensor bar, and to get the buttons to emulate keyboard functions, a couple of bits need to be added to xorf.conf.

Open xorg.conf in your favourite text editor (eg: sudo gedit /etc/X11/xorg.conf - don't forget the sudo! ) then add the following section after the last "InputDevice" section:

```

 Section "InputDevice"
        Identifier      "Wiimote"
        Driver          "evdev"
        Option          "Name"          "Nintendo Wiimote"
EndSection

```

and the following at the end of the "ServerLayout" section:

```

InputDevice     "Wiimote" "AlwaysCore"

```

Now to reload xorg.conf by restarting X. (if there's a better way to reload it, I'd appreciate it if someone told me!) Make sure you haven't got anything unsaved, then press ctrl+alt+backspace. This will drop you back at a login screen, so make sure you know how to get back here!

Now you can reload wminput with the IR settings. Press 1 and 2 on the Wiimote to enter discoverable mode and type:

```

sudo wminput -c ir_ptr

```

Now waving the Wiimote at your sensor bar will move the mouse around the screen! A and B still act as left and right click - just like in the Wii menus!

It's worth noting that if the Wii is turned off, so is the sensor bar, so you have to have it turned on. This means that if your Wiimotes are paired with your console, when you press 1 and 2, they'll automatically link to the console, rather than your computer. I'm currently working round this by pressing the red button under the battery cover instead of 1 and 2 to enter discoverable mode. I'm planning to go and pair one of my Wiimotes with someone else's console, so I won't have to do that.

If you want to change the config files, they're in /usr/local/etc/cwiid/wminput - it'll load "default" unless something else is specified. After install, default is linked to acc_ptr, so the acclerometers control the pointer. buttons contains the mappings for the buttons to keys, and is linked by the other config files. I've made a new config file, which is basically a copy/paste from buttons and ir_ptr:

```

#IR pointer 

Plugin.ir_ptr.X	= ~ABS_X
Plugin.ir_ptr.Y	= ~ABS_Y

#buttons

Wiimote.A		= BTN_LEFT
Wiimote.B		= BTN_RIGHT
Wiimote.Up		= KEY_UP
Wiimote.Down	= KEY_DOWN
Wiimote.Left	= KEY_LEFT
Wiimote.Right	= KEY_RIGHT
Wiimote.Minus	= KEY_BACK
Wiimote.Plus	= KEY_FORWARD
Wiimote.Home	= KEY_HOME
Wiimote.1		= KEY_SPACE
Wiimote.2		= 

#Nunchuk.C		= BTN_LEFT
#Nunchuk.Z		= BTN_RIGHT
#
#Classic.Up		= KEY_UP
#Classic.Down	= KEY_DOWN
#Classic.Left	= KEY_LEFT
#Classic.Right	= KEY_RIGHT
#Classic.Minus	= KEY_BACK
#Classic.Plus	= KEY_FORWARD
#Classic.Home	= KEY_HOME
#Classic.A		= BTN_LEFT
#Classic.B		= BTN_RIGHT
#Classic.X		= 
#Classic.Y		= 
#Classic.ZL		= 
#Classic.ZR		= 
#Classic.L		= 
#Classic.R		= 

```

But I'm currently having a few problems with it. The up/down/left/right maps aren't working - up currently does a print screen, the other three don't do anything apparent. I'm not sure where to go with this at the moment. Still, I can control mplayer with it, and that's the main thing - for now!


There are a couple of things I'm not quite happy with here. The first is having to run wminput as a superuser. I'm sure it should be possible to run it as a normal limited user, and if anyone knows why it doesn't work, I'd love to hear it! Also, I'd like to find a way to disassociate my controllers from my console, so that they don't automatically link to it whenever it's on.

Hope this howto's useful, if you get it working, please post and let me know! If you do anything cool or extra, also please let me know, and I'll add it in here somewhere. If you have problems ... well, please feel free to post. I'll do my best to help, but it may be beyond me! I'm still fairly new to Linux (been using it about 8 months now), so my understanding is still a little limited. With that in mind, I'd appreciate it if anyone who knows a bit more about this than I do could tell me if I've done anything wrong, missed anything out, or done anything I didn't need to. I will, of course, update this post as required.

---

### Post by ddrichardson on 2007-08-27
Great howto - would you consider putting a copy in the Wiki?

UAResolved

---

### Post by leffect on 2007-08-28
Thanks, and of course! Which Wiki? The WiiLi one? - Just had a look and it requires a login, and so account to be made. I'll probably do that later today when I'm not supposed to be working!

Have you gone through the same process? Are there any changes you think I should make? Or for that matter, anything I did that I shouldn't have...

---

### Post by Magneticgravity on 2007-08-28
Does this actually work? Like well?

---

### Post by leffect on 2007-08-28
Sort of. It certainly works. Currently, I've only got tilting for moving the mouse around (and A and B as left and right click), rather than using the sensor bar, like the Wii does on the menu screen. This means it's a little more awkward to use, and not quite as nice, but it certainly works to some extent. 

I can see it being useful as is for controlling a media player/Mythbox type setup, or as a pointer for presentations - plan to use it like that tomorrow, in fact! - but it's not going to replace a mouse.

That said, there is the capability there to do it properly. wmgui shows the input from the IR sensor, and it's certainly working, so there's no reason it can't be extended, and I believe wminput is capable of it, I just haven't got the config files working yet. I'd appreciate any input anyone can give on that!

---

### Post by trvr on 2007-08-29
just curious, have you tried using WMD? It's [fairly easy to install]("http://www.wiili.org/index.php/Wiimote_linux_tutorial"); and from the looks of it, it supports movement using the IR sensor. I don't have a sensor bar (I need to pick up a Nyko wireless one), so I don't have a way to test it.

---

### Post by babazoid on 2007-08-31
Cwiid now works with the IR sensor.  It's pretty neat.  Still has a few bugs, but it's coming along.

I found WMD to be horribly documented...  Cwiid isn't very much better, but at least I could get it compiled and running!

I found that I had to add this to my xorg.conf to get the ir_ptr working:

(in the ServerLayout section):     

```
InputDevice     "Wiimote" "AlwaysCore"
```

and

```
Section "InputDevice"
        Identifier      "Wiimote"
        Driver          "evdev"
        Option          "Name"          "Nintendo Wiimote"
EndSection
```

under my last InputDevice declaration.

It seems to work now, but only on head 0, can't get it working on my HDTV head 0.1 where I really want it.  Anyone have any ideas?

Thanks

---

### Post by leffect on 2007-08-31
Is that the only thing you had to change? I got the impression there was supposed to be a wminput config file somewhere that I'd need to change, but I couldn't find it, and I couldn't find any examples on the net. I'd also like to be able to flick between desktops with + and -, and scroll with the D-pad (and probably make 1 and 2 things like pause in mplayer), but that might be the /next/ challenge.

I don't have any bright ideas about getting it working on a second head, I'm afraid. Dual monitors has always given me problems in Linux.  :-\

Thanks for the suggestion, I shall give that a try!

---

### Post by babazoid on 2007-08-31
Configuration files on my install are located in /usr/local/etc/cwiid/wminput/

When you want to use the IR pointer you need to run "sudo wminput -c ir_ptr"

Take a look at the ir_ptr file, you'll see some config settings -- you should be able to go from there.

Check out [http://abstrakraft.org/cwiid/wiki/wminput](http://abstrakraft.org/cwiid/wiki/wminput) for more info.

---

### Post by leffect on 2007-09-01
That's great, thanks! For some reason, I couldn't find the config files.  :-\ I've updated the howto now, it now covers using the sensor bar.  :-)

Still having a few issues with button mappings, and I'm not entirely sure why... I suspect it could be because I'm using a laptop, so the keyboard's got different codes for the keys. I've got space working, but up/down/left/right are still failing, and I'd like to set it up to use + and - to flick a desktop left and right in Beryl.

A random thought, could you switch which monitor's which, so the HDTV becomes head 0, so the Wiimote works with it? Granted, that might break other things, but could it be worth trying?

---

### Post by MNICY on 2007-09-01
Just wondering... how well does this work?
is it difficult to move the cursor arround the screen?
on a scale from 1 to 10 (10 being a GREAT mouse, and 1 being a crappy laptop touch screen ;)), what would you rate this?

---

### Post by leffect on 2007-09-02
Heh. That's a fair question, I think! I've not really used it as a proper mouse yet, most of what I've done's been playing, so I've just had a quick go, doing normal web browsing type stuff with it, and I think I'd say, on your scale, **it's about a 6 or 7**.

It's better than one of those little nipple things in the middle of the keyboard, but definately not as good as a real mouse. The main reason it's not as good is 'cos my hands shake a tiny bit, so the pointer jitters slightly - most noticable when I was pulling a scroll bar down slowly as I was reading a site. 

That said, I don't really see it as a direct replacement for a mouse - I intend to use it at times when a mouse is impractical, for controlling my media server from the sofa for example, or when running a presentation. I think for that sort of thing, it's more than good enough.

Oh, and I feel I should give it at least a 2 or 3 point bonus for the cool factor, so that puts it up between 8 and 10.  ;-)

---

### Post by Ymze on 2007-09-02
Anyone got some tips on how the printscreen issue can be fixed ?

when i add the lines that the first post says, in my xorg.conf,  my up-button on the wiimote is taking a screenshot, when the xorg.conf is without the lines, it works fine.

---

### Post by leffect on 2007-09-02
That's interesting... I've just tried it again without the xorg additions (I've got one computer with the xorg stuff, and controlling with pointing, the other without and controlling with tilting 'cos I haven't updated it yet) and the buttons do nothing - no scrolling, no screenshotting.

I'm afraid I don't have an answer though - I'm still stuck with screenshots, instead of cursor movement.

---

### Post by tekwiki on 2007-09-02
> **babazoid said:**
> Cwiid now works with the IR sensor.  It's pretty neat.  Still has a few bugs, but it's coming along.

I found WMD to be horribly documented...  Cwiid isn't very much better, but at least I could get it compiled and running!

I found that I had to add this to my xorg.conf to get the ir_ptr working:

(in the ServerLayout section):     

```
InputDevice     "Wiimote" "AlwaysCore"
```

and

```
Section "InputDevice"
        Identifier      "Wiimote"
        Driver          "evdev"
        Option          "Name"          "Nintendo Wiimote"
EndSection
```

under my last InputDevice declaration.

It seems to work now, but only on head 0, can't get it working on my HDTV head 0.1 where I really want it.  Anyone have any ideas?

Thanks



How were you able to get the IR working? I have cwiid working perfectly and even got the UP DOWN LEFT RIGHT to work correctly, I've got B mapped to LEFT CLICK and A mapped to ALT so I can easily drag a window from anywhere inside it. I just can't seem to figure out how to get an ir signal... wmgui shows nothing with ir chosen.

Any help is greatly appreaciated!!

---

### Post by tekwiki on 2007-09-02
Oh by the way the PRINT SCREEN thing and the directional buttons can be fixed by using the following mapping... also note all buttons on this mapping work, have not yet assigned Wiimote.1 and Wiimote.2


Wiimote.A       = KEY_LEFTALT
Wiimote.B       = BTN_LEFT
Wiimote.Home    = KEY_HOME
Wiimote.Minus   = KEY_ESC
Wiimote.Plus    = KEY_SPACE
Wiimote.Left    = KEY_HENKAN
Wiimote.Right   = KEY_MUHENKAN
Wiimote.Up      = KEY_KATAKANA
Wiimote.Down    = KEY_KPENTER


Any help with my IR issue in return?

---

### Post by Ymze on 2007-09-02
Thank you tekwiki   =D

now i can finally use the wiimote with my Mythbox  XD

my ir worked without doing anything special, just enabled ir in wmgui, and lighted a candle (dont have sensor bar) and it worked.

EDIT: and of course to get IR to work with wminput, i added the linse from first post to my xorg.conf

---

### Post by tekwiki on 2007-09-02
> **Ymze said:**
> Thank you tekwiki   =D

now i can finally use the wiimote with my Mythbox  XD

my ir worked without doing anything special, just enabled ir in wmgui, and lighted a candle (dont have sensor bar) and it worked.

EDIT: and of course to get IR to work with wminput, i added the linse from first post to my xorg.conf

 

AH HAH Thanks for the tip on the candle! Wonder what I could use that would be a little more permanent.

---

### Post by leffect on 2007-09-02
Ah yes - to use the IR, you need an IR source of some description. Here's a copy of what I've just put on the Wiki page:

> Since the sensor bar consists of a number of IR LEDs (in two groups, one at each end of the bar), which the Wii remote detects as two dots, it's relatively easy to make an alternative sensor bar for use away from the Wii. Ideally, you want two IR point sources, such as IR LEDs, however candles, lighters, light bulbs etc will work as well. Also, CWiiD only actually requires a single point to track, so it is possible to just point the remote at a room light, and track from that.

There are a number of companies selling various Wii accessories, such as replacement sensor bars, which could be used, however I plan to buy some IR LEDs and mount them on my laptop, and connect them to a USB port. 

I think that says everything I was going to! So yeah, I'm going to build myself a thing with a couple of USB powered IR LEDs on it that I can stick on my laptop, or shove under a projection screen for presentations.

Thanks for the suggestions on keys, Tekwiki, I'll give that a shot now! I don't suppose you know /why/ it didn't work? If it does work, I'll come back and change the howto and wiki page anyway.

(Edit:) I've tried that, and the arrow keys now work fine, that's great, thanks! Only thing is, now the binding for B as right mouse button has stopped working. I'm sure it was working before! It's really weird... So, I'm hoping if you tell me how you worked out the other key mappings, I'll be able to get that one working for myself.

---

### Post by tekwiki on 2007-09-02
> **leffect said:**
> Ah yes - to use the IR, you need an IR source of some description. Here's a copy of what I've just put on the Wiki page:



I think that says everything I was going to! So yeah, I'm going to build myself a thing with a couple of USB powered IR LEDs on it that I can stick on my laptop, or shove under a projection screen for presentations.

Thanks for the suggestions on keys, Tekwiki, I'll give that a shot now! I don't suppose you know /why/ it didn't work? If it does work, I'll come back and change the howto and wiki page anyway.


I'm not sure exactly why the keys didnt work. I figured it out by using xev to capture the keys, what I did was I set the up down left right to UP DOWN LEFT RIGHT and captured the keys in xev. This gave me a different address than what was stated in my input.h file in my linux header includes. I noted that it was off by a specific number of spaces, from there it was just counting that number of spaces up for the rest of the buttons, however a couple were off even one or two from that.

From what I can tell, THIS IS THE MOST IMPORTANT PART, is that X sees the wiimote as a different keyboard layout, therefore what is KEY_UP on one keyboard, is something totally different on another....

Anyone have any idea how we can change the keyboard layout assigned to the wiimote? This I believe would fix the problem.

---

### Post by leffect on 2007-09-02
There's a file in with the source files called cwiid-0.5.03/wminput/action_enum.txt which has a list of the codes for all the keys. I think the problem is due to wminput mapping directly to key codes, rather than through X's keyboard codes, which means that it's not corrected for what keyboard you're using. I don't think that's fixable though, without rewriting at least some of the source code, which is sadly beyond me. 

Doesn't explain why the BTN_RIGHT has suddenly stopped working of course. :-\  I shall continue to play!

(Edit) A little more experimentation has shown me that BTN_RIGHT is now being picked up as a middle click,  BTN_MIDDLE isn't doing anything, BTN_MOUSE is a left click, BTN_SIDE and BTN_EXTRA also don't do anything.

This is especially frustrating because BTN_RIGHT as, well, right click used to work, before I changed the settings for the D-pad, but now even if I use old copies of the config files, it doesn't work.

I suspect the software might be a little beta!

---

### Post by tekwiki on 2007-09-03
> 
Doesn't explain why the BTN_RIGHT has suddenly stopped working of course. :-\  I shall continue to play!

(Edit) A little more experimentation has shown me that BTN_RIGHT is now being picked up as a middle click,  BTN_MIDDLE isn't doing anything, BTN_MOUSE is a left click, BTN_SIDE and BTN_EXTRA also don't do anything.

This is especially frustrating because BTN_RIGHT as, well, right click used to work, before I changed the settings for the D-pad, but now even if I use old copies of the config files, it doesn't work.

I suspect the software might be a little beta!

BTN_RIGHT never did work for me! 

I plan on diving into the source in the next few days, I will post if I find anything.

---

### Post by tekwiki on 2007-09-03
I just found something very interesting, BTN_RIGHT does do something, what I'm not sure, but if I have a nautilus window open and I double click the SUPPOSED BTN_RIGHT, it opens the folder in a new window, and closes the old one, usually if you double click the left mouse button it will open that folder in a new window with the old one open, WHAT THE @!*& is that? Anyone know what is happening here?

---

### Post by tekwiki on 2007-09-04
HAHAHAHAHAHAHAHAHHHHHHHHHHHHHHHHHHAAAAAAAAAAAAAAAAAAAA


Hours and Hours and Hours! of hacking and I finally have it....

**[CENTER][SIZE="7"]I HAVE FIXED THE BTN_RIGHT ON THE WIIMOTE[/SIZE][/CENTER]**

Ok here is what I did step by step.....

I downloaded a different version of the wriver WMD....
I downloaded a package that took me forever to find, the WII-XMMS python hack (THIS IS NOT REALLY NEEDED)
I got it all setup, very easy,_ let me know if anybody needs me to post a how-to_
I ran WMD, which gives me the output as seen by X from the wiimote
I ran xev, which I just now found out has a small window to capture mouse clicks, I didnt realize this, I thought it only captured keyboard presses. I run Yakuake and it was covering up this small window! Once I figured this out it was all over.

Long story short two things were needed to figure this out...
    - Something to enable the wiimote (any driver would have worked)
    - And a way to capture supposed mouse clicks (xev)

I set the wiimote to use button '2' as a BTN_RIGHT click event, click while the mouse was over xev, nothing.... set it to be a BTN_MIDDLE event, it showed it as mouse button 2, wait a minute, so why didnt setting it to BTN_MIDDLE work then? Not sure about this part. If you have followed the tutorial on setting up the mouse pointer in your xorg.conf, that is a big clue as to the fix....


Here it is folks, the way to fix BTN_RIGHT!!!!

OMG I just realized something when I went to do a copy/paste on my conf file, I made a huge mistake, that is what fixed it!!

I thought I added th Option to my xorg.conf under the wiimote InputDevice Section for Emulate3Buttons true, but I didn't I added it to my ati remote device section, WTF! 8-[

HAHAHA Anyone was to try this just try either a using BTN_MIDDLE and see if that does a right mouse click, or try adding 

```
Option    "Emulate3Buttons" "true"
```

to your /etc/X11/xorg.conf file....

Let me know if anyone has any success with this! I'll be interested to know the outcome.

---

### Post by leffect on 2007-09-04
Bah, Firefox seems to be very unstable these days! Crashed just before I posted this.  :-\

Right. So, I added that line to my xorg.conf, so the section now shows:
```

Section "InputDevice"
        Identifier      "Wiimote"
        Driver          "evdev"
        Option          "Name"          "Nintendo Wiimote"
	Option    "Emulate3Buttons" "true"
EndSection

```

and it doesn't seem to have made any difference! I restarted X, then tried right clicking - no obvious effect, however when I tried to right click on an icon in my Avant toolbar, it opened the Avant preferences. I then tried to do that with the normal mouse, and couldn't find a combination of buttons which would!

Next, I tried changing BTN_RIGHT to BTN_MIDDLE in my wminput config file, which didn't help either - the B button is certainly still not working as either a right click or a middle click. I'm somewhat out of my depth here - I can see what the options in the config files mean, and I vaguely understand that they're referencing other codes, however I don't really understand the underlying system, so I don't really know where to go next.

What I do know more about is the electronics side. Yesterday, I built a couple of test "sensor bars", consisting of an IR LED (from RS Components) and a resistor, connected to the power lines of a USB plug.

The USB connection gives a 5V source, and the LED was rated at 150mA, so I initially tried a 27R resistor. This was nice and bright (I used a IR sensitive camera to check it was working), but the resistor got quite warm. I also tried 100 and 200R resistors, these were much less bright than with the 27R, but not noticably different. 

I've done range tests with these, and got a range of 1.5m from the 100R resistor, and a range of 5m from the 27R. I realise this depends very much on the LEDs used, however it gives an idea of what's possible!

My next model will have either 2 or 3 LEDs (the LEDs drop about 1.3V to 1.5V each so I can't have 4 in series from 5V - might try anyway though!) in order to get the two points, more brightness and hopefully more range. Doubling the LEDs should get me another 40% or so on the range.

I shall report back!

---

### Post by tekwiki on 2007-09-04
Here is the relevant xorg.conf file if it will help at all....


```

Section "InputDevice"
    Identifier     "ATI Remote"
    Driver         "mouse"
    Option         "Protocol" "PS/2"
    Option         "Device" "/dev/input/mice"
    Option         "SendCoreEvents"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Wiimote"
    Driver         "evdev"
    Option         "Name" "Nintendo Wiimote"
EndSection


```

This may sound a little off, you probably dont have an ati remote, and really I dont even use mine, but I think if you add that section to your xorg it will help, I think even though all the tutorials say to use driver evdev, its actually using /dev/input/mice ??? Thats the only other guess I have..

Anyway I gave up on the right click, even though mine works :) I'm now completely rewriting the WMD drivers, and I've been able to get it to send multiple key events for combo presses that I can then assign in my window manager to do something.....

For instance I have shake right is volume up, shake left is volume down, the z axis is a little harder i can only get it to do one thing at the moment, its play next...

_[SIZE="3"]Anyone interested in working with me on fixing up the WMD driver and fixing these keymaps? If anything else I'm going to go through one by one and figure them all out... Anyone know python? I'm not that fluent, but cant get around good enough to add tons of functionality to WMD, maybe make a config window so you can easily set what each button, and accelerator movement does, maybe even make the thresholds easily changeable. Hit me up on here if you are interested in helping, I might get a site going, this remote ROCKS![/SIZE]_

---

### Post by leffect on 2007-09-05
I shall take a look at that xorg stuff this evening, thanks! I hope it works. :-)

Rewriting them sounds like quite a major task! Good on you for taking it on though! Multiple key combinations sounds fantastic - one of the things I wanted to do was use the + and - buttons for changing desktop, which I don't think I can do at the moment, without remapping, which would confuse me when /not/ using the Wiimote!

I would be more than happy to offer any help I can, however my coding experience is rather limited, I did a little bit of C recently, but that's it (and it was a very little bit of C), but if there's anything you want testing, or ideas you want to bounce off someone - or you can think of something I could help with, please give me a shout!

---

### Post by babazoid on 2007-09-06
> **tekwiki said:**
> Here is the relevant xorg.conf file if it will help at all....

...

Anyway I gave up on the right click, even though mine works :) I'm now completely rewriting the WMD drivers, and I've been able to get it to send multiple key events for combo presses that I can then assign in my window manager to do something.....

For instance I have shake right is volume up, shake left is volume down, the z axis is a little harder i can only get it to do one thing at the moment, its play next...

_[SIZE="3"]Anyone interested in working with me on fixing up the WMD driver and fixing these keymaps? If anything else I'm going to go through one by one and figure them all out... Anyone know python? I'm not that fluent, but cant get around good enough to add tons of functionality to WMD, maybe make a config window so you can easily set what each button, and accelerator movement does, maybe even make the thresholds easily changeable. Hit me up on here if you are interested in helping, I might get a site going, this remote ROCKS![/SIZE]_

I'm kinda confused.  I thought this thread was on Cwiid not WMD.  Are you using Cwiid or WMD?   Or both somehow?  

Cwiid works fine for me by itself, but I still can't figure out how to use it on my secondary display.

---

### Post by tekwiki on 2007-09-06
> **babazoid said:**
> I'm kinda confused.  I thought this thread was on Cwiid not WMD.  Are you using Cwiid or WMD?   Or both somehow?  

Cwiid works fine for me by itself, but I still can't figure out how to use it on my secondary display.

My apologies, it was about Cwiid, but I switched from using cwiid to wmd. The keycode problem remains the same in both however. I'm half way through getting the correct mapping (for my system at least) and I will post it when complete.


I switched to the WMD driver because it is written in python and is very easy to manipulate. It does the same thing as cwiid but more, by allowing you to map things to shaking the remote, such as right for volume up, left for volume down.

I'm already half way through writing the class for a gui to manipulate the options. An rc of my fork which I'm calling (for the moment) Wiimote Command Center should be available in about a month or so, and a site will be available by then.

---

### Post by tekwiki on 2007-09-06
By the way how do you have your secondary display set up? Mine is using Nvidia Twinview and wmd works on both displays....

---

### Post by leffect on 2007-09-07
I had a thought last night, about that multiple display issue. As far as I understand, there are basically two ways to do multiple displays in X. One has what's effectively one desktop stretched over two monitors, the other has 1 desktop on each monitor. I suspect that you might be configured the latter way, and so the Wii driver has mapped the sensor positions to one of your desktops. If it was the other way, I suspect you wouldn't have that problem.

This is a bit of a guess, I admit, but I think it makes sense!


On another note, Tek, have you contacted whoever wrote CWiiD and WMD? If you can get hold of them, they might want to help, or be able to give you some useful information.

Looking forward to seeing what you do with it!

Something that occurred to me, which I think should be fairly easy to implement, is a way of turning the Wiimote off to save battery, but keep scanning for it for when it's turned on again. This would be good when watching films, or something similar - you could turn the 'mote off once you've got it playing, then turn it on again if you want to pause, or start a different file. That'd stop the battery running out as quickly, and stop the cursor skittering across the screen if you nudged the Wiimote. :-)

I had considered using one of the buttons (ideally the power one, but I don't know if that's supported) to run a script that would kill wmInput (to disconnect) then run it again in continual scan mode so it would pick the Wiimote up again when you turned it on.

---

### Post by babazoid on 2007-09-07
> **tekwiki said:**
> By the way how do you have your secondary display set up? Mine is using Nvidia Twinview and wmd works on both displays....

Ahhh.  Thanks for clearing that up!  I tried WMD and had issues getting it running...  Maybe I'll try again.

My monitors are set up using twinview as well.  Two discrete displays (no mirroring or spanning or anything).  Here is my screen section:

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1440x900 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "ExactModeTimingsDVI" "TRUE"
    SubSection     "Display"
        Depth       24
        Modes      "1368x768_60" "1360x768_60"
    EndSubSection
EndSection

```

I have no idea why Cwiid won't work... works fine on screen 0 but only goes to the extreme edge of screen 1.  Oh and my serverlayout is:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice     "Wiimote" "AlwaysCore"
EndSection

```

Any help would be appreciated!

Thanks

---

### Post by leffect on 2007-09-07
I think this: "Two discrete displays (no mirroring or spanning or anything). " is why it doesn't work. I tried to explain my idea in my previous post, but I'm really tired today, so I might not have explained it very well. I think because your displays are discrete, rather than spanned. CWiiD, I think, places the mouse on the screen, a distance across and down in proportion to the position the IR camera is picking up the sensor bar, so if there's a second display as well, it's not considered part of it. If it was spanned, I suspect it might work better (emphasis on might!)

This is, of course, a guess, but it's based on my understanding of how X handles multiple monitors. 

The other solution, of course, is to swap the screens over, and configure your TV as monitor 0. I understand that's not ideal though!

Have I explained well enough in the top part? I'm aware it's not great.

---

### Post by gazlang on 2007-09-07
Hi,

Just wondering if there is a way to make wminput start and search for a wiimote automatically on system boot??

i tried installing the crontab: @reboot wminput -w -c /usr/local/etc/cwiid/wminput/ir_ptr
but no luck with that!

Any other suggestions??

I want the wiimote to be my only mouse for a HTPC setup, and don't want to have to run the terminal on every boot.

Cheers

---

### Post by leffect on 2007-09-07
If you go to the preferences menu, and sessions, there's a tab in there where you can select things to load on login. You could try putting it in there, however I suspect that since you need to run it as a superuser (ie sudo), it might not work. I think if you put gksudo before it (ie ```
gksudo "wminput -w -c ir_ptr"
```) it should work.

Emphasis on should - I don't have a Wiimote with me here, so I can't test it properly.

---

### Post by gazlang on 2007-09-07
Well, I have kubuntu, so it's slightly different. I have a section called 'System Services' in which you can change which programs start on boot. However, you can only select from those in the list, and wminput isn't there.

Ultimately I want to run LinuxMCE on my system with the wiimote running on it. I think there will be more problems than getting wminput to run on boot :) but it will be a good start

---

### Post by leffect on 2007-09-08
Hmmm. I don't have Kubuntu any more (decided I preferred Gnome) so I can't really help you, I'm afraid. Maybe Google will be able to throw up something helpful?

The other alternative, if you can get it to login automatically, would be to ssh to the computer, and load wmInput from there, using a different machine.

---

### Post by Officer Dibble on 2007-09-08
I considered using this app called GlovePie with Windows, but never got around to trying it. Could something like this be used with Linux via Wine?

[GlovePie]("http://carl.kenner.googlepages.com/glovepie_download")

[GlovePie on YouTube]("http://www.youtube.com/watch?v=A_ytdW6Ys2A")

---

### Post by gazlang on 2007-09-10
What I need is a start-up script to put into /etc/innit.d that starts up wminput on reboot and keeps t restarting untill a wiimote is found.

Simply adding wminput -w -c ir_ptr as a cronjob doesn't work because wminput will exit if the bluetooth adapter hasn't found the wiimote.

I have no clue how to write startup scripts unfortunately!

Does anybody have an idea of how to put something like this together?

---

### Post by leffect on 2007-09-10
Are you sure about that? I was under the impression that -w was supposed to make it keep looking until it found one?

Maybe have the cron task run a script with a loop in it... I'm afraid I don't know much more about bash scripting than you do, but I could look into that if you want?

---

### Post by Eezyville on 2007-09-10
Oh SNAPS!! :shock:


I gotta try it out!

---

### Post by gazlang on 2007-09-11
Well it was just an idea, since I have to keep restarting wminput from the terminal 4 or 5 times before it connects.

After a bit of pondering though I think the -w does make wminput wait untill a wiimote is found but only so long as it has a bluetooth port to listen on, and in my case (as I have kubuntu, not sure if it is the same with ubuntu) I don't think a port is opened untill my bluetooth manager (kbluetoothd) has detected a bluetooth device and started up.

wminput -w works fine so long as kbluetoothd is running already.

So maybe I need to try getting kbluetoothd to run on boot and enter detect mode before wminput starts.

Has anybody tried running wminput -w -c ir_ptr as a cronjob in ubuntu with any success?? Or even adding it to the sessions menu to load on login??

---

### Post by Ymze on 2007-09-11
yeah, i added "wminput -d" in my session menu and rebootet, waited a while and connected my wiimote just fine =)  i use ubuntu gnome

---

### Post by DaRKoP on 2007-09-19
hi, how i do to use the button center in button 2 of wiimote? 

Wiimote.2		=??????

thx

---

### Post by spiderworm on 2007-09-19
On Feisty I am having trouble during the ./configure step, any help appreciated:

> checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for gawk... gawk
checking for flex... flex
checking lex output file root... lex.yy
checking lex library... -lfl
checking whether yytext is a pointer... yes
checking for bison... bison -y
checking for python... python
checking for pthread_create in -lpthread... yes
checking for hci_devid in -lbluetooth... yes
checking for dlopen in -ldl... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdint.h... (cached) yes
checking bluetooth/bluetooth.h usability... yes
checking bluetooth/bluetooth.h presence... yes
checking for bluetooth/bluetooth.h... yes
checking for bluetooth/l2cap.h... yes
checking for bluetooth/hci.h... yes
checking linux/input.h usability... yes
checking linux/input.h presence... yes
checking for linux/input.h... yes
checking for linux/uinput.h... yes
checking for library containing strerror... none required
./configure: line 4546: syntax error near unexpected token `GTK,'
./configure: line 4546: `PKG_CHECK_MODULES(GTK, $pkg_modules)'


---

### Post by tribble222 on 2007-09-29
> **gazlang said:**
> Well it was just an idea, since I have to keep restarting wminput from the terminal 4 or 5 times before it connects.

After a bit of pondering though I think the -w does make wminput wait untill a wiimote is found but only so long as it has a bluetooth port to listen on, and in my case (as I have kubuntu, not sure if it is the same with ubuntu) I don't think a port is opened untill my bluetooth manager (kbluetoothd) has detected a bluetooth device and started up.

wminput -w works fine so long as kbluetoothd is running already.

So maybe I need to try getting kbluetoothd to run on boot and enter detect mode before wminput starts.

Has anybody tried running wminput -w -c ir_ptr as a cronjob in ubuntu with any success?? Or even adding it to the sessions menu to load on login??

What about telling cron to run a bash script at boot?  Have the script loop to check if kbluetoothd is running and once it detects it running, have it run the wminput command?  I'd try it out but I haven't installed Kubuntu yet.

---

### Post by tribble222 on 2007-10-03
I have a solution to the right click problem!  I tried a lot of things with my xorg.conf but I just couldn't get it to do anything.  My left click was mapped to 0x110, middle click 0x210, right click 0x410.  No matter what I did.  So here's a workaround to bind a keyboard key to right click:

1) In Gnome, go to System --> Preferences --> Accessibility --> Keyboard Accessibility
2) Check "Enable keyboard accessibility features"
3) Click the Mouse Keys tab and check "Enable Mouse Keys", then close the window
4) Open up a terminal and run xev (sudo apt-get install xev, if you don't have it)
5) Make sure the xev window has focus, then press the key on your keyboard you want to bind to right click and make a note of the keycode, then close xev
6) Type the following into the terminal, replacing YOURKEYCODEHERE with the keycode you found in step 5

```
xmodmap -e "keycode YOURKEYCODEHERE = Pointer_Button3"
```

Now that button should be mapped to right click!  Now:

7) Edit your config file in /usr/local/etc/cwiid/wminput/ to reflect whatever that keyboard button is (this is mostly trial and error but your /usr/include/linux/input.h can help you)

8 ) In order for this to work every session, add that xmodmap command to your System --> Preferences --> Sessions, to make it run at boot.

That's it!

---

### Post by fatalGlory on 2007-10-10
I've found that after following all the useful info in the wiki page derived from this thread, I have full access to the stuff the wiimote can tell my box - except IR.

Do wmgui AND wminput both use the libwiimote C api to read the IR data?  In wmgui I can see a bunch of infra-red stuff if I just point the remote out the window into the sunlight, but if i run

wminput -c ir_ptr

I get no response from the mouse at all even when pointing it at an IR LED.  Do I just need a more powerful IR source?  Or is it more likely something in the source or a config?  Accelerometer mouse movement is working fine, I've added the InputDevice info to xorg.conf.  Still not even a jitter from the mouse with ir_ptr in use.

Any ideas?

---

### Post by leffect on 2007-10-11
I had a similar problem getting it to work with the IR as well, but that was because I hadn't updated my xorg.conf. You said you added the InputDevice, did you add the Section "InputDevice" as well? You'll need to restart X (ctrl+alt+backspace) after doing that to make it reload the config file.

If that doesn't work, check you've added those bits in the right places, and perhaps post your xorg.conf here for someone to look at!

As for the more powerful source, I've found it to be quite a lot more sensitive in Linux than on the Wii - I've used a lightbulb for example, and it's quite happy with just a single point, instead of two.

---

### Post by fatalGlory on 2007-10-11
lol, my bad.  I did actually add the lines as specified in the howto and restart X (I'm not a stranger to editing the X config file) but after reading your reply I decided to have another check - don't know why but the WiiMote related lines were missing.

Must have accidently replaced the new file with my backup before restarting or something.  Pointing out the window gets a response now, thanks.

You've written a brilliant howto by the way leffect, great contribution to the community.

**A Technical Proposal**
I have an idea.  Why does xorg.conf need to be edited at all?  Could the algorithm in the wminput program not just determine where the mouse should be and place it there with [XWarpPointer?](http://tronche.com/gui/x/xlib/input/XWarpPointer.html)  If the algorithm is simple enough to interpret (or even copy), I might have a go at implementing this.

Is there any real reason under the hood anyone knows of why evdev needs to be used?  Manually editing xorg.conf is a real problem for a lot of new linux (and hence many ubuntu) users.  If this distro could have point and click IR wiimote setup, I think that would be an awesome drawcard.

---

### Post by tribble222 on 2007-10-11
> **fatalGlory said:**
> 
Is there any real reason under the hood anyone knows of why evdev needs to be used?  Manually editing xorg.conf is a real problem for a lot of new linux (and hence many ubuntu) users.  If this distro could have point and click IR wiimote setup, I think that would be an awesome drawcard.

I don't have any experience with anything like XWarpPointer but perhaps it is too slow?  Does it work fully with programs that accept mouse gestures?

Another solution to help the newbies edit their xorg.conf would be to write a script to insert the correct lines, but the warping would definitely be better if it works.

---

### Post by prct2006 on 2007-10-27
I have this problem:

prct@prct-home:/etc/X11$ sudo wminput
Put Wiimote in discoverable mode now (press 1+2)...
Error opening control channel
unable to connect

---

### Post by TheBuzzSaw on 2007-10-27
> **prct2006 said:**
> I have this problem:

prct@prct-home:/etc/X11$ sudo wminput
Put Wiimote in discoverable mode now (press 1+2)...
Error opening control channel
unable to connect
Did you make multiple attempts? Usually, that message comes up for me when I make my first attempt. The blue lights keep blinking, so I just enter "sudo wminput" again, and it catches it the second time. Be persistent. Otherwise, you'll have to check your various settings.

So far, this method has worked wonderfully. I was able to use my Wii remote pointer as a mouse (I have the Nyko wireless sensor bar). Does anyone know how to integrate these controls into games?

---

### Post by prct2006 on 2007-10-28
"Did you make multiple attempts? Usually, that message comes up for me when I make my first attempt. The blue lights keep blinking, so I just enter "sudo wminput" again, and it catches it the second time. Be persistent. Otherwise, you'll have to check your various settings."

the error persist...
Many times.

---

### Post by gavintux on 2007-10-28
I had this problem.

$ wminput -c ir_ptr
ImportError: No module named cwiid

---

### Post by prct2006 on 2007-10-29
Now its work, with a new bluethooth connector.

Tanks.

---

### Post by xjgnsdof on 2007-11-03
Has anyone come up with another solution? I don't want to have to keep buying bluetooth adapters to see which one works. It picks up my Wiimote, but the gui can't connect. It must be a software issue, right?

---

### Post by xjgnsdof on 2007-11-03
I performed all of the steps (in the wiki, I'm at the "Controlling the Remote" step), but in wmgui I get a pop-up saying "unable to connect" and a Terminall message saying "Error opening control channel." I basically copied and pasted every command, so I have no clue why it's working for some of you and not for me. The Wiimote is brand new, and so is my Bluetooth dongle (which manages to pick up the Wiimote in the hcitool scan). What's wrong here?

---

### Post by leffect on 2007-11-04
I've had the computer not spot the Wiimote the first time I try to connect to it a few times. Have you tried selecting "connect" from the file menu again, after it fails, while the lights are still flashing on the wiimote?

I'm afraid I'm not hugely experienced with Linux, so I don't know whether I'll be able to help all that much!

---

### Post by xjgnsdof on 2007-11-04
I have tried that, and it didn't work.

---

### Post by xjgnsdof on 2007-11-10
Am I supposed to be pointing my Wiimote at candles or something ridiculous like that when I'm pressing buttons 1 and 2? I did all the steps up till that, so there's no reason why this isn't working, unless I'm missing something fundamental here.

---

### Post by xjgnsdof on 2007-11-11
I figured out what the problem was: I had to manually set my Wiimote bluetooth address.

First, input ```
hcitool scan
``` to find your Wiimote address.

Then, run wmgui to test everything:
```
wmgui 00:1B:7A:D9:DC:23 
```

Finally, run wminput:
```
wminput 00:1B:7A:D9:DC:23
```

In both cases, you will replace the address above with your own Wiimote address.

---

### Post by feest on 2007-11-16
The wiimote works (wii :)) but my mouse doesn't work anymore, its configured as corepointer using the mx1000 tutorial wiki... any suggestions?

---

### Post by Xanderfoxx on 2007-11-23
A Wii remote for Ubuntu? Do you know how cool that sounds?

If I could make it where the tilting moved the cursor the way it does in its intended use, and I get the buttons and such to work, this idea has endless potential for wowing my friends and family.

Really cool. However, how am I going to allocate the time??  :lolflag:

---

### Post by ehcualp on 2007-11-25
ive discovered that the guitar hero 3 controller is just the classic controller rerouted. so i have assigned the keys for ***_frets on fire_*** to correspond with the guitar hero controller!
I have gained the ablitiy to pwn all now! 
:guitar:

my buttons code:
```

#buttons

Wiimote.A	= BTN_LEFT
Wiimote.B	= BTN_RIGHT
Wiimote.Up	= KEY_UP
Wiimote.Down	= KEY_DOWN
Wiimote.Left	= KEY_LEFT
Wiimote.Right	= KEY_RIGHT
Wiimote.Minus	= KEY_BACK
Wiimote.Plus	= KEY_FORWARD
Wiimote.Home	= KEY_HOME
Wiimote.1	= KEY_PROG1
Wiimote.2	= KEY_PROG2

Nunchuk.C	= BTN_LEFT
Nunchuk.Z	= BTN_RIGHT

Classic.Up	= KEY_BACKSPACE
Classic.Down	= KEY_ENTER
Classic.Left	= KEY_LEFT
Classic.Right	= KEY_RIGHT
Classic.Minus	= KEY_8
Classic.Plus	= KEY_2
Classic.Home	= KEY_HOME
Classic.A		= KEY_F5
Classic.B		= KEY_F6
Classic.X		= KEY_F7
Classic.Y		= KEY_F8
Classic.ZL		= KEY_F9
#Classic.ZR		= 
#Classic.L		= 
#Classic.R		= 

```
in frets on fire i have green on f5, red on f6, and so on to purple on f9. the strum is enter or backspace. and thats basicly all i needed. i use the keyboard to set up and pick the song, but beyond that, its all wii guitar! 
have fun! :)
 (ps. make a backup copy of your buttons file incase you dont want this later on..)

---

### Post by Damwid on 2007-11-29
Seems the libwiimote library is unnecessary, I got cwiid work without libwiimote installed. 

I also found another weird problem:
when run wminput with "-c buttons" option, all four direction buttons work well, while other buttons don't. without this option, acc_ptr config is used, button A and B work as left/right mouse button, but all direction buttons don't work anymore.

I dig into the source and found wminput have nothing to do with X, it just use kernel uinput driver to emulate an input device by writing the events into /dev/input/uinput. By adding the debug output, I found the same data are sent to /dev/input/uinput for a given button in these two cases, but the behavior is totally different. I was confused by this, maybe a input module bug?

I will continue debugging on this, since the keycode read from wiimote is correct, this would be a big problem to fix.

---

### Post by qwerdy on 2007-11-29
if you installed the cwiid package, the library is included

---

### Post by kia94 on 2007-12-04
This all worked good till the very end. when a try and us my mouse in keyboard in fps games, if i press a key on the keyboard the mouse will freeze. making any kind of shooter impossible to play

any idea on how to make this work or a least get it back to original state 

thank u so much Sean 
:lolflag:

---

### Post by Niklas Schröder on 2007-12-08
nvm...

---

### Post by sem7ex on 2007-12-11
Hi people,
i am stuck at starting wminput. i get:

unable to open uinput

wmgui worked fine and it displays all input from the wiimote.
what is uinput and how can i get it?
can anybody help ... please!?




nevermind ... got it working.

anyway this is GREAT! i wanted to try it out it in fps games ... but its not that usable.

---

### Post by abandonedthe_mulletator on 2007-12-19
> **sem7ex said:**
> Hi people,
i am stuck at starting wminput. i get:

unable to open uinput

wmgui worked fine and it displays all input from the wiimote.
what is uinput and how can i get it?
can anybody help ... please!?




nevermind ... got it working.

I have the same problem.  How did you fix it?:guitar:

---

### Post by otac0n on 2007-12-19
you can probably:
sudo chmod  a+r /dev/input/uinput


anyways, i have the "module cwiid not found" error...

any word on that?

---

### Post by abandonedthe_mulletator on 2007-12-22
I got it working!!!
I had to run:
ldconfig /usr/local/lib/
and
modprobe uinput

before wminput would work.

It's a little strange to control but it works for movies.  Does anyone know how to make certain buttons work with MPlayer like play, stop and skip?  Also it kills the batteries really fast it would be nice if I could turn the wiimote on and off with a button on it.  Anyway great topic; I've attempted to use the wiimote as a remote for my computer a few times and CWiiD is the only one that has worked for me.  Maybe because I'm running Fedora and most posts about this are for Ubuntu.  I didn't get the name right away but its pretty funny CWiiD (seaweed).:lolflag:

---

### Post by qwerdy on 2007-12-22
Edit the buttons file to get it to work with Mplayer.

And if you run wminput as a daemon (wminput -d) then you can turn it off with the off button and just reconnect (press a+b button) when you need to use it again. that will save alot of battery time =)

---

### Post by mikeserv on 2007-12-22
Everytime I try "wminput -d" I get the error that -d is not a vaild option.  

Also, I'm wondering if there's a way to set the buttons to turbo.  I set ```
Wiimote.Dpad.X  = REL_X
Wiimote.Dpad.Y  = -REL_Y

```so that the dpad will work to move the cursor, but I have to continually press it.  I would like to be able to hold down a direction and have the cursor continue to move in that direction until I release the button.

Another thing, what's up with forthewiin.org?  Is there an alternate page for WMD?

-Mike

---

### Post by eFfeM on 2007-12-23
I got things (more or less) running, but I was wondering how to use the mouse in absence of an IR source.

I can use the wiimote with wminput although movement is far from smooth. Also movement from left to right and back is achieved by rotating the wiimote, not by moveing it L-R.

Putting a lamp besides the computer and using ir_ptr makes things a lot better, but is it possible to get a decent performance without ir source??

---

### Post by abandonedthe_mulletator on 2007-12-23
> **mikeserv said:**
> Everytime I try "wminput -d" I get the error that -d is not a vaild option.  


I get the same message with wminput -d.
I installed the newer version of CWiiD but it crashed so I went back to cwiid-0.5.03.

---

### Post by qwerdy on 2007-12-25
yeah, its only available in the newest version of cwiid (0.6.00)

---

### Post by ACLBandit on 2007-12-27
So with this niftiness, my WiiMote now functions as a (somewhat sloppy) mouse. When the howto speaks of a sensor bar, does it, in fact, mean that interesting wireless Nyko one? If so, then I will have to buy one of those. Has anyone tested that bar with just a bluetooth receiver? I would like to make sure it will work correctly before I drop the cash for a sensor bar.

EDIT: Aha, I understand. Any sensor bar will work fine so long as the Wii is turned on. Wonderful. 

Question, though: Does the Nyko have the option to be turned on when the Wii is *not* on?

Also, my Wii remote, when using the infrared pointer, has no right click. The B button, for some reason, is a middle click. I find this to be kind of strange.

---

### Post by davem2312 on 2007-12-27
Well this is interesting.  I just got a Wii for Christmas, and its a lot of fun, and I am now working on the Wii Remote as a mouse for Ubuntu.  I have it all working now, I just have to program the buttons to do what I want.

One bad thing though, and this is why I am posting.  My touchpad on my Dell Inspiron 9300 running Ubuntu 7.10 has stopped working.  At first I thought that this was due to the changes in xorg.conf, so I commented out the lines for the wii remote, but it still didn't work.  Any help would be appreciated.  Here is my xorg.conf

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

# I tried commenting out this section to see if the touchpad would work, but it didn't

Section "InputDevice"
        Identifier      "Wiimote"
        Driver          "evdev"
        Option          "Name"          "Nintendo Wiimote"
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV41.8 [GeForce Go 6800]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-72
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV41.8 [GeForce Go 6800]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
	InputDevice     "Wiimote" "AlwaysCore"  # I tried to comment out this line with that section above
EndSection
Section "Module"
	Load		"glx"
EndSection
```

---

### Post by qwerdy on 2007-12-29
i dont know why your touchpad stopped working, but heres a ubuntu help page: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by davem2312 on 2007-12-31
So, I have done a little bit of looking, and it turns out that mouseemu is what breaks my touchpad.  When I uninstall it, the touchpad works perfectly, but then wminput will not run.  Does anybody have any suggestions as to how to work around this?

---

### Post by eFfeM on 2008-01-01
> **ACLBandit said:**
> So with this niftiness, my WiiMote now functions as a (somewhat sloppy) mouse. When the howto speaks of a sensor bar, does it, in fact, mean that interesting wireless Nyko one? If so, then I will have to buy one of those. Has anyone tested that bar with just a bluetooth receiver? I would like to make sure it will work correctly before I drop the cash for a sensor bar.

EDIT: Aha, I understand. Any sensor bar will work fine so long as the Wii is turned on. Wonderful. 

Question, though: Does the Nyko have the option to be turned on when the Wii is *not* on?

Also, my Wii remote, when using the infrared pointer, has no right click. The B button, for some reason, is a middle click. I find this to be kind of strange.

Those wireless sensor bars are just a bunch of infrared leds powered by batteries. The Wii needs not to be on to use this.

---

### Post by Jojan on 2008-01-01
):P I too have problem with the keys KEY_UP DOWN RIGHT and LEFT to get working. Did someone solve this? I've also have some trouble with some other buttons from [http://abstrakraft.org/cwiid/browser/trunk/wminput/action_enum.txt](http://abstrakraft.org/cwiid/browser/trunk/wminput/action_enum.txt) , for example the KEY_VOLUMEUP and KEY_VOLUMEDOWN.

> **eFfeM said:**
> Those wireless sensor bars are just a bunch of infrared leds powered by batteries. The Wii needs not to be on to use this.
The infrared sensor just steals energy from the Wii-console.

---

### Post by zeehio on 2008-01-01
> **davem2312 said:**
> So, I have done a little bit of looking, and it turns out that mouseemu is what breaks my touchpad.  When I uninstall it, the touchpad works perfectly, but then wminput will not run.  Does anybody have any suggestions as to how to work around this?

I had a similar problem, I think that the solution is:

Open the config file of mouseemu:
sudo gedit /etc/default/mouseemu

Change this:
#TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress
to this:
TYPING_BLOCK="-typing-block 000" # block mouse for 300ms after a keypress

This will help to all of you who have problems with the mouse and mouseemu, I think. I couldn't play UrbanTerror with mouseemu installed because my mouse was blocked when I pressed a key. Now I can play, because the "block time" is set to 0.

I'm Spanish, so forgive me if my English sounds a bit weird ;-)

PS: By the way, I'm stuck with the BTN_RIGHT problem, I'm not able to "right click" with the wiimote. Actually most of the "KEY_..." I've tried didn't do the expected thing, KEY_MINUS prints me an apostrophe, for example. I think (as someone has already said around here) that wminput doesn't use the X keycodes. It uses the kernel ?keysymbol?. To solve this, I'm following this route:
1. [http://abstrakraft.org/cwiid/wiki/wminput]("http://abstrakraft.org/cwiid/wiki/wminput") (The configuration Requirements section has the four steps)
2. [How to set up a Multimedia Keyboard]("http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys#Finding_raw_scan_codes_-_USB_keyboards") The section about "Finding RAW scan codes" seems to be the key
3. [How to retreive scancodes]("http://keytouch.sourceforge.net/howto_keyboard/node4.html") Here is where I am.

I think that I have to find the right /dev/input/eventX to find the scan codes to give them a "name" so I can map them in the wminput configuration. I hope someone can help or give a hint...

---

### Post by ACLBandit on 2008-01-02
> **zeehio said:**
> 
Open the config file of mouseemu:
sudo gedit /etc/default/mouseemu

Change this:
#TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress
to this:
TYPING_BLOCK="-typing-block 000" # block mouse for 300ms after a keypress


Interesting thing I've just discovered, following those steps, and perhaps this explains EVERYONE'S right click problems (perhaps not).

In the opened file, it says the following:

```

# Defaults for mouseemu initscript (/etc/init.d/mouseemu)
# These are the default values on PowerPC. On all other architectures
# middle and right click are disabled by default. 
# Key codes can be found in include/linux/input.h in the kernel headers
# or by using `showkey` in a console.

```

Hmm. Interesting. If someone can post back to explain this (btw, I'm on 32-bit ubuntu 7.10), and also tell me if it affects me, then that might be helpful.\

Also, as an afterthought, my new Nyko wireless sensor bar is AMAZING. ^_^

---

### Post by zeehio on 2008-01-03
Thank you! That's it!! I've got Right click!

First we open the mouseemu config file:
```

sudo gedit /etc/default/mouseemu
```
Mouseemu was made for PowerPC, that's why we have to change the default configuration:

Just add these two lines:
```

RIGHT_CLICK=BTN_RIGHT             # wiimote right click
MID_CLICK=BTN_MIDDLE              # wiimote middle click
```

Now, my /etc/default/mouseemu config file looks like:
```
# Defaults for mouseemu initscript (/etc/init.d/mouseemu)
# These are the default values on PowerPC. On all other architectures
# middle and right click are disabled by default. 
# Key codes can be found in include/linux/input.h in the kernel headers
# or by using `showkey` in a console.

#MID_CLICK="-middle 0 87"         # F11 with no modifier
#MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 88"        # F12 with no modifier
#RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
#SCROLL="-scroll 56"              # Alt key

RIGHT_CLICK=BTN_RIGHT             # wiimote right click
MID_CLICK=BTN_MIDDLE              # wiimote middle click
TYPING_BLOCK="-typing-block 000" # block mouse for 300ms after a keypress
```

mouseemu was written for mac users who don't have right click and have to emulate it.
By default, all non powerPC (we are x86) have disabled emulation of right click (because we already have our mouse),
As we want to emulate the right click with the wiimote, we must tell mouseemu that we want to emulate it. That's why we have to map it in this config file.

I did my best explaining me, I hope you could understand it :).

This solves all the right click problem, but doesn't solve the KY_MINUS that prints me an apostrophe. Anyway, I think that this is a minor problem.

Thanks!

---

### Post by savethewabbit on 2008-01-05
Thanks for this HowTo! It works perfectly for me. 
Only thing is I'd love it to go a little faster - the mouse pointer does move but it's quite slow to respond to movements. I was also wondering if it was possible to make it a little more sensitive to movements, as it seems to be connected to the speed. 

Anyone know how can I set this ? Thanks a whole lot.

---

### Post by zeehio on 2008-01-07
> **savethewabbit said:**
> Thanks for this HowTo! It works perfectly for me. 
Only thing is I'd love it to go a little faster - the mouse pointer does move but it's quite slow to respond to movements. I was also wondering if it was possible to make it a little more sensitive to movements, as it seems to be connected to the speed. 

Anyone know how can I set this ? Thanks a whole lot.

I don't know if I'll be able to help, but anyway: Do you move your mouse with the accelerometers or with the IR bar?

---

### Post by linkenobi on 2008-01-07
Huge problem :confused:

After editing the xorg.conf file i saved and then pressed ctrl+alt+backspace. The screen went to all black and only a blinking cursor was left. I waited a few minutes and tried to shut down or use ctrl+alt+backspace again but it didn't work so i had to hold the button till powerloss. I then started the laptop up again and it booted normally until the point at which the login screen would usually appear just the blinking cursor appeared. I don't know what to do. Anybody have any ideas? This probably has something to do with the xorg.conf file and there is probably a solution on this forum but after hours of searching i couldn't find any. Any help would be greatly appreciated.

Thank you,
linkenobi

---

### Post by leffect on 2008-01-08
Try pressing ctrl+alt+f1 to get to a terminal login. 

From there, you can replace the xorg.conf with a backup if you made one, use nano or vi to edit it to undo the changes.

If those don't work and you're desperate, do a sudo dpkg-reconfigure xserver-xorg to get the computer to recreate the xorg.conf from scratch. It will ask you a lot of questions if you do that though!

The first two shouldn't cause you any problems, but the last one could be fairly complicated - it's worth making a backup of your xorg.conf first, even if it doesn't work! Someone else may be able to give you a better solution as well.

---

### Post by linkenobi on 2008-01-09
> **leffect said:**
> Try pressing ctrl+alt+f1 to get to a terminal login. 

From there, you can replace the xorg.conf with a backup if you made one, use nano or vi to edit it to undo the changes.

If those don't work and you're desperate, do a sudo dpkg-reconfigure xserver-xorg to get the computer to recreate the xorg.conf from scratch. It will ask you a lot of questions if you do that though!

The first two shouldn't cause you any problems, but the last one could be fairly complicated - it's worth making a backup of your xorg.conf first, even if it doesn't work! Someone else may be able to give you a better solution as well.



Well i actually already fixed the problem.Let me rephrase that, it fixed itself. There was a bug and it actually wouldn't let me get into the terminal login. So i tried going in the "safe mode" and it wouldn't load correctly. So after about 5 or 6 restarts the safe mode finally works. I was about to reconfigure the xorg file but then wondered why the safe mode just started to work suddenly. So i restarted and went into the regular boot and in worked fine. I'm using a F572US Compaq laptop(which has deep problems with Ubuntu) and so far Gutsy has been the buggiest of all releases of tried. Thanks for the help though :)

On a actually thread related note. I got the whole Wiimote as a cursor thing to work and have been rather happy with it. Haven't noted a problem with the B as right mouse click thing. Everything seems to work fine but haven't been able to change some of the buttons. I want to change the number 1 and 2 buttons to Pause and Next. I found on the Cwiid website that you can supposedly put in FN_F12(which is my media key for next) as a key but it didn't work for me. If anyone else figures this out I'd be very appreciative :)

---

### Post by bmod on 2008-01-22
great!

---

### Post by segalion on 2008-01-22
Great howto!!!.
I´ve tested this with a trust usb bluetooth dongle, and works all in 5 minutes.

Now, I want to reach a static configuration to:
1. Emulate mouse with ir pointer
2. control my freevo with the wiimote (cursors and a few buttons...)
3. Play MarioKart64 with mupen64, with wiimote as a joystick (acceleration input), and two more buttons.

Has anybody a wminput config file to make all this (specially mupen64 joypad emulation)?.

Thanks in advance.

---

### Post by Chibi-Tatsu on 2008-01-25
The procedure worked until the 'make' step for the wiimote library.  I got this error:

/usr/bin/ld: /tmp/ccnHIRuz.o: relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/tmp/ccnHIRuz.o: could not read symbols: Bad value

And I'm not entirely sure what's going on.

EDIT: Nevermind; with some research, figured out it was a problem with using a 64-bit architecture.

[http://www.gentoo.org/proj/en/base/amd64/howtos/index.xml?part=1&chap=3](http://www.gentoo.org/proj/en/base/amd64/howtos/index.xml?part=1&chap=3)

Not entirely sure how to fix it still, but it's identified at least

EDIT: nevermind again; it works now (installed the packages found in symantic with a "wii" search)

---

### Post by motin on 2008-01-26
Any progress in making the Wiimot ir_ptr work on the second head in a Xinerama dual head display configuration?

The Gutsy version is 0.5.x, but using prevu it is quite easy to build the 0.6.00-3 version (from Debian testing):

```
prevu http://ftp.de.debian.org/debian/pool/main/c/cwiid/cwiid_0.6.00-3.dsc
```

Haven't tried it yet, but thought I would mention that it backports fine.

---

### Post by motin on 2008-01-26
> **leffect said:**
> Now to reload xorg.conf by restarting X. (if there's a better way to reload it, I'd appreciate it if someone told me!) Make sure you haven't got anything unsaved, then press ctrl+alt+backspace. This will drop you back at a login screen, so make sure you know how to get back here!

> **leffect said:**
> Try pressing ctrl+alt+f1 to get to a terminal login. 

From there, you can replace the xorg.conf with a backup if you made one, use nano or vi to edit it to undo the changes.

If those don't work and you're desperate, do a sudo dpkg-reconfigure xserver-xorg to get the computer to recreate the xorg.conf from scratch. It will ask you a lot of questions if you do that though!

The first two shouldn't cause you any problems, but the last one could be fairly complicated - it's worth making a backup of your xorg.conf first, even if it doesn't work! Someone else may be able to give you a better solution as well.

[SIZE="3"]**There is a much easier, safe and fully graphical way of doing this for which I just wrote a Howto about (as a thank you for your great tutorial in the first place): [http://ubuntuforums.org/showthread.php?p=4211618](http://ubuntuforums.org/showthread.php?p=4211618)**[/SIZE]

---

### Post by segalion on 2008-01-29
This is my wminput config to use the wiimote as a wheel for Mupen64 MariosKart:

```
# wheel
# Plugin.acc.X = Y = up&down in MarioKart (escalado x5)
# Plugin.acc.Y = X = left-right (escalado x2)

Plugin.acc.X = ABS_Y
Plugin.acc.Y = ABS_X
Plugin.acc.X_Scale = 5.0
Plugin.acc.Y_Scale = 2.0

# Plugin.acc.Roll = ABS_X
# Plugin.acc.Roll_Scale = 2.0
# Plugin.acc.Pitch = -ABS_Y
# Plugin.acc.Pitch_Scale = 2.0

Wiimote.Up = BTN_0
Wiimote.Down = BTN_1
Wiimote.Left = BTN_2
Wiimote.Right = BTN_3
Wiimote.A = BTN_A
Wiimote.B = BTN_B
Wiimote.Minus = BTN_SELECT
Wiimote.Plus = BTN_START
Wiimote.Home = BTN_MODE
Wiimote.1 = BTN_Y
Wiimote.2 = BTN_X


```

You have to put this text in $HOME/.cwiid/wminput/wheel   file
and launch with ```
$wminput -c wheel
```
Mupen64 blight_input joystick plugin recognice Wiimote as a standar joypad and you can play games using wiimote as a wheel

---

### Post by nfox on 2008-01-31
Hello all,

I've got my Wiimote working except for a couple of (user?) issues with some buttons. I want multiple Wiimotes to work at once.
Does anyone have experience with MPX (Multi-pointer Xserver) and CWiiD?
I do not want to put a replacement Xserver but it looks promising. I would like to have multiplayer games on my PC with multiple Wiimotes.

If you don't know MPX, watch this:
[http://www.youtube.com/watch?v=W0iANEFf6WI](http://www.youtube.com/watch?v=W0iANEFf6WI)

Now how to get that to work with CWiiD? I don't see anything about multiple devices at all.

---

### Post by qwerdy on 2008-02-01
> **segalion said:**
> This is my wminput config to use the wiimote as a wheel for Mupen64 MariosKart:

```
# wheel
# Plugin.acc.X = Y = up&down in MarioKart (escalado x5)
# Plugin.acc.Y = X = left-right (escalado x2)

Plugin.acc.X = ABS_Y
Plugin.acc.Y = ABS_X
Plugin.acc.X_Scale = 5.0
Plugin.acc.Y_Scale = 2.0

# Plugin.acc.Roll = ABS_X
# Plugin.acc.Roll_Scale = 2.0
# Plugin.acc.Pitch = -ABS_Y
# Plugin.acc.Pitch_Scale = 2.0

Wiimote.Up = BTN_0
Wiimote.Down = BTN_1
Wiimote.Left = BTN_2
Wiimote.Right = BTN_3
Wiimote.A = BTN_A
Wiimote.B = BTN_B
Wiimote.Minus = BTN_SELECT
Wiimote.Plus = BTN_START
Wiimote.Home = BTN_MODE
Wiimote.1 = BTN_Y
Wiimote.2 = BTN_X


```

You have to put this text in $HOME/.cwiid/wminput/wheel   file
and launch with ```
$wminput -c wheel
```
Mupen64 blight_input joystick plugin recognice Wiimote as a standar joypad and you can play games using wiimote as a wheel
EDIT: nevermind, had to remove "InputDevice     "Wiimote" "AlwaysCore"" to get it to work like a joystick and not a mouse.
damn goldeneye was har with a wiimote to aim with :p

---

### Post by nfox on 2008-02-02
> **Damwid said:**
> Seems the libwiimote library is unnecessary, I got cwiid work without libwiimote installed. 

I also found another weird problem:
when run wminput with "-c buttons" option, all four direction buttons work well, while other buttons don't. without this option, acc_ptr config is used, button A and B work as left/right mouse button, but all direction buttons don't work anymore.

I dig into the source and found wminput have nothing to do with X, it just use kernel uinput driver to emulate an input device by writing the events into /dev/input/uinput. By adding the debug output, I found the same data are sent to /dev/input/uinput for a given button in these two cases, but the behavior is totally different. I was confused by this, maybe a input module bug?

I will continue debugging on this, since the keycode read from wiimote is correct, this would be a big problem to fix.










Let me know how that goes. I have the same problem. I want the acceleration for mouse and the rest of the buttons...

Would anyone know how to use the nunchuk joystick as mouse (or the d-pad)? I see nothing of this.

---

### Post by motin on 2008-02-03
> **nfox said:**
> Hello all,

I've got my Wiimote working except for a couple of (user?) issues with some buttons. I want multiple Wiimotes to work at once.
Does anyone have experience with MPX (Multi-pointer Xserver) and CWiiD?
I do not want to put a replacement Xserver but it looks promising. I would like to have multiplayer games on my PC with multiple Wiimotes.

If you don't know MPX, watch this:
[http://www.youtube.com/watch?v=W0iANEFf6WI](http://www.youtube.com/watch?v=W0iANEFf6WI)

Now how to get that to work with CWiiD? I don't see anything about multiple devices at all.

I am longing to do the same thing. The MPX developer has written a simple (without IR support yet) _native_ driver for X (not evdev-managed). Not sure if there is a significant advantage with this approach. This and many other questions have I asked him general questions about MPX and the Wiimotes for which he has been kind to promptly reply to. I hope to be able to share the email discussion on this thread if he agrees to it.

---

### Post by nfox on 2008-02-04
About MPX and his driver, 

I've been asking him here and there but I've got issues with compiling MPX. Something to do with it not recognizing xorg-xserver when it wants xserver-xorg or something. I tried to play with the name a bit but big zero to that...

His wiimote driver might work but I haven't seen what I'm after with its features. Call me new-fashion but I like simple configs. Add to this the whole point is to have multiple wiimotes running mice and keyboards which means I still need MPX installed.



**Here's the best workaround I could find with CWiiD:**

Map buttons to the keypad and make one of them (Home) the numlock key. This doubles the amount of buttons available. Plus you can set the mouse to move with the keypad which is mapped to the Wiimote's D-pad. 
Then you get buttons and mouse albeit D-pad accuracy.

Also, make sure wminput doesn't need sudo and you can set another button to swap profiles. So you can have your gampad layout, press a button to load a new config, press 1+2 and then wave around the mouse. 

This about kills the wow-factor and you still need to deal with the dreaded 250ms delay between input. 


Maybe I'll steer away from CWiiD and find something better. Any other ideas, please share.

---

### Post by motin on 2008-02-04
Peter Hutterer, the MPX developer just got back and it looks like his native driver is an alternative, but not necessary way to get it to work with MPX. As long as it (or evdev) is considered as a mouse/keyboard by X it will work in MPX as a separate pointer. My fear however is that wminput is designed to only use the evdev device for key mappings and not for the pointer movement - and thus invalidates this approach. 

What we need is some kind of discussion board for the target of making it possible to use several wiimotes controlling a pointer each at once. The end solution would probably need to consist of:

1. MPX
2. A native Wiimote pointer device driver - OR Multiple uinput / wminput pointer devices support

The best would be if we could hear what Peter (MPX) and Donnie (wminput) had to say about this. I have emailed them separately and will next time propose that they discuss this in an appropriate forum.

---

### Post by cl_audio on 2008-02-04
Got it working nice! 

Using TrendNet 101UB dongle...



another issue has arrived now though, my touchpad is no longer working.[SOLVED]

-Change the placement of the wiimote code in the xorg.conf file to right under the touchpad declaration, should work!

---

### Post by cirpo on 2008-02-08
hi,
thanks for the howto, my wiimote works.
But i don't understand this:
if i run wminput the wiimote works, but if i specify 
```

cirpo@nestore:/etc/cwiid/wminput$ sudo wminput -c buttons
Put Wiimote in discoverable mode now (press 1+2)...
Ready.

```

only the directional buttons works...

why??

thanks

cirpo

---

### Post by nfox on 2008-02-09
So,

 I am thoroughly disappointed with the setup here and every day that I have only a mouse or keyboard support is a day that the 250 ms delay for input makes me want to punch small ceramic gnomes in the face.

Who is able to wave the remote as a mouse, press A + B as mouse buttons AND use the other buttons at the same time?
I expect that no one can.... what do we do?



I know this is a CWiiD forum going and maybe we need a new thread but has anybody used MPX's Wiimote driver? I can not get it to configure. 

It's mad about not finding 'xorg-server' and I don't know how to override the environment variables to point to it.

---

### Post by motin on 2008-02-09
> **nfox said:**
> So,

 I am thoroughly disappointed with the setup here and every day that I have only a mouse or keyboard support is a day that the 250 ms delay for input makes me want to punch small ceramic gnomes in the face.

Who is able to wave the remote as a mouse, press A + B as mouse buttons AND use the other buttons at the same time?
I expect that no one can.... what do we do?

I know this is a CWiiD forum going and maybe we need a new thread but has anybody used MPX's Wiimote driver? I can not get it to configure. 

It's mad about not finding 'xorg-server' and I don't know how to override the environment variables to point to it.

I can wave the mouse around and left+middle click (right click does not work any longer) and use the directional buttons and A+ B, volume up/down + home buttons at the same time. 

So currently, I can get my desktop on the wall using a projector and then use the wiimote to start a nes/snes,neogeo,segams or psx emulator + select and start a game. Then I tilt the wiimote over and use it as a simple gamepad. This is enough for all NES games and quite a few SNES + Sega MS games as well.

Here is my config:

```
#IR pointer 

Plugin.ir_ptr.X = ~ABS_X
Plugin.ir_ptr.Y = ~ABS_Y

#buttons

Wiimote.A               = BTN_LEFT
Wiimote.B               = BTN_RIGHT
Wiimote.Up              = KEY_KATAKANA
Wiimote.Down            = KEY_KPENTER
Wiimote.Left            = KEY_HENKAN
Wiimote.Right           = KEY_MUHENKAN
Wiimote.Minus           = KEY_BACK
Wiimote.Plus            = KEY_FORWARD
Wiimote.Home            = KEY_HOME
Wiimote.1               = KEY_SLASH
Wiimote.2               = KEY_SPACE

```

The next step is to combine cwiid and MPX in order to be able to use several pointer devices and keyboards simultaneously. I am running a conversation with Peter Hutterer (mpx) and Donnie Smith (cwiid) about this currently and will happily share the conversations in this thread soon. 

Cheers!

---

### Post by Clockware on 2008-02-12
I just have a problem with my Wiimote, Gutsy and CWiid. It's a little bit strange...I just followed the Wiki Guide! ;)

> 
**sudo wminput**
Put Wiimote in discoverable mode now (press 1+2)...
Socket connect error (control channel)
unable to connect
The Bluetooth adapter is plugged and working. I already used that for connecting the Wiimote using the WiiRemoteJ java library and all worked fine!

> 
**uname -a:**
2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

**lsmod:**
Module                  Size  Used by
uinput                 10368  0 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
hci_usb                18332  2 
bluetooth              57060  7 rfcomm,l2cap,hci_usb
joydev                 11328  0 
evdev                  11136  6 
reiserfs              248704  2 
usbhid                 29536  0 
hid                    28928  1 usbhid
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  5 hci_usb,usbhid,ehci_hcd,uhci_hcd
...

**lsusb:**
Bus 002 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
The **lswm**'s output is the correct wiimote's baddr. Where I am wrong?! :)

Thanks
Valerio

---

### Post by nfox on 2008-02-12
Clockware, 

Not sure what the trouble is. You say that the Java one worked fine but have you had any other bluetooth devices working either? There's a lot to configure, I'll assume your bluetooth setup is a-okay so you need to break the problem down.

I'll try to help but I'll need a little more info. 
First, don't run wminput with sudo. That alone could be restricted depending on your setup. Befor anything, do this:

```
sudo sh -c 'echo "KERNEL==\"uinput\", GROUP=\"admin\"" > /etc/udev/rules.d/50-cwiid-input.rules'
/etc/init.d/udev restart
```

And do you have all of these packages installed?
libcwiid0, lswm, wmgui and wminput

Also, what does wmgui tell you? Are you getting any results there?

I followed this with meager results:
[COLOR="Blue"][https://help.ubuntu.com/community/CWiiD]("https://help.ubuntu.com/community/CWiiD")[/COLOR]

Did you install CWiiD through the repositories or from the source?


P.S.
We should probably be moving to a new thread for general Wiimote connectivity. This CWiiD deal is less than adequate but an awesome, light framework. Please tell me about the WiiRemoteJ. I never heard of it and since I suck at Java, can you tell me how you ran it? I use JSP-based Java at work so I should be able to understand the procedure-- call me lazy. I like APIs, sounds like a good base to start with. 

I'd love to hear how you got it running..... Thanks

---

### Post by Clockware on 2008-02-13
> **nfox said:**
> Clockware, 

Not sure what the trouble is. You say that the Java one worked fine but have you had any other bluetooth devices working either? There's a lot to configure, I'll assume your bluetooth setup is a-okay so you need to break the problem down.


Yes, I tried different BT devices but didn't work neither with the java package.

> 
I'll try to help but I'll need a little more info. 

```
sudo sh -c 'echo "KERNEL==\"uinput\", GROUP=\"admin\"" > /etc/udev/rules.d/50-cwiid-input.rules'
/etc/init.d/udev restart
```


I followed the wiki guide, so I added this rulez. However running wminput after the startup prints out this message:
:~$ wminput 
unable to open uinput

So I run modprobe to loading the uinput module. (it doesn't seem to be loaded automatically)

> 
And do you have all of these packages installed?
libcwiid0, lswm, wmgui and wminput

Also, what does wmgui tell you? Are you getting any results there?
Did you install CWiiD through the repositories or from the source?


Well, these packages was installed by apt-get under Ubuntu Gutsy 7.10, so I didn't compiled the sources. :)

> 
P.S.
We should probably be moving to a new thread for general Wiimote connectivity. This CWiiD deal is less than adequate but an awesome, light framework. Please tell me about the WiiRemoteJ. I never heard of it and since I suck at Java, can you tell me how you ran it? I use JSP-based Java at work so I should be able to understand the procedure-- call me lazy. I like APIs, sounds like a good base to start with. 

I'd love to hear how you got it running..... Thanks

Nice, probably in April I'm going to prepare a JUG meeting on this topic!
Using WiiRemoteJ is quite simple, you need AvetanaBT library and BlueZ linux-bluetooth stack up and running to run the sample.

[http://www.wiili.org/index.php/WiiremoteJ](http://www.wiili.org/index.php/WiiremoteJ)  (for download packages)

You just need to compile the AvetanaBT and put the jar inside your classpath (the wiki suggest inside JRE/ext/...)

Thanks,
Clockware

PS: let me hear about it...! ;)

---

### Post by nfox on 2008-02-13
About other BT devices, do they work with software other than the Java package? 

"So I run modprobe to loading the uinput module. (it doesn't seem to be loaded automatically)"
    ```
echo "uinput" >> /etc/modules
```

How's wmgui looking? If that's showing no input than I don't think it's a CWiiD problem, maybe a driver  issue.


So, got the wiiremotej going. Here's a fun fact: my java setup is [insert something bad and offensive] so I can't even play with it. 

Could you tell me what the feedback/ input delay is like and if you've had any problems with it? I'd have to reinstall java jdk and abandon my current setup like adopted kids at airports.
Thanks

---

### Post by Clockware on 2008-02-13
> **nfox said:**
> About other BT devices, do they work with software other than the Java package?


The other BT dongles worked well with the Gnome-Bluetooth utilities but not with the java package. I used them with OBEX file sharing so they did their homeworks.

> 
How's wmgui looking? If that's showing no input than I don't think it's a CWiiD problem, maybe a driver  issue.


The wmgui is loading well but when I start the Connect procedure an error message is shown: "Unable to Connect". The same is printed out in the terminal if I run the wmgui from there. (the error message shown in the console is the same I noticed in the first post)

> 
So, got the wiiremotej going. Here's a fun fact: my java setup is [insert something bad and offensive] so I can't even play with it. 

Could you tell me what the feedback/ input delay is like and if you've had any problems with it? I'd have to reinstall java jdk and abandon my current setup like adopted kids at airports.
Thanks

The feedback is good. It seems to be the same of the other frameworks - written in various languages. Probably because the bluetooth communication levels the performances. In my opinion the WiiRemoteJ library is a very flexible way to use your wiimote. You just need an JSR-082 (Java Bluetooth API) implementation and a lot of imagination! :)

However, start from a new fresh installation of a JDK (version 6 if possible, performance issues) and install AvetanaBT (the jre/ext dir is appropriate). If you run your program from an IDE, like Eclipse, you just need to configure the new JVM and the IDE will think about the correct JVM invocation. (from terminal just set the correct variables and the game is up and running) :)

Thanks,
Clockware

---

### Post by Stingray8989 on 2008-02-14
I would like to make it possible to use the IR as a mouse (which I already got working), and make jerking motions on the accelerometers emulate certain keys. For instance- jerk wiimote up (acc pitch) would result in a space key emulation (Good for first person shooter games to jump with).

Also, does anyone have a link to a tutorial which would tell all the code options for different keys? That way I could make multiple wiimote profiles and know what I'm actually doing.

---

### Post by Stingray8989 on 2008-02-14
Oh, and also the coding for the wiimote's input as well.

---

### Post by nfox on 2008-02-14
Clockware,
Thanks for the info. I'm busy but when I get a chance, I'll try out the Java app-- it sounds better than what CWiiD's offering. I'll post an update.

Stingray8989,
Look no further than the install directory for this file:
action_enum.txt
Has it all mapped according to the ASCII (right?) key codes. Check the examples layouts too for reference. 

If that isn't clear enough, head here:
[http://www.wiili.org/index.php/Wminput]("http://www.wiili.org/index.php/Wminput")

---

### Post by Stingray8989 on 2008-02-16
thanks, but I couldnt find that file in the install directory. The other link there looks quite helpful however

---

### Post by Stingray8989 on 2008-02-16
I've run into a problem. No matter what I put for wiimote.up,down,left,right,home,plus,minus,&B they do nothing. Except up takes a screenshot, but I never told it to do that. Also I couldnt figure out what to do to make accelerometers emulate key strokes. It would make no sense to just put 'plugin.acc.Y = KEY_SPACE'. I would have to put some type of argument for what value the pitch must be (or better how sudden the pitch is shifted) to make the key event. any ideas?

---

### Post by Triggerhapp on 2008-02-18
Right. Ive spent all night thinking this one up/making it work/tweaking xorg.conf  ...

What I wanted to do was set buttons on my Wiimote to, for example, use Mouse buttons OTHER than left and middle/right (this problem has been addressed alot from what I see)
Heres the steps I took from Multiple sources, most of which have been lost in my history, thanks to the fact that I find Ctrl-alt-bkspace to be the best method of testing.

First, Assign some higher "Button numbers" to Keys. 
From input.h
```
#define BTN_LEFT                0x110
#define BTN_RIGHT               0x111
#define BTN_MIDDLE              0x112
#define BTN_SIDE                0x113
#define BTN_EXTRA               0x114
#define BTN_FORWARD             0x115
#define BTN_BACK                0x116
#define BTN_TASK                0x117
```
If you dont know C... DONT PANIC
It starts nice and simple, left click, right click. Middle.
If you use a scroll wheel, ignore side and extra (Naming convention kinda fell over here IMO), and I'll assume if you use 2 scroll wheels also ignore Forward and back... not tested with anything but 1 scroll wheel :P.

Heres what I did next. Try to use them in my ir_ptr config file... 
```
Wiimote.Plus            = BTN_FORWARD
Wiimote.Minus           = BTN_BACK
```

I ran up the program and realised that this didnt do anything (Doesnt it feel great when that happens!?)

I then did a few random checks on google (3am, you kinda lose where you were aiming and go on all the tangents you can find)
I found some interesting xorg.conf settings that made the big difference

```
Section "InputDevice"
        Identifier      "Wiimote"
        Driver          "evdev"
        Option          "Name"  "Nintendo Wiimote"
        Option          "Emulate3Buttons"       "true"
        Option         "Buttons" "7"
        Option          "ButtonMapping"         "1 2 3 6 7"
EndSection
```

Again, 4 and 5 are my scroll wheel, and are ommited from the list. Your milage may vary.
I *also* ran this line, not sure if it DID anything, but if this so far doesnt work, try it.

```
xmodmap -e "pointer = 1 2 3 6 7 8 9 10 11 12 4 5" &
```
From the documentation i read, all scroll wheel related buttons MUST be placed at the end of the list of numbers.

I did my usual saving and Ctrl-alt-bkspace and got back to find that I could now use all 3 usual buttons on my normal mouse and draw in fire with my Plus button :D

What a waste of a good few hours just for something I wont use XD

Anyways, hope this might be of slight use to someone out there who needs more mouse buttons on thier wiimote.

Any questions/comments/flames let me know, Im rather new here so I expect some kind of criticism before long ;)

Edit: Im sure I shouldnt be putting this in as a SIDE NOTE but heres something I found.
My wiimote comes up happily in "hcitool scan" but when i connect just with "wminput" it wont see it, I always have to specify the MAC address that hcitool gives me. Just a heads up incase anyone else is finding they cant connect for "No Reason"

---

### Post by danstah on 2008-02-23
Maybe i am missing something here but i cannot get my right click to work on my wiimote.. Does anyone have a solution to this?

---

### Post by nfox on 2008-02-24
Clockware,
I have WiiRemoteJ and the needed bluetooth input packages.
Avetana is in "/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/ext"
The docs say "Add WiiRemoteJ.jar to your CLASSPATH system variable. "

How do I get it to run and subsequently work? Am I to 'javac WiiRemote.jar' from the directory? 


Triggerhapp,
I'm going to have to look at the '.h' file about mapping the buttons manually. 
My issue wasn't the mouse-- it's that the mouse+gyro don't allow any other buttons to work.

danstah,
You can get the other buttons to work? As I stated above/before, I can not use all buttons on all profiles. This app is extremely fussy about combinations of keys (at least for me) so I would suggest trying other profiles first (i.e 'wminput -c buttons'). 
In short, if right mouse is your only problem, you've fared better than me.





And has anybody had any input slowdown with this installed? Copy+paste freezes my mouse for a split second but only after I've installed wminput. I uninstalled+purged it and now I have to live with this. It's like AIDS but less fun. Any solutions for that would be appreciated.

---

### Post by Triggerhapp on 2008-02-24
Try the commands I posted (if you havnt already), minus adding the usage of futher mouse buttons.

---

### Post by nanite on 2008-02-24
Hey Valerio. I'm getting exactly the same problem as you. *Exactly* the same messages from uname, lsusb, and wminput. "Socket connect error (control channel)" whaaaaaaaaaaaaaaaaaaat? This is bugging me, I can't find anyone else with this problem except you!
-Mark

> **Clockware said:**
> I just have a problem with my Wiimote, Gutsy and CWiid. It's a little bit strange...I just followed the Wiki Guide! ;)

The Bluetooth adapter is plugged and working. I already used that for connecting the Wiimote using the WiiRemoteJ java library and all worked fine!

The **lswm**'s output is the correct wiimote's baddr. Where I am wrong?! :)

Thanks
Valerio

---

### Post by durand on 2008-02-25
Hi,

I just tried Cwiid and the gui works but when I run sudo wminput, I get this error:

```
error on uinput ioctl
```
I'm running this on the ps3 so maybe there are some 64bit compatibility problems?

Found a website from someone who's using the wiimote on a ps3 but I don't have a clue how to patch python and rebuild...

[http://www.keshi.org/moin/PS3/WiiRemote](http://www.keshi.org/moin/PS3/WiiRemote)

Any ideas? Thanks in advance.

---

### Post by adam_r on 2008-03-04
can you use the wiimote as a mouse without the an IR bar? with bluetooth?

---

### Post by Triggerhapp on 2008-03-04
Did you even try? XD yes thats the option by default with Cwiid, you need to specify with it if you want the bar. you tilt (anti)clockwise for left/right and forward/back for up/down

Personally I prefer the bar and still need to get around to making my own personal bar (looking into hearing aid batterys to make a miniture single LED box)

---

### Post by shadowhywind on 2008-03-15
hay all first off, THANKS for the guide. I got my wiimote connected, and with the Z+C buttons on the nunchuk working. However I do have a question. Has anyone been able to get the directional/joystick on the nunchuk to work? If so can you post your config. I have been struggling to get mine to work and have gotten no where. So any help would be great Thanks!

---

### Post by asforme on 2008-03-15
> **durand said:**
> Hi,

I just tried Cwiid and the gui works but when I run sudo wminput, I get this error:

```
error on uinput ioctl
```
I'm running this on the ps3 so maybe there are some 64bit compatibility problems?

Found a website from someone who's using the wiimote on a ps3 but I don't have a clue how to patch python and rebuild...

[http://www.keshi.org/moin/PS3/WiiRemote](http://www.keshi.org/moin/PS3/WiiRemote)

Any ideas? Thanks in advance.

Try to run a
```
sudo modprobe uinput
```

If that doesn't work you may want to install the hardy package from packages.ubuntu.com (you'll have to download several dependencies).  It was the only way I could get it working in 64bit.

How ironic and awesome it would be to use a wiimote to control a ps3.  :lolflag:

---

### Post by Garf on 2008-03-18
Hi guys... 

I can't get my wiimote to connect...

I am using Gutsy, so I did sudo apt-get install libcwiid0 lswm wmgui wminput

I opened up the GUI an went to File -> Connect and followed the instructions...

But all I get is "Unable to connect"

When I did "sudo wminput", I got the same thing 
  Socket connect error (control channel)
  unable to connect

I know that my bluetooth dongle can see the wiimote because I did hcitool scan and got this:

Scanning ...
        00:9A:75:1D:65:8E       n/a
        00:1E:35:1D:65:8E       Nintendo RVL-CNT-01
        00:15:DE:E2:DE:E4       Nokia 6280

I also put in the Input device stuff into the xorg.conf

So any idea's?

---

### Post by Triggerhapp on 2008-03-18
Garf, when running the command, specify your Nintendo Wiimote by using the same address that hciscan tells you it is... I found that is the only way to get my one to work. Let me know how that goes.

---

### Post by nfox on 2008-03-18
garf,

try the basics first-- does CWiiD's GUI connect?

do this:
```
hcitool --connect XX:XX:XX:XX:XX:XX
```
but substituting the MAC address of you're mouse. 

If hcitool can connect you know where the problem is

---

### Post by Garf on 2008-03-19
I just gave that a try... this is what happend

hcitool --connect 00:1E:35:1D:65:8E
hcitool: unrecognized option `--connect'

---

### Post by Garf on 2008-03-19
> **Triggerhapp said:**
> Garf, when running the command, specify your Nintendo Wiimote by using the same address that hciscan tells you it is... I found that is the only way to get my one to work. Let me know how that goes.

Cool, I got it to connect...
Now to figure out how to make it control the mouse...

---

### Post by Triggerhapp on 2008-03-19
Tilt it, if you use it normally...
The better option is a little more akward till you have an IR bar seperated from the Wii.

Connect your Wiimote using the command ```
wmimput -c ir_ptr xx:xx:xx:xx:xx:xx
``` im sure you get the picture by now :P
Then turn on your Wii, and move the IR bar to be just above or below the screen.
Then, pointing works fine.

This also works with open flames (ie candles) or IR Led's, which are rather easier.

The problem with the Wii is it will automatically (and alot faster than you PC!) pair with your Wiimote. XD

---

### Post by mchiareli on 2008-03-19
hi, when i try the command:

#hcitool scan

i get the message:

00:1B:7A:E8:D7:03       n/a

and i cant to connect =(

you can help me?

---

### Post by Triggerhapp on 2008-03-20
run, and give us the output of ```
wminput (Mac address)
``` and ```
wmgui
``` (although the latter will not print much output, tell us if it'll let you connect)

Wait, I just re-read, and if im not mistaken, You cant find your Mac address to start with?
in that case Press 1+2 on the Wiimote, then scan a moment after, while the Wiimote lights are flashing.

---

### Post by qwerdy on 2008-04-07
Is it possible to make the accelerometers emulate key strokes with cwiid?

i know xwii have a flick option, but i want to be able to bind different keys to different flicks, if you understand?

edit: or is there some other drivers that allow this?

---

### Post by nfox on 2008-04-07
qwerdy:
There is no native way of doing that (as far as I'm aware) with CWiiD. I would not recommend you go through the code to make it possible unless you know exactly what you're doing. I don't and I haven't found a way.

As far as alternatives, there is always WiiRemoteJ which, if you're good at Java (or have some willingness to pick up the rather intuitive design methods) would be relatively simple to modify for your needs. 

For instance, without looking at a single line of it's code, I would assume there would be a central axis component that could handle a few of the following pseudo-code lines:

if (axis.equals("leftdown") { return asc("13"); }

of course that's loose but very possible to make your own keymaps. 


I would certainly love to figure it out with someone if there was interest in a unified configuration for Wiimotes. If you've been following the post, you may have noticed I tried a bunch of things out and never was overly impressed and currently I don't even bother with it. It's like the adopted kid you thought you could cheer at the little league game but after a while you just give up on.

---

### Post by durand on 2008-04-08
I think thats going to get pretty complicated. You would probably need to program something using the bindings for C, java, etc. If you find anything useful, please let us know :)

---

### Post by nfox on 2008-04-09
Or even better, why don't we all switch to Windows and use the existing drivers?



I think the best bet would be to wait for the technology to mature or be proactive. The best solution for the user may be to use CWiiD/etc and keybind through your desktop manager like KDE or Gnome. At least in terms of getting the desired result quickly.

As for hand gestures for hotkeys, just imagine trying to account for thresholds and your own orientation. Suppose you want to tap down the Wiimote like a hammer. Would you use relative acceleration and at what point would it trigger? Would you use absolute positioning? Coding nightmare.

I think, right now, the person who knows Xserver input handling would be very successful at getting things to work correctly. That clearly isn't me and I don't think anyone on this thread is either. I hate to throw the pessimistic card but I think you will have to live with the existing drivers and your mods to them or wait a bit. I hope I'm wrong.

---

### Post by qwerdy on 2008-04-10
in windows i got i working nearly exactly as i wanted, using GlovePIE. 
But i have mythbuntu on my htpc were i was going to use it. I'm using XWII right now, because of the profile changer and the flick ability.

Guess i have to wait for OpenPIE to get what i want in linux.

---

### Post by audwan on 2008-04-20
I managed to get everything working except the IR part.

I compiled and installed libwiimote-0.4 and cwiid-0.6.00 on my Ubuntu 8.04 box, and followed the instructions from the Wiki, including the xorg.conf part.

When i run wmgui i can see the dots from two candles I lit, but when I run "wminput -c ir_ptr", only the buttons work and the cursor won't move. I see the light on the Wiimote flashing when I point it at the candles though, so I guess it might be something with my xorg configuration.

My Xorg.log.0 contains these lines:
[snip]
(EE) Wiimote: No Device specified.
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Wiimote"
(WW) Configured Mouse: No Device specified, looking for one...
[/snip]

Is this normal? Any ideas would be deeply appreciated, 'cause I'd love to get this working with Elisa media center.

---

### Post by intense.ego on 2008-04-20
I have a few questions (I did not read through the whole thread so sorry if I am repeating anything):

1) Can this fully work without the sensor bar (i.e. only bluetooth)?

2) Is there a more up to date guide? this one was last edited in September

---

### Post by audwan on 2008-04-21
> **intense.ego said:**
> I have a few questions (I did not read through the whole thread so sorry if I am repeating anything)

1) Can this fully work without the sensor bar (i.e. only bluetooth)?:

If you just run wminput, you can tilt the Wiimote to move the cursor, so it doesn't require a sensor bar.

If you want to use it as a mouse (i.e. pointing it at the screen to move the cursor), you will need some kind of IR source. Some use candles or homebred IR LED solutions. All those should work if they emit enough light for the Wiimote camera.

> **intense.ego said:**
> 2) Is there a more up to date guide? this one was last edited in September

I believe this guide still applies, but you could try out WMD as well. I'm not sure which one is the best, but i got WMD running with IR, allthough it makes Elisa run slow on video playback. Seems like it consumes a great amount of resources, but it might just be my bad.

Try searching in the forums or Google for WMD, Wiimote and CWiiD for more info.

---

### Post by nieekou on 2008-04-27
ok, i'm on a fresh 8.04 ubuntu install, i installed these

```
sudo apt-get install libcwiid1 lswm wmgui wminput
```

as the guide said.
the wiimote connects with no problem, the wmgui works out of the box (bluetooth only, i haven't tested ir yet).

at first the wminput refused to run, now it runs just fine, the bluetooth mouse works. now i just want to load custom button maps, but i can't find where wminput is installed, so that i can save my maps in! argh! it's not in /usr/local/etc/cwiid/wminput, neither in ~/.wminput. i used search for it but it didn't find anything. i tried ```
wminput ~/home/Desktop/custm
``` which is the file of my custom map but it still loaded the default one. any help?

---

### Post by Schendje on 2008-04-27
> **audwan said:**
> I managed to get everything working except the IR part.

[...]

Is this normal? Any ideas would be deeply appreciated, 'cause I'd love to get this working with Elisa media center.

Hi audwan!

I had exactly the same problem. Everything worked except for the IR part. I could see it in wmgui though. I finally solved the problem when I changed 

```
Plugin.ir_ptr.X	= ~ABS_X
Plugin.ir_ptr.Y	= ~ABS_Y
```

In the ir_ptr file, to:

```
Plugin.ir_ptr.X	= ABS_X
Plugin.ir_ptr.Y	= ABS_Y
```

So, removing the "~". And now it works! I hope this helps. :)

---

### Post by intense.ego on 2008-04-27
> **audwan said:**
> If you just run wminput, you can tilt the Wiimote to move the cursor, so it doesn't require a sensor bar.

If you want to use it as a mouse (i.e. pointing it at the screen to move the cursor), you will need some kind of IR source. Some use candles or homebred IR LED solutions. All those should work if they emit enough light for the Wiimote camera.



I believe this guide still applies, but you could try out WMD as well. I'm not sure which one is the best, but i got WMD running with IR, allthough it makes Elisa run slow on video playback. Seems like it consumes a great amount of resources, but it might just be my bad.

Try searching in the forums or Google for WMD, Wiimote and CWiiD for more info.

Follow up question: If I got a wireless IR sensor bar, would I need bluetooth at all for the mouse to work? I don't have bluetooth built in and have to use an ugly adapter that sticks out of the usb slot, so i'd prefer not to need it.

---

### Post by Triggerhapp on 2008-04-27
> **intense.ego said:**
> Follow up question: If I got a wireless IR sensor bar, would I need bluetooth at all for the mouse to work? I don't have bluetooth built in and have to use an ugly adapter that sticks out of the usb slot, so i'd prefer not to need it.

YEP! the "bar" is just infrared LED's. thats all it is.
The Wiimote sees the light, and uses the lights position to position the mouse on screen. The Wiimote uses a camera, by the way.
You will always need bluetooth.

---

### Post by intense.ego on 2008-04-28
> **Triggerhapp said:**
> YEP! the "bar" is just infrared LED's. thats all it is.
The Wiimote sees the light, and uses the lights position to position the mouse on screen. The Wiimote uses a camera, by the way.
You will always need bluetooth.

Oh, okay. Thanks. I was hoping I wouldn't need it, but it doesn't really matter.

---

### Post by darude on 2008-05-04
I've installed the packages, following the instructions on here:
[https://help.ubuntu.com/community/CWiiD](https://help.ubuntu.com/community/CWiiD)

However, I can't find the configuration files on my Mythbuntu 8.04.
Both wmgui and wminput works fine, I just like to map the Wii A to KEY_ENTER etc, to use it as a simple remote control for my MythTV.

"ls /usr/local/etc" returns nothing. Can someone help guide a newbie? Thank you!

---

### Post by SniperKIng on 2008-05-04
Hey same problem here. no files at all in that location

---

### Post by darude on 2008-05-04
Found it, it's in /etc/cwiid/wminput on my Mythbuntu box

---

### Post by darude on 2008-05-04
I've used the following buttons for my MythTV setup, works perfectly. Time for a movie I think...:popcorn:

```
#buttons

Wiimote.A		= KEY_ENTER
Wiimote.B		= KEY_ESC
Wiimote.Up		= KEY_UP
Wiimote.Down	= KEY_DOWN
Wiimote.Left	= KEY_LEFT
Wiimote.Right	= KEY_RIGHT
Wiimote.Minus	= KEY_SLASH
Wiimote.Plus	= KEY_KPASTERISK
Wiimote.Home	= KEY_ESC
Wiimote.1		= KEY_SPACE
Wiimote.2		= KEY_F
```

---

### Post by segalion on 2008-05-09
Has anybody try the linux whiteboard with the wiimote and a simple ir-led?

[http://ubuntuforums.org/showthread.php?p=4917093#post4917093](http://ubuntuforums.org/showthread.php?p=4917093#post4917093)

---

### Post by Rhubarb on 2008-05-09
> **segalion said:**
> Has anybody try the linux whiteboard with the wiimote and a simple ir-led?
Not just yet, I've only just managed to get my wiimote working perfectly with hardy (without having to compile anything - just a few config files to edit).
I will probably attempt to get the whiteboard working in a week or so.

---

### Post by durand on 2008-05-09
Trying..but its hard to place the wiimote where it can see the whole screen.

---

### Post by mattgyver83 on 2008-05-11
Ive been trying to use a wiimote as a mouse/game controller.  Im having a rough time getting my wiimote to respond to both mouse movement and button presses.  

When using [wminput -c buttons] configuration i get all buttons except 1 & 2 to respond, when not specifying the [-c buttons] i have mouse movement only.

Another issue is that on my Desktop computer wminput locates my wiimote without entering the MAC address.  When i use my laptop i can only access it by typing wminput and the addr, they are setup exactly same.

If anyone has any suggestions it would be greatly appreciated.  Thanks.

matt.

---

### Post by mattgyver83 on 2008-05-11
I got this working finally, pardon my simple mindedness. :roll:

---

### Post by audwan on 2008-05-21
Finally got to try ir_ptr out again, and your [fix]("http://ubuntuforums.org/showpost.php?p=4811212&postcount=145") worked just great, Schendje. Should this be filed as a bug, by the way?

I've made some changes to the configuration file to make it more useful for the Elisa Media Center. Plus and Minus are used for next and previous song, and Home to pull up the menu. Haven't mapped 1 and 2 to anything useful yet, but I guess you might figure something out.

---

### Post by audwan on 2008-05-21
Anyone got an idea how to map a button to Ctrl+X?

---

### Post by clevermacia on 2008-05-26
Ok, so this is really frustrating. After upgrading to Hardy Heron, my wiimote doesn't work anymore. The only thing that seems to work is the left click!

Here is my buttons file

#buttons

Wiimote.A		= BTN_LEFT
Wiimote.B		= KEY_TAB
Wiimote.Up	= KEY_KATAKANA
Wiimote.Down	= KEY_KPENTER
Wiimote.Left	= KEY_HENKAN
Wiimote.Right	= KEY_MUHENKAN
Wiimote.Minus	= KEY_BACK
Wiimote.Plus	= KEY_FORWARD
Wiimote.Home	= KEY_LEFTSHIFT
Wiimote.1		= KEY_PROG3
Wiimote.2		= KEY_PROG2

Nunchuk.C		= KEY_LEFTALT
Nunchuk.Z		= KEY_LEFTCTRL

Classic.Up		= KEY_UP
Classic.Down	= KEY_DOWN
Classic.Left	= KEY_LEFT
Classic.Right	= KEY_RIGHT
Classic.Minus	= KEY_BACK
Classic.Plus	= KEY_FORWARD
Classic.Home	= KEY_HOME
Classic.A		= BTN_LEFT
Classic.B		= BTN_RIGHT
#Classic.X		= 
#Classic.Y		= 
#Classic.ZL		= 
#Classic.ZR		= 
#Classic.L		= 
#Classic.R		= 

This configuration worked perfectly fine in Gutsy, but in Hardy (which is the only change i've made that I'm guessing could cause the problem) now the only thing that works is BTN_LEFT!!! Nothing else works, and I've changed some values to BTN_LEFT so that more than one key will do the left click, and they work! I've also tried changing the values back to KEY_LEFT, KEY_UP etc, but those don't work either... wmgui shows that the buttons are being registered and everything else is working perfectly fine. Please help me fix this problem!

---

### Post by clevermacia on 2008-05-26
Nevermind, I fixed it. I just copied the buttons file into the ir_ptr file.

---

### Post by KagenoKaze on 2008-06-04
Hey all,

  Great work on this...

I'm trying to make the home key Superkey so i can use it with Compiz Fusion... any ideas how?

Thanks,

Kage

---

### Post by Rhubarb on 2008-06-08
> **KagenoKaze said:**
> I'm trying to make the home key Superkey so i can use it with Compiz Fusion... any ideas how?

I don't quite understand what a home key super key is.
Have a look at all the possible keys you can bind on the wiimote here:
[http://abstrakraft.org/cwiid/browser/tags/cwiid-0.6.00_rc3/wminput/action_enum.txt](http://abstrakraft.org/cwiid/browser/tags/cwiid-0.6.00_rc3/wminput/action_enum.txt)

---

### Post by iTawm on 2008-06-13
Super key is the winkey in windows, in everything I've seen, ubuntu refers to it as Super L. and Home Key is the home button on the wiimote.

My question is, does anyone have a mapping I can use so I can set the joystick on the nunchuck to move the cursor? I'm a bit of a linux newbie and the list of bindings confused me :(

Edit; nevermind, just made it to the part of the thread where it's pointed out that the joystick doesn't work with Cwiid. :/
I tried to get WMD, but the site appears to be gone. Back to googling other drivers for it.

---

### Post by Rhubarb on 2008-06-15
> **iTawm said:**
> My question is, does anyone have a mapping I can use so I can set the joystick on the nunchuck to move the cursor? I'm a bit of a linux newbie and the list of bindings confused me :(

Edit; nevermind, just made it to the part of the thread where it's pointed out that the joystick doesn't work with Cwiid. :/
I tried to get WMD, but the site appears to be gone. Back to googling other drivers for it.

The joystick on the nunchuck should be able to move the mouse cursor.
While I don't have the nun-chuck, I do have the classic controller that has a joystick on it.

Try running:
```
wminput -d -c nunchuck_acc_ptr 01:23:45:67:89:AB
```
(use your mac address of your wiimote).

If that doesn't work, create your own customised config file for your nunchuck here:
/etc/cwiid/wminput

As an example, to get the joystick running on my classic controller (using absolute control, not relative):

/etc/cwiid/wminput/gamepad
```
# gamepad

include buttons

#Classic.Dpad.X = ABS_X
#Classic.Dpad.Y = ABS_Y
Classic.LStick.X = ABS_X
Classic.LStick.Y = -ABS_Y
Classic.RStick.X = ABS_RX
Classic.RStick.Y = ABS_RY
Classic.A = KEY_A
Classic.B = KEY_B
Classic.X = KEY_X
Classic.Y = KEY_Y
Classic.Minus = BTN_SELECT
Classic.Plus  = BTN_START
Classic.Home  = BTN_MODE
Classic.L  = BTN_TL
Classic.R  = KEY_SPACE
Classic.ZL = BTN_TL2
Classic.ZR = BTN_TR2
```

This is the part that actually does the business of making the left stick control the mouse:
```
Classic.LStick.X = ABS_X
Classic.LStick.Y = -ABS_Y
```


To bind the home button on your wii remote to the left Super key, you need to change a line in your /etc/cwiid/wminput/buttons file to read this:
```
Wiimote.Home	= KEY_LEFTMETA
```

As the left Super key would be KEY_LEFTMETA 
The right Super key would be KEY_RIGHTMETA

---

### Post by Nikayah on 2008-06-16
Can anyone give me a hand? I got Cwiid set up perfectly, and it connnects to my wiimote and everything but i want to map the left and right joysticks on a clssic controller AS joysticks, if anyone can help me out with the config file that'd be great.

---

### Post by Rhubarb on 2008-06-16
> **Nikayah said:**
> Can anyone give me a hand? I got Cwiid set up perfectly, and it connnects to my wiimote and everything but i want to map the left and right joysticks on a clssic controller AS joysticks, if anyone can help me out with the config file that'd be great.

You can only bind 1 joystick on the controller as a joystick.  (it'd be as pointless as having 2 mice control the same cursor)

So, to get the left joystick functioning as a joystick, put this into your /etc/cwiid/wminput/gamepad (or similar):-
```
Classic.LStick.X = ABS_X
Classic.LStick.Y = ABS_Y
```
If you find that your Y axis is upside-down, use this:
```
Classic.LStick.X = ABS_X
Classic.LStick.Y = -ABS_Y
```

To find out all possible axis / button bindings you can do, have a look here:
[http://abstrakraft.org/cwiid/browser/tags/cwiid-0.6.00_rc3/wminput/action_enum.txt](http://abstrakraft.org/cwiid/browser/tags/cwiid-0.6.00_rc3/wminput/action_enum.txt)

Normal Joysticks also have mini-joysticks on them (hats), and can be bound to the other joystick on the classic controller.

Also note that you'll need to bind other buttons to the classic controller too - this is entirely up to you what buttons / axis you want to bind them to.

For bindings that would be helpful with the classic controller, here is a list of useful bindings for gamepads, joysticks, and joystick axis:

**Joystick buttons:**
BTN_JOYSTICK
BTN_TRIGGER
BTN_THUMB
BTN_THUMB2
BTN_TOP
BTN_TOP2
BTN_PINKIE
BTN_BASE
BTN_BASE2
BTN_BASE3
BTN_BASE4
BTN_BASE5
BTN_BASE6
BTN_DEAD

**Gamepad buttons:**
BTN_GAMEPAD
BTN_A
BTN_B
BTN_C
BTN_X
BTN_Y
BTN_Z
BTN_TL
BTN_TR
BTN_TL2
BTN_TR2
BTN_SELECT
BTN_START
BTN_MODE
BTN_THUMBL
BTN_THUMBR

**Joystick axis:**
ABS_X
ABS_Y
ABS_Z
ABS_RX
ABS_RY
ABS_RZ
ABS_THROTTLE
ABS_RUDDER
ABS_HAT0X
ABS_HAT0Y
ABS_HAT1X
ABS_HAT1Y
ABS_HAT2X
ABS_HAT2Y
ABS_HAT3X
ABS_HAT3Y
ABS_TILT_X
ABS_TILT_Y

---

### Post by Nikayah on 2008-06-16
Thank you so much! :)

---

### Post by Toshibawarrior on 2008-06-16
Ummm...ok...this might sound stupid...but can anyone let me know where's an actual How-To for this wiimote-linux thing?...this thread has tons of good info but it's all scrambled across 170+ posts...Can anyone let me know what do i need and what do i need to do?...and is this safe?...I've read that some people are left without track/touchpad sensitivity, and they're left only with left and right clicks, without any cursor movement...

Any help will be greatly appreciated! :)

---

### Post by Rhubarb on 2008-06-17
Very good point there Toshibawarrior.
Much of this how-to is out of date, and you won't come across too many problems most people came across earlier in this thread.

I will create a nice tutorial for Ubuntu 8.04 probably this upcoming weekend - when I have a chance to test it out from a fresh Ubuntu install.

If you're too impatient to wait until this weekend, it's worth noting that you don't need to compile anything to get your wiimote working in Ubuntu, - there's just a few configuration files you need to edit and a few packages you need to download and install.

It is safe to get all this working with your wiimote (by making a backup of the configuration files you edit first).

---

### Post by Toshibawarrior on 2008-06-17
Thanks a whole lot Rhubarb! I'm definitely looking forward to your how-to! I was reading this thread last night and I was concerned about some things I read that went wrong. But if you're so kind of making an up-to-date how-to for Hardy then I'll be greatly grateful! :)

And don't worry I can wait until the weekend :popcorn:!

Thanks again!

---

### Post by drjonze on 2008-06-20
I can't get IR working, I just need to update the config file but I tired it once and long story short, I'm back up and running 90 minutes later. I really don't know what I'm doing. Here is my config file, could someone maybe copy it, insert the changes and reply back?

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by Rhubarb on 2008-06-20
drjonze, you do not need to touch your xorg.conf file.  Leave it alone.

You will need to edit a different file, so open up the terminal any type this in:
```
gksu gedit /etc/cwiid/wminput/ir_ptr
```

Make the ir_ptr file look exactly like this:
```
#ir_ptr

include buttons

Plugin.ir_ptr.X	= ABS_X
Plugin.ir_ptr.Y	= ABS_Y
```
Save and quit the text editor.

To connect your wiimote up and get it running as a mouse with IR, push buttons 1 + 2 on your wiimote, then run this in a terminal:
```
wminput -c ir_ptr
```

---

### Post by drjonze on 2008-06-20
> **Rhubarb said:**
> drjonze, you do not need to touch your xorg.conf file.  Leave it alone.

You will need to edit a different file, so open up the terminal any type this in...


Thank you! I will give this at try when I get home from work.

---

### Post by iTawm on 2008-06-20
Hmm, for some reason, whenever I try to open wminput, command line gives me an error?

> tom@tom-laptop:~$ wminput
unable to open uinput
I haven't changed anything since last time I used it.
I tried completely uninstalling and purging all config files, and then reinstalling, but it still does it.

---

### Post by drjonze on 2008-06-20
> **drjonze said:**
> Thank you! I will give this at try when I get home from work.

This worked beautifuly, thank you so much!

Now, off to install Elisa!

---

### Post by Rhubarb on 2008-06-21
> **iTawm said:**
> Hmm, for some reason, whenever I try to open wminput, command line gives me an error?
To fix this up, you need to install the package mouseemu
```
sudo aptitude install mouseemu
```

---

### Post by iTawm on 2008-06-21
> **Rhubarb said:**
> The joystick on the nunchuck should be able to move the mouse cursor.
While I don't have the nun-chuck, I do have the classic controller that has a joystick on it.

Thanks, I think I have an idea of how to do it now, just need to find out what the ID for the nunchuk's joystick is. (:
Edit; I got it, thanks for the link in your other post. My Wiimote now functions as a full mouse, and then some.

> **Rhubarb said:**
> To fix this up, you need to install the package mouseemu
```
sudo aptitude install mouseemu
```

Thanks a lot, it worked and now I can sync my wiimote again. :D
Don't understand why I need this now though, wminput was working fine a week ago.

---

### Post by MrMunkily on 2008-06-21
I have ir_ptr working througgh wmimput, but I'm really not satisfied with how it works.

It seems that whenever I push the pointer past the edge of the screen and then ease off a few degrees back towards center, the cursor moves immediately back from the edge of the screen towards center instead of waiting until I angle the wiimote back to the angle which the cursor initially touched the screen at. It's treating the cursor as a relative device, instead of an absolute device, I guess, kind of like a pen tablet that's mistakenly set on mouse mode.

The other problem is turning off the wiimote. I don't want to have to pull out the batteries each time. I can kill wminput and that shuts down the wiimote, but then I can't reconnect reliably, even if I restart wminput.

Does anyone know how I can address either issue?

---

### Post by Rhubarb on 2008-06-21
MrMunkily, to fix up your ir_ptr file:
```
gksudo gedit /etc/cwiid/wminput/ir_ptr
```
change the two lines in there to look like this:
```
Plugin.ir_ptr.X	= ABS_X
Plugin.ir_ptr.Y	= ABS_Y
```

It is possible to run wminput in daemon mode, so if you power off your wiimote (by pressing and holding the power button), you can simply power on your wiimote later (by pressing buttons 1 + 2) and wminput will automatically reconnect.

Use this command:
```
wminput -d -c ir_ptr 00:1F:32:95:EF:B0
```
- use your wiimote bluetooth address obviously

If you wish to run it as a background process:
```
wminput -d -c ir_ptr 00:1F:32:95:EF:B0 &
```

To stop the wminput daemon:
```
killall wminput
```

I have submitted a new howto thread describing how to setup and configure a wiimote in Ubuntu 8.04.  But alas, it hasn't appeared there yet (waiting for moderators perhaps?).

---

### Post by Rhubarb on 2008-06-22
Toshibawarrior and others here wanting a newer updated howto to get your wiimote working in Ubuntu 8.04 should look here:
[SIZE="4"][HOWTO: Wii remote in Ubuntu 8.04]("http://ubuntuforums.org/showthread.php?p=5232024")[/SIZE]

There is no need to compile anything, it just requires you to download a few packages, and configure a few text files.
You don't even need to run wminput with sudo!

Have fun with your wiimote + Ubuntu + google earth / elisa / DVDs / phun / crayon physics / etc etc :D

---

### Post by Toshibawarrior on 2008-06-22
Rhubarb you are my hero! Thanks so much for this How-To...I read it and it seems to be easy enough...I just have one little question before tampering with my Wiimote and my "current flawlessly working keyboard+mouse configuration"...

If I download all these packages and make these configurations...will my Wiimote still work on my Wii?...I know the configs are on Ubuntu, and the Wiimote is not supposed to be changed in any way, but I want to make 100% sure...

And, if I follow this How-To, will my keyboard+mouse combo will suffer any changes, other than the specified on your How-To (the one about the mouse dying when you type on the keyboard)?

Thank you so much for this! :popcorn::)

---

### Post by MrMunkily on 2008-06-22
[QUOTE=Rhubarb]MrMunkily, to fix up your ir_ptr file:[/QUOTE]

Hmmm. When I try this, the mouse doesn't move at all, though I'm sure it's connected because button pushes still go through. I think my version of cwiid may be too old.

---

### Post by Rhubarb on 2008-06-22
MrMunkily, Ubuntu 8.04 comes with cwiid 0.6.00.
I hope you get it sorted out soon enough.

---

### Post by lunarcloud on 2008-06-29
Any ides how to get the nunchuk stick mapped to keys?

---

### Post by Rhubarb on 2008-07-01
> **zarquad said:**
> Any ides how to get the nunchuk stick mapped to keys?
This may be possible using joy2key.
[http://ubuntuforums.org/showthread.php?t=646564](http://ubuntuforums.org/showthread.php?t=646564)

---

### Post by Rhubarb on 2008-07-09
A perhaps more elegant way is to compile a plugin for wminput:
[http://kyrlian.free.fr/binaries/cwiid/latest/](http://kyrlian.free.fr/binaries/cwiid/latest/)

I haven't tried this myself, and it does appear to be under development.

---

### Post by vbman11 on 2008-07-09
Ok so when I add the xorg section and restart X My computer goes into low graphics mode. Any ideas on how to fix this?

---

### Post by Rhubarb on 2008-07-09
> **vbman11 said:**
> Ok so when I add the xorg section and restart X My computer goes into low graphics mode. Any ideas on how to fix this?
There's no need to edit your /etc/X11/xorg.conf if you're running Ubuntu 8.04.
Please follow my updated much easier guide here: [**HOWTO: Wii remote in Ubuntu 8.04**]("http://ubuntuforums.org/showthread.php?p=5232024")
To fix up your low graphics mode (which is a sure sign you're in bullet-proof X mode because it didn't like your xorg.conf edit previously):
Press **Alt + F2**, enter in: **gksu displayconfig-gtk**
You may need to specify your monitor and graphics card there.
Altertatively there may be a backup xorg.conf file sitting in your /etc/X11/ directory that you may be able to restore.

---


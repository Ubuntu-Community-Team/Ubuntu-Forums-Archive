---
title: "Guitar Hero3 wii controller in Ubuntu"
date: 2007-11-05
forum: Gaming &amp; Leisure
---

### Post by djuniah on 2007-11-05
I just picked up GH3 for my Wii and I'm loving the game.  I also play Frets on Fire on my ubuntu machine quite frequently and I thought it would be a SIMPLE matter to connect my GH3 controller to my PC via bluetooth and jam out.  Boy was I wrong!  I have everything set up for the wii remote control and it works splendidly, BUT when I try to connect my wiimote with the GH3 adapter added on I get the following error:
```

Registering key BTN_RIGHT for button A with code 111
Registering key BTN_LEFT for button B with code 110
Registering key ['KEY_LEFTCTRL', 'KEY_LEFTALT', 'BTN_LEFT'] for button D with code 1d
Registering key ['KEY_LEFTCTRL', 'KEY_LEFTALT', 'BTN_LEFT'] for button D with code 38
Registering key ['KEY_LEFTCTRL', 'KEY_LEFTALT', 'BTN_LEFT'] for button D with code 110
Registering key ['KEY_LEFTALT'] for button L with code 38
Registering key KEY_1 for button 1 with code 2
Registering key KEY_2 for button 2 with code 3
Registering key ['KEY_LEFTCTRL'] for button U with code 1d
Registering key ['KEY_F8'] for button R with code 42
[[1074025828, 2], [1074025830, 0], [1074025830, 1], [1074025828, 1], [1074025828, 0], [1074025829, 273], [1074025829, 272], [1074025829, 29], [1074025829, 56], [1074025829, 272], [1074025829, 56], [1074025829, 2], [1074025829, 3], [1074025829, 29], [1074025829, 66]]
Could not import pygame. Set DISABLE_PYGAME=1
CONNECTING
Looking for Wiimote services at address  00:1A:E9:30:4D:F0
Victory! We have found that Wiimote!
We are now connected to Wiimote at address  00:1A:E9:30:4D:F0
CONNECTED
Traceback (most recent call last):
  File "WMD.py", line 45, in <module>
    wmd = WMD()
  File "WMD.py", line 41, in __init__
    cycles = wm.main_loop()
  File "/home/ricky/Downloads/wmd-0.1.2/wmd/Wiimote/WMManager.py", line 42, in main_loop
    self.parser.parse( data )
  File "/home/ricky/Downloads/wmd-0.1.2/wmd/Wiimote/Input.py", line 102, in parse
    self.split_report( report, type )
  File "/home/ricky/Downloads/wmd-0.1.2/wmd/Wiimote/Input.py", line 119, in split_report
    func( slice )
  File "/home/ricky/Downloads/wmd-0.1.2/wmd/Wiimote/Input.py", line 155, in slice_STAT
    self.process_stats( s )
TypeError: process_stats() takes exactly 1 argument (2 given)

```

I also noticed that even on the wii, the GH3 controller does NOT work until you put the disk in and click on it in the menu.  This initializes a system update and then once that is done, the Guitar can control the cursor in the menu.  This leads me to believe that its using some new type of interface with the wii than we are used to seeing.  So, there has to be a way to get this working with WMD.  I just havent figured it out yet.  Has anyone else tried this?  I'm going to start poking around in the python files to see what the cause is.  

Also, if i use 
```
sudo hidd --search
```
and
```
sudo hcidump -X
```
with JUST the wiimote, i get the expected results, but as soon as i plug in the GH adapter it spat out the following lines then stopped responding to key presses (even if i removed the GH adapter).  
```

> ACL data: handle 6 flags 0x02 dlen 12
    L2CAP(d): cid 0x0041 len 8 [psm 0]
      0000: a1 20 00 00 02 00 00 57                           . .....W

```

can anyone with a little more experience shed some light on this issue?

Thanks,
DJuniah

---

### Post by Niklas Schröder on 2007-11-05
wow.  that's really strange...  my guess is that redoctane knew some people were gonna try it on the pc and did something to the guitar that would change the signal.  but it's not like it's a permanent road-block right!  :p

---

### Post by markmark on 2007-11-06
In "Input.py" find:
```
  def process_stats( s ):
    pass

  def process_bat( b ):
    pass
```
And change it so it reads:
```
  def process_stats( self, s ):
    pass

  def process_bat( self, b ):
    pass
```

Alternatively process_stats and process_bat don't do anything, so you could just comment out any calls to them.

I'm planning on getting GH3 for my Wii sometime soon and I want to use it in FoF, so hopefully someone will get all this working.

---

### Post by markmark on 2007-11-06
Actually I just looked at the svn version of wmd and notice that Input.py has been updated a fair bit from the version I downloaded ([https://svn.forthewiin.org/wmd/trunk/wmd/Wiimote/Input.py](https://svn.forthewiin.org/wmd/trunk/wmd/Wiimote/Input.py))

Might be worth checking out the lastest version from SVN.

---

### Post by djuniah on 2007-11-06
Ok, getting a little further now.  It is at least seeing that there is a peripheral attached but it doesent seem to know what to do with it.  Heres the console output:
```

uinput: Attempting to autodetect device file
uinput: /dev/misc/uinput isn't a usable uinput device file
uinput: autodetection chose /dev/input/uinput as uinput device file
uinput: Trying to open /dev/input/uinput as control device
uinput: Writing WIIMOTE_UUD
uinput: Registering 31 events
uinput: Creating device
uinput: initialized and ready
Could not import pygame. Set DISABLE_PYGAME=1
CONNECTING
Looking for Wiimote services at address 00:1A:E9:30:4D:F0
Victory! We have found that Wiimote!
We are now connected to Wiimote at address 00:1A:E9:30:4D:F0
CONNECTED
EXTCON_ATTACH EVENT v=1
Event type WM_CLOCK_BEAT is being ignored
EXTCON_ATTACH EVENT v=1
tilt (x,y) = (141, 130)
tilt (x,y) = (141, 130)
tilt (x,y) = (141, 131)
tilt (x,y) = (141, 131)
tilt (x,y) = (143, 131)
tilt (x,y) = (144, 132)
tilt (x,y) = (144, 132)
tilt (x,y) = (145, 133)
Wiimote Calibration Bytes:  [112, 0, 22, 131, 129, 132, 8, 157, 156, 156, 42, 0, 0, 0, 0, 0, 0, 0, 0]
tilt (x,y) = (145, 133)
tilt (x,y) = (146, 134)
tilt (x,y) = (146, 134)
tilt (x,y) = (146, 134)
tilt (x,y) = (146, 134)
tilt (x,y) = (146, 135)
tilt (x,y) = (146, 135)
tilt (x,y) = (145, 135)
tilt (x,y) = (145, 135)
tilt (x,y) = (145, 135)
Invalid memory read during controller attachment
Traceback (most recent call last):
  File "WMD.py", line 45, in <module>
    wmd = WMD()
  File "WMD.py", line 41, in __init__
    cycles = wm.main_loop()
  File "/home/ricky/Downloads/wmd-0.1.2/wmd/Wiimote/WMManager.py", line 46, in main_loop
    self.parser.parse( data )
  File "/home/ricky/Downloads/wmd-0.1.2/wmd/Wiimote/Input.py", line 36, in parse
    self.split_report( rep_payload, rep_def )
  File "/home/ricky/Downloads/wmd-0.1.2/wmd/Wiimote/Input.py", line 63, in split_report
    func( slice_bl )
  File "/home/ricky/Downloads/wmd-0.1.2/wmd/Wiimote/Input.py", line 158, in slice_MEM_READ_DATA
    self.wmstate.incoming_ram_data( slb )
  File "/home/ricky/Downloads/wmd-0.1.2/wmd/Wiimote/Input.py", line 327, in incoming_ram_data
    callback( data )
  File "/home/ricky/Downloads/wmd-0.1.2/wmd/Wiimote/Input.py", line 375, in read_extcont_type_callback
    if ext_device_name in self.valid_ext_device_names:
UnboundLocalError: local variable 'ext_device_name' referenced before assignment


```

---

### Post by markmark on 2007-11-07
Did you check out an entire new version of the whole program from SVN? Or just grab that one file. I know my post wasn't very clear, but you'll have to use subversion to check out everything.

---

### Post by djuniah on 2007-11-07
yes i made sure to grab everything and do a full checkout, but no luck. I did see the new file that looks like it handles controller add-ons though.  I'm guessing what i seek has something to do with a definition that needs to be added to that.

---

### Post by markmark on 2007-11-07
The error is saying ext_device_name isn't defined but they are trying to check the value of it.

Perhaps change:
```
 def __init__( self, ev, wmmode ):
    self.ev = ev
    self.wmmode = wmmode
```
to read
```
 def __init__( self, ev, wmmode ):
    self.ev = ev
    self.wmmode = wmmode
    self.ext_device_name = ""

```

That should make sure that ext_device_name is set to something when the object is created (although I thought what they had would have done that).

It looks like this bit:
```
    if off == 0xfe and ct1 == ct2:
      if ct1 == 0xfd:
        ext_device_name = 'Classic'
      elif ct1 == 0xfe:
        ext_device_name = 'Nunchuk'
      else:
        log( LOG_ERR, "Unknown device type %x" % ct1 )
    else:
      log( LOG_ERR, "Invalid memory read during controller attachment" )

```
Will need to be updated to handle the Guitar, but without one to play with myself I can't figure out what values to put in there.

Actually, looking at that the log should contain a line saying "Unknown device type xxxx" we need to add stuff to handle the guitar like:

```
    if off == 0xfe and ct1 == ct2:
      if ct1 == 0xfd:
        ext_device_name = 'Classic'
      elif ct1 == 0xfe:
        ext_device_name = 'Nunchuk'
      elif ct1 == xxxx:
        ext_device_name = 'Guitar'
      else:
        log( LOG_ERR, "Unknown device type %x" % ct1 )
    else:
      log( LOG_ERR, "Invalid memory read during controller attachment" )

```

Where 'xxxx' is whatever is in the log file, and 'Guitar' will have to be added to valid_ext_devices' or whatever it was. Of course we still won't actually have code to handle the Guitar.

---

### Post by markmark on 2007-11-07
Actually, as an idea for a quick and dirty fix, change it to:```
    if off == 0xfe and ct1 == ct2:
      if ct1 == 0xfd:
        ext_device_name = 'Classic'
      elif ct1 == 0xfe:
        ext_device_name = 'Nunchuk'
      else:
        ext_device_name = 'Nunchuk'
        log( LOG_ERR, "Unknown device type %x" % ct1 )
    else:
      log( LOG_ERR, "Invalid memory read during controller attachment" )
```Which will make it think the Guitar is a Nunchuck. Might be enough to get the buttons and stuff working, which would be all you'd need for FoF?

---

### Post by djuniah on 2007-11-07
Thanks for all the awesome replies, I'll give it a shot later on tonight and report back on with a full writeup of what i had to do to get it working.
(if i can manage to tear myself away from frets on fire that is ;) )

---

### Post by djuniah on 2007-11-08
GOT IT!!! AND ITS WORKING AMAZINGLY!

This assumes that you already have a working WMD installed and you can connect a regular wiimote.  Also, this assumes that you are using the SVN version of WMD as of 11/8/2007 found at [https://svn.forthewiin.org/wmd/trunk/]("https://svn.forthewiin.org/wmd/trunk/")

NOTE: Following this guide WILL DISABLE motion sensing in the wiimote and will make all "unknown" controllers look like a classic controller to WMD.  Also, it will change the default action of one of the buttons on the classic controller.

Heres what i needed to change:

**ExtensionControllers.py**
comment out line 222
```
#self.ev.send( WM_EXT_ANALOG, activeAxes )
```

**Input.py**
comment out line 80
```
#self.ev.send( WM_ACC, force )
```
line 365 should look like this:
```

if off == 0xfe and ct1 == ct2:
      if ct1 == 0xfd:
        ext_device_name = 'Classic'
      elif ct1 == 0xfe:
        ext_device_name = 'Nunchuk'
      else:
	ext_device_name = 'Classic'
        #log( LOG_ERR, "Unknown device type %x" % ct1 )
    else:
      ext_device_name = 'Classic'
      log( LOG_ERR, "Invalid memory read during controller attachment" )

```

**Config.py**
line 39
The default configuration for the orange "fret" was the left mouse button and that cant be mapped in Frets on Fire so i changed it to be the L key
```
'CZl': [ 'key', 'KEY_L'  ],  # Zl (small shoulder button)
```

Once all that is done, open up Frets on Fire and go to the settings menu.  From there you can re-map the keys in the game to the controller.  Once that is done you should be all set.

Thanks to everyone in this post for pointing me in the right direction on this one!

---

### Post by markmark on 2007-11-08
Excellent. I'm hoping to grab GH3 this weekend, so I should get to give it a go myself sometime soon. Actually I should try and dig up my bluetooth adapter and see if it works first I guess...

---

### Post by djuniah on 2007-11-08
I hoping that support for it will be built into WMD soon, but for now this should do the trick.  I have a few items i may change in that mini-tutorial up there but i'm not sure about that yet.  Instead of just changing the one keymapping in WMD and doing the rest in FoF it might be better to do it all with WMD.  My reason for leaving it out initially was to screw with the original WMD files as little as possible.  I figure that would be easier for most people.

---

### Post by CaseyR on 2007-11-09
this is good news guys!  is there any way to pair the GH guitar with a sequencer/sampler (similar to a midi device) and use it as an instrument?

im using CWiiD instead of wmd.  im having some trouble tweaking the joystick on the guitar to use it as a mouse similar to how it is used in the wii menu.  any ideas?

thanks!

---

### Post by djuniah on 2007-11-09
I could never get Cwiid (heh seaweed...i just got that....anyways...) to work for me, but i could see it being possible.  You just have to route the keypresses through some sort of script that would translate it to midi data.  But i'm not sure how effective of an instrument it would be with that few keys to hit.  Definitely keep us updated though, i would like to try it.

---

### Post by jpreville on 2007-11-18
I've been trying to get my GH3 wii controller to work with FOF under ubuntu. But for some reason
i can get to ]https://svn.forthewiin.org/wmd/trunk/

or the main site [http://www.forthewiin.org](http://www.forthewiin.org)

seems to be gone. or down..

i just need the newest version of WMD i think

if someone could point me in the write direction i would appreciate it.

- John

EDIT:

I ended up getting this to work with cwiid and make a new gh3 config file.

---

### Post by mzdsb on 2007-11-20
same problem here with the [http://www.forthewiin.org](http://www.forthewiin.org) web...

> I ended up getting this to work with cwiid and make a new gh3 config file.

could you please post how did you make it work with cwiid?

---

### Post by jpreville on 2007-11-20
to start off im running Ubuntu 7.1 gutsy on a laptop with a cheap 20
dollar bluetooth adaptor from walmarts.

First thing you need to do is make sure your bluetooth can see
the wiimote.

open up terminal 

hcitool scan (press 1+2 on on wiimote before pressing enter)

if its working you should see something like.

xx:xx:xx:xx:xx:xxx
Nintendo RVL-CNT-01

once you verified that.

i used to synaptics package manager to install cwiid

open synaptics. search cwiid. I pick all that came up.

esp wmgui (usefull for tesing wiimote and nowing what your hitting on wiimote, wiiguitar)

run wmgui which installs under application/accessories

click file/connect (verify you are talking to your wiimote. the one in the wiiguitar)

the wiiguitar emulates a classic controller so go under settings/and click on extension data


hits some keys on your wiiguitar to make sure they work with wmgui.

if they do go then your good so far.


to make cwiid or wminput emulate the keystrokes in Frets on Fire you need a profile
that matches the keys in FOF.

i ended up copying and modifying the gamepad profile under

/etc/cwiid/wminput

named it gh3 (might be better to do a FOF.. but oh well)

i made a file under /etc/cwiid/wminput called gh3

sudo gedit /etc/cwiid/wminput/gh3

place this in the file

# wiiguitar profile for FOF
Classic.Down=KEY_ENTER #Strum
Classic.Dpad.X = ABS_X
Classic.Dpad.Y = ABS_Y
Classic.LStick.X = ABS_HAT0X
Classic.LStick.Y = ABS_HAT0Y
Classic.RStick.X = ABS_HAT1X
Classic.RStick.Y = ABS_HAT1Y
Classic.A = KEY_F1 #First Fret starting at top of wiiguitar
Classic.B = KEY_F2 #Second Fret
Classic.X = KEY_F3 #Third Fret
Classic.Y = KEY_F4 #Forth Fret
Classic.Minus = BTN_SELECT
Classic.Plus  = BTN_START
Classic.Home  = BTN_MODE
Classic.L  = BTN_TL
Classic.R  = BTN_TR
Classic.ZL = KEY_F5 #Fifth Fret
Classic.ZR = BTN_TR2


save

note: the keys mapped to wiiguitar. I left FOF at default keys.
i havent mapped everything yet. was excited enough
just to be able to play FOF with wiiguitar. any how i will finish it up tonite if i get
a chance.

to use open up terminal

sudo wminput -c /etc/cwiid/wminput/gh3  (before pressing enter press 1+2 on wiimote in wiiguitar once blinking press enter)

if everything works you should see a ready.. Leave terminal window open

run Frets on Fire and you should be working.

im sure there are better ways to do this like writing a little bash script
to sync wiiguitar first then launch FOF. i'll work on this another time.

anyway hopefully this helps

- John

Edited:nov 20 8:52

---

### Post by mzdsb on 2007-11-20
thanks! great tutorial!
unfortunately  guitar hero 3 will not be released until this friday in spain, so I can't test your tutorial. but i'm pretty sure it'll do the job :D

thanks again.

---

### Post by jpreville on 2007-11-20
ahh that sucks..3 more days.

anyway.. just check back on this post. i'll see if i can make the mappings better for frets on fire for all buttons on wiiguitar. i will just edit the previous post.

John

---

### Post by GavinZac on 2007-12-28
anyone else tried this? just got guitar hero iii for the wii and want to try out some other songs :)

---

### Post by GavinZac on 2007-12-29
ok, i set all of this up, the only problem is that at the last bit, when I run *sudo wminput -c /etc/cwiid/wminput/fof* (i named mine FOF because thats what its for :) ) I get an error saying *unable to open uinput*

did a little researcha nd the fix was
*sudo ldconfig /usr/local/lib/*
and
*sudo modprobe uinput*

I AM NOW PLAYING FOF WITH MY WII GUITAR :D :D

---

### Post by BHSPitMonkey on 2008-09-21
> **CaseyR said:**
> this is good news guys!  is there any way to pair the GH guitar with a sequencer/sampler (similar to a midi device) and use it as an instrument?

No.  The Guitar Hero guitar is not designed to emulate any of the functions of an actual instrument.  It is a toy.

---

### Post by djuniah on 2008-09-22
so quick to say no there....
there are ways of doing it (i've seen it done, but i'm not sure of the list of apps that were used to get it to work)
There are software applications out there that can map standard input to midi signals and then you can route that to an application. You arent going to be getting a lot of buttons to work with, but it is possible

---


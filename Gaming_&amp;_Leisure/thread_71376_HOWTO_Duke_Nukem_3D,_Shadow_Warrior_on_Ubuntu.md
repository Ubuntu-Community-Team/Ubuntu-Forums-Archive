---
title: "HOWTO: Duke Nukem 3D, Shadow Warrior on Ubuntu"
date: 2005-10-03
forum: Gaming &amp; Leisure
---

### Post by dolny on 2005-10-03
Check out: [http://jonof.edgenetwork.org/](http://jonof.edgenetwork.org/)

Shadow Warrior Installation tutorial (v 0.2 ;) )

1. Download Build engine source
2. Download Shadow Warrior source
3. Download Shadow Warrior music patch: [http://jonof.edgenetwork.org/forum/viewtopic.php?t=580](http://jonof.edgenetwork.org/forum/viewtopic.php?t=580)
4. Download Shadow Warrior shareware: [http://www.3drealms.com/sw/](http://www.3drealms.com/sw/)

You'll need the following libraries: 
GCC
nasm ([http://sourceforge.net/project/showfiles.php?group_id=6208](http://sourceforge.net/project/showfiles.php?group_id=6208))
libsdl1.2-dev
libsdl1.2
fmod ([http://www.fmod.org](http://www.fmod.org))

1. Create a dir called 3drealms
2. Put both sources there
3. Rename the Build source dir to build
4. Rename the SW source dir to sw
5. Your dirs should look like this:
../3drealms/build/
../3drealms/sw/
6. Apply the sound patch ([http://jonof.edgenetwork.org/forum/viewtopic.php?t=580](http://jonof.edgenetwork.org/forum/viewtopic.php?t=580)) 

```
patch -p1<nameofthefile.diff
```

7. Go into the ../3drealms/build/include/ dir and remove the "extern unsigned char keynames[256][24];" line from baselayer.h.
8. Switch the dir to ../3drealms/sw/ and run 'sudo make' (I don't know whether the root permissions are necessary)
9. Ignore the warnings and after compilation copy the SW.GRP and SW.RTS files (from the original full/shareware version of Shadow Warrior) to your /sw/ dir and rename it to sw.grp and sw.rts
10. Run: ./sw
11. Disable ambience sounds in the options if the game freezes after entering the level
12. Exit the game and configure it through sw.cfg
13. Enjoy.

I'm using Breezy, the tutorial may not work with Hoary for example - I've used GCC 4.x. Following this tutorial may crash your Linux box, your dog may get a fever etc. I don't take any responsibility for the results ;)

Here's my screenshot of SW running on my Linux box: [http://www.echostar.pl/~dolny/ubu/swlinux.jpg](http://www.echostar.pl/~dolny/ubu/swlinux.jpg)

I would like to thank the author for his work on the port and cooperation.

---

### Post by dolny on 2005-10-05
A config that adds mouse aiming (by phen):

```
Screen Setup] 
Shadows = 1 
Detail = 1 
Tilt = 1 
Messages = 1 
ScreenMode = 1 
ScreenWidth = 1024 
ScreenHeight = 768 
ScreenBPP = 32 

[Sound Setup] 
FXVolume = 208 
MusicVolume = 200 
SoundToggle = 1 
VoiceToggle = 1 
AmbienceToggle = 0
MusicToggle = 1 
FXDevice = 0 
NumVoices = 32 
NumBits = 16 
NumChannels = 2 
MixRate = 48000 
MusicDevice = 0 
ReverseStereo = 0 

[Controls] 
MouseSensitivity = 19656 
ControllerType = 1 
MouseAiming = 0 
MouseButton0 = "Fire" 
MouseButtonClicked0 = "" 
MouseButton1 = "Open" 
MouseButtonClicked1 = "" 
MouseButton2 = "" 
MouseButtonClicked2 = "" 
MouseButton3 = "" 
MouseButtonClicked3 = "" 
MouseButton4 = "" 
MouseButton5 = "" 
MouseAnalogAxes0 = "analog_turning" 
MouseAnalogAxes1 = "analog_moving" 
MouseAnalogScale0 = 65536 
MouseAnalogScale1 = -65536 
MouseDigitalAxes0_0 = "" 
MouseDigitalAxes0_1 = "" 
MouseDigitalAxes1_0 = "" 
MouseDigitalAxes1_1 = "" 
JoystickButton0 = "Fire" 
JoystickButtonClicked0 = "" 
JoystickButton1 = "Strafe" 
JoystickButtonClicked1 = "Inventory" 
JoystickButton2 = "Run" 
JoystickButtonClicked2 = "Jump" 
JoystickButton3 = "Open" 
JoystickButtonClicked3 = "Crouch" 
JoystickButton4 = "Aim_Down" 
JoystickButtonClicked4 = "" 
JoystickButton5 = "" 
JoystickButtonClicked5 = "" 
JoystickButton6 = "Aim_Up" 
JoystickButtonClicked6 = "" 
JoystickButton7 = "" 
JoystickButtonClicked7 = "" 
JoystickAnalogAxes0 = "analog_turning" 
JoystickDigitalAxes0_0 = "" 
JoystickDigitalAxes0_1 = "" 
JoystickAnalogScale0 = 65536 
JoystickAnalogDead0 = 1000 
JoystickAnalogSaturate0 = 9500 
JoystickAnalogAxes1 = "analog_moving" 
JoystickDigitalAxes1_0 = "" 
JoystickDigitalAxes1_1 = "" 
JoystickAnalogScale1 = 65536 
JoystickAnalogDead1 = 1000 
JoystickAnalogSaturate1 = 9500 
JoystickAnalogAxes2 = "analog_strafing" 
JoystickDigitalAxes2_0 = "" 
JoystickDigitalAxes2_1 = "" 
JoystickAnalogScale2 = 65536 
JoystickAnalogDead2 = 1000 
JoystickAnalogSaturate2 = 9500 
JoystickAnalogAxes3 = "" 
JoystickDigitalAxes3_0 = "Run" 
JoystickDigitalAxes3_1 = "" 
JoystickAnalogScale3 = 65536 
JoystickAnalogDead3 = 1000 
JoystickAnalogSaturate3 = 9500 

[KeyDefinitions] 
Move_Forward = "W" "" 
Move_Backward = "S" "" 
Turn_Left = "" "" 
Turn_Right = "" "" 
Strafe = "LAlt" "" 
Fire = "" "" 
Open = "E" "" 
Run = "LShift" "" 
AutoRun = "CapLck" "" 
Jump = "Space" "" 
Crouch = "LCtrl" "" 
Look_Up = "PgUp" "" 
Look_Down = "PgDn" "" 
Strafe_Left = "A" "" 
Strafe_Right = "D" "" 
Aim_Up = "Home" "" 
Aim_Down = "End" "" 
Weapon_1 = "1" "" 
Weapon_2 = "2" "" 
Weapon_3 = "3" "" 
Weapon_4 = "4" "" 
Weapon_5 = "5" "" 
Weapon_6 = "6" "" 
Weapon_7 = "7" "" 
Weapon_8 = "8" "" 
Weapon_9 = "9" "" 
Weapon_10 = "0" "" 
Inventory = "Enter" "" 
Inventory_Left = "[" "" 
Inventory_Right = "]" "" 
Med_Kit = "M" "" 
Smoke_Bomb = "S" "" 
Night_Vision = "N" "" 
Gas_Bomb = "G" "" 
Flash_Bomb = "F" "" 
Caltrops = "C" "" 
TurnAround = "BakSpc" "" 
SendMessage = "T" "" 
Map = "Tab" "" 
Shrink_Screen = "-" "" 
Enlarge_Screen = "=" "" 
Center_View = "Kpad5" "" 
Holster_Weapon = "ScrLck" "" 
Map_Follow_Mode = "F" "" 
See_Co_Op_View = "K" "" 
Mouse_Aiming = "U" "" 
Toggle_Crosshair = "I" "" 
Next_Weapon = "'" "" 
Previous_Weapon = ";" "" 

[Options] 
BorderNum = 1 
Brightness = 0 
BorderTile = 0 
Bobbing = 1 
Tilting = 0 
Shadows = 1 
AutoRun = 1 
Crosshair = 1 
AutoAim = 0 
Messages = 1 
Talking = 1 
Ambient = 1 
FxOn = 1 
MusicOn = 1 
NetGameType = 0 
NetLevel = 0 
NetMonsters = 0 
NetHurtTeammate = 0 
NetSpawnMarkers = 1 
NetTeamPlay = 0 
NetKillLimit = 0 
NetTimeLimit = 0 
NetColor = 0 
Voxels = 1 
MouseAimingOn = 1 
MouseInvert = 0 
Stats = 1 
Rooster = "" 
Kiwi = 0 
PlayCD = 0
```

Any comments?

---

### Post by NeoChaosX on 2005-10-10
Edit: Never mind, got it working. Also, list libsdl-mixer1.2-dev as a dependency, as I wasn't aware of this and was confused why it wouldn't compile at first.

Edit 2: How do you get music working with this thing? Or is it impossible right now?

---

### Post by NeoChaosX on 2005-10-10
In fact, maybe this should be updated considering Jonof just released new versions of all his ports yesterday.

---

### Post by seethru on 2005-10-10
great HOWTO dolny :)

---

### Post by fakie_flip on 2005-10-14
I see the howto guide for Shadow Warrior, but where is the one to install Duke Nukem. I love that game.

---

### Post by geearf on 2006-02-24
duke is crashing and I cannot find the good files for SW :(

---

### Post by Gato303co on 2012-11-12
Hello, sorry for "activating" an old post, but well, I am trying this for the first time and I got questions, if you were kind to help me ;)

First, the JonoF's website in the address of the post is no longer working, I found him at this address:
[http://www.jonof.id.au/](http://www.jonof.id.au/)

Second, when you say the SW source, you mean the source that can be downloaded from 3DRealms website?  [http://www.3drealms.com/sw/](http://www.3drealms.com/sw/) ??

Thanks for your attention :)

---

### Post by overdrank on 2012-11-12
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---


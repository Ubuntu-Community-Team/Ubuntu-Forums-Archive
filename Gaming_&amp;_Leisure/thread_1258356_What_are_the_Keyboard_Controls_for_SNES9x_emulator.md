---
title: "What are the Keyboard Controls for SNES9x emulator?"
date: 2009-09-04
forum: Gaming &amp; Leisure
---

### Post by Blue Dolphins on 2009-09-04
So far I've got by guessing them, but now I need to know how to press the left and right shoulder buttons and I can't find them.  So far I've figured out  ...

Enter=Start
IJKL(or arrow buttons)=Directional 
D=A 
C=B  

What are X, Y, Select, and the L and R shoulder buttons?  Through Google, I can't find any info.

---

### Post by hikaricore on 2009-09-04
I hate to sound obvious here but why don't you just go into the Options menu and change the keybinding to whatever you want?

---

### Post by Blue Dolphins on 2009-09-04
I can't, I can only change the controls for joypads, not the computer keyboard.

---

### Post by benmoran on 2009-09-05
I recommend using GTKsnes9x. It's way better than the version in the repositories. Check it out:

[http://www.snes9x.com/phpbb2/viewtopic.php?p=22874](http://www.snes9x.com/phpbb2/viewtopic.php?p=22874)

---

### Post by Blue Dolphins on 2009-09-05
Do you use Snes9x?  Can you tell me what the default controls are?, that's all I need.

 I don't want to install anything, my only problem is not knowing the default controls.  Also, I've tried adding new repos before, but I'm real computer-stupid, I only know how to use .deb files or the default repos.  Even if I did install that gtksnes9x, wouldn't I have to restart the game I'm playing from scratch, since it's a different emulator?

---

### Post by 569874123 on 2009-09-06
You can install snes9express from synaptic, it has the option to configure the button maps.

---

### Post by urjaman on 2010-04-27
And the default controls are (from snes9x.conf.default in the snes9x 1.52 source package):
K00:k = Joypad1 Right
K00:Right = Joypad1 Right
K00:h = Joypad1 Left
K00:Left = Joypad1 Left
K00:j = Joypad1 Down
K00:n = Joypad1 Down
K00:Down = Joypad1 Down
K00:u = Joypad1 Up
K00:Up = Joypad1 Up
K00:Return = Joypad1 Start
K00:space = Joypad1 Select
K00:S+d = Joypad1 ToggleTurbo A
K00:C+d = Joypad1 ToggleSticky A
K00:d = Joypad1 A
K00:S+c = Joypad1 ToggleTurbo B
K00:C+c = Joypad1 ToggleSticky B
K00:c = Joypad1 B
K00:S+s = Joypad1 ToggleTurbo X
K00:C+s = Joypad1 ToggleSticky X
K00:s = Joypad1 X
K00:S+x = Joypad1 ToggleTurbo Y
K00:C+x = Joypad1 ToggleSticky Y
K00:x = Joypad1 Y
K00:S+a = Joypad1 ToggleTurbo L
K00:S+v = Joypad1 ToggleTurbo L
K00:C+a = Joypad1 ToggleSticky L
K00:C+v = Joypad1 ToggleSticky L
K00:a = Joypad1 L
K00:v = Joypad1 L
K00:S+z = Joypad1 ToggleTurbo R
K00:C+z = Joypad1 ToggleSticky R
K00:z = Joypad1 R

K00:KP_Left = Joypad2 Left
K00:KP_Right = Joypad2 Right
K00:KP_Up = Joypad2 Up
K00:KP_Down = Joypad2 Down
K00:KP_Enter = Joypad2 Start
K00:KP_Add = Joypad2 Select
K00:Prior = Joypad2 A
K00:Next = Joypad2 B
K00:Home = Joypad2 X
K00:End = Joypad2 Y
K00:Insert = Joypad2 L
K00:Delete = Joypad2 R

K00:A+Escape = Debugger
K00:CS+Escape = Reset
K00:S+Escape = SoftReset
K00:Escape = ExitEmu
K00:Tab = EmuTurbo
K00:S+Tab = ToggleEmuTurbo
K00:Scroll_Lock = Pause
K00:Pause = Pause

K00:A+Sys_Req = DumpSPC7110Log
K00:A+Pause = DumpSPC7110Log
K00:S+1 = BeginRecordingMovie
K00:S+2 = EndRecordingMovie
K00:S+3 = LoadMovie

K00:A+F1 = SaveSPC
K00:C+F1 = SaveSPC
K00:A+F2 = LoadFreezeFile
K00:C+F2 = LoadFreezeFile
K00:A+F3 = SaveFreezeFile
K00:C+F3 = SaveFreezeFile
K00:F1 = QuickLoad000
K00:F2 = QuickLoad001
K00:F3 = QuickLoad002
K00:F4 = QuickLoad003
K00:F5 = QuickLoad004
K00:F6 = QuickLoad005
K00:F7 = QuickLoad006
K00:F8 = QuickLoad007
K00:F9 = QuickLoad008
K00:F10 = LoadOopsFile
K00:F11 = LoadFreezeFile
K00:F12 = SaveFreezeFile
K00:S+F1 = QuickSave000
K00:S+F2 = QuickSave001
K00:S+F3 = QuickSave002
K00:S+F4 = QuickSave003
K00:S+F5 = QuickSave004
K00:S+F6 = QuickSave005
K00:S+F7 = QuickSave006
K00:S+F8 = QuickSave007
K00:S+F9 = QuickSave008

K00:0 = ToggleHDMA
K00:1 = ToggleBG0
K00:2 = ToggleBG1
K00:3 = ToggleBG2
K00:4 = ToggleBG3
K00:5 = ToggleSprites
K00:6 = SwapJoypads
K00:S+6 = OpenGLCube
K00:8 = BGLayeringHack
K00:S+9 = Mode7Interpolate
K00:9 = ToggleTransparency
K00:minus = DecFrameRate
K00:S+minus = DecFrameTime
K00:C+minus = DecTurboSpeed
K00:A+minus = DecEmuTurbo
K00:equal = IncFrameRate
K00:S+equal = IncFrameTime
K00:C+equal = IncTurboSpeed
K00:A+equal = IncEmuTurbo
K00:BackSpace = ClipWindows
K00:Print = Screenshot
K00:Sys_Req = Screenshot
K00:A+f = FullscreenToggle

K00:bracketleft = InterpolateSound
K00:bracketright = SynchronizeSound
K00:A+F4 = SoundChannel0
K00:C+F4 = SoundChannel0
K00:A+F5 = SoundChannel1
K00:C+F5 = SoundChannel1
K00:A+F6 = SoundChannel2
K00:C+F6 = SoundChannel2
K00:A+F7 = SoundChannel3
K00:C+F7 = SoundChannel3
K00:A+F8 = SoundChannel4
K00:C+F8 = SoundChannel4
K00:A+F9 = SoundChannel5
K00:C+F9 = SoundChannel5
K00:A+F10 = SoundChannel6
K00:C+F10 = SoundChannel6
K00:A+F11 = SoundChannel7
K00:C+F11 = SoundChannel7
K00:A+F12 = SoundChannelsOn
K00:C+F12 = SoundChannelsOn

I do wonder why a) somebody didnt post this previoysly b) you didnt look it up yourself; if in doubt, use the source...

---


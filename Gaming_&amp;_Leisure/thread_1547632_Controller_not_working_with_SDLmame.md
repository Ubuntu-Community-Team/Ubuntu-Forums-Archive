---
title: "Controller not working with SDLmame"
date: 2010-08-07
forum: Gaming &amp; Leisure
---

### Post by kakyoism on 2010-08-07
It's driving me crazy.
I installed SDLmame, WahCade, loemu, gmameui, advancedMAME....
Followed the classic how-to post as it exactly says:
[http://ubuntuforums.org/showthread.php?t=545066](http://ubuntuforums.org/showthread.php?t=545066)

The result:
WahCade: doesn't recognize sdlmame or romes. Can't figure out.
loemu: sees my romes, but can't start any of them, no error messages.
gmameui: can start games, can input coins, but when trying to setup controller keys. The only keys that work are the downward arrow, insert coins... function keys (F7 for instance), pause, tab....
advancedMAME: Through advancedMENU, I can see the list of my roms, but can't start any of them, pressed all keys on my keyboard.

When I try using 
sdlmame <rom_name>

It just gives me 
> h-h0-d.3h NOT FOUND
h-l0-d.3h NOT FOUND
h-h1.rom NOT FOUND
h-l1.rom NOT FOUND
h-sh0.rom NOT FOUND
h-sl0.rom NOT FOUND
hook-c0.rom NOT FOUND
hook-c1.rom NOT FOUND
hook-c2.rom NOT FOUND
hook-c3.rom NOT FOUND
hook-000.rom NOT FOUND
hook-010.rom NOT FOUND
hook-020.rom NOT FOUND
hook-030.rom NOT FOUND
hook-da.rom NOT FOUND
ERROR: required files are missing, the game cannot be run.
Ignoring MAME exception: ERROR: required files are missing, the game cannot be run.


The enter key is completely not working! I can't change any key mapping after pressing "tab". Yeah, tab works, it calls up the key mapping setup.

I tried deleting /etc/mame/mame.ini, /etc/sdlmame/mame.ini, ~/.mame/cfg/mame.ini. and the default.cfg of sdlmame. 

None of these worked.

HELP!!

---

### Post by kakyoism on 2010-08-07
bump

---

### Post by 2Karl on 2010-08-07
in GMAMEUI do you have your joypad enabled? I know it sounds daft, but it has foiled me before. Select options > default options > input and make sure "enable joystick" is checked.

Also, select options>GMAMEUI preferences and make sure the correct device is listed in the box. (mine is /dev/js0, yours may vary)

could be you have an old romset which is not compatible with the never version of the emulator

---

### Post by babai on 2010-08-08
Maybe ur bios(neogeo.zip) is an old one. Get the new bios and try again.

---

### Post by kakyoism on 2010-08-08
Thanks guys.
Got sdlmame working in the end.

I found no complete guide to the whole process. Here is mine.
Procedure:
1) Install
```
sudo aptitude install sdlmame 
```
On lucid, it gives you mame 0.136. I remember adding this repo: [http://sdlmame.wallyweek.org/repository/](http://sdlmame.wallyweek.org/repository/) and updated. After this sudo aptitude install sdlmame will give me an extra package "mame{a}" I think. So after this I have /etc/mame and /etc/sdlmame two folders, both having mame.ini and vector.ini in them. Plus ~/.mame/cfg/mame.ini

2) Configuration and paths
I haven't tested which mame.ini would overide the others. But it looks like ~/.mame/cfg/mame.ini will be overriden by /etc/mame/mame.ini at least. And if you delete /etc/mame/mame.ini, your ~/.mame/cfg/mame.ini will not work. So basically you should configure /etc/mame/mame.ini

type ```
mame -createconfig
``` or ```
sdlmame -createconfig
``` if there is no mame.ini under the specified paths.

necessary fields:
rompath
cfg_directory

3) Permission
Make your /etc/mame/mame.ini r/w instead of read-only. This would cause the game complain about errors in mame.c. The error code makes no sense if you try to understand it. All it says is about permission. REMEMBER, if any error happens, a file error.log will be generated in /etc/mame, and the initial permission is r/w. When that happens, running mame will fail the same way as well. So set that file to r/w if applicable. Usually logs are generated because you set the INI field "log" to 1.

3) Key config
Edit ```
~/.mame/cfg/default.cfg.
``` I think it'll be regenerated too if you run ```
sdlmame -createconfig
```

You can set default key mapping in this file so that it becomes default key mapping to all games.

Between <mameconfig version="10"> tag pair, edit the system tag:
```

    <system name="default">
	<input>
        </input>
    </system>

```

Then under <input> tag, 
Use <port> to specify your individual key-mapping
Here is mine
```
<port type="UI_UP">
	<newseq type="standard">KEYCODE_UP OR KEYCODE_8_PAD</newseq>
	</port>
	<port type="UI_DOWN">
	<newseq type="standard">KEYCODE_DOWN OR KEYCODE_2_PAD</newseq>
	</port>
	<port type="UI_LEFT">
	<newseq type="standard">KEYCODE_LEFT OR KEYCODE_4_PAD</newseq>
	</port>
	<port type="UI_RIGHT">
	<newseq type="standard">KEYCODE_RIGHT OR KEYCODE_6_PAD</newseq>
	</port>
	<port type="UI_SELECT">
	<newseq type="standard">KEYCODE_ENTER OR KEYCODE_LCONTROL</newseq>
	</port>

	<port type="UI_CONFIGURE">
	<newseq type="standard">KEYCODE_TAB OR KEYCODE_1 KEYCODE_3</newseq>
	</port>
	<port type="UI_CANCEL">
	<newseq type="standard">KEYCODE_ESC OR KEYCODE_2 KEYCODE_4</newseq>
	</port>

	<port type="START1">
	<newseq type="standard">KEYCODE_1</newseq>
	</port>
	<port type="START2">
	<newseq type="standard">KEYCODE_2</newseq>
	</port>
	<port type="COIN1">
	<newseq type="standard">KEYCODE_5</newseq>
	</port>
	<port type="COIN2">
	<newseq type="standard">KEYCODE_4</newseq>
	</port>
	<port type="START3">
	<newseq type="standard">KEYCODE_3</newseq>
	</port>
	<port type="START4">
	<newseq type="standard">KEYCODE_6</newseq>
	</port>

	<port type="P1_JOYSTICK_UP">
	<newseq type="standard">KEYCODE_W</newseq>
	</port>
	<port type="P1_JOYSTICK_DOWN">
	<newseq type="standard">KEYCODE_X</newseq>
	</port>
	<port type="P1_JOYSTICK_LEFT">
	<newseq type="standard">KEYCODE_A</newseq>
	</port>
	<port type="P1_JOYSTICK_RIGHT">
	<newseq type="standard">KEYCODE_D</newseq>
	</port>
	<port type="P1_JOYSTICKRIGHT_UP">
	<newseq type="standard">KEYCODE_R</newseq>
	</port>
	<port type="P1_JOYSTICKRIGHT_DOWN">
	<newseq type="standard">KEYCODE_F</newseq>
	</port>
	<port type="P1_JOYSTICKRIGHT_LEFT">
	<newseq type="standard">KEYCODE_D</newseq>
	</port>
	<port type="P1_JOYSTICKRIGHT_RIGHT">
	<newseq type="standard">KEYCODE_G</newseq>
	</port>
	<port type="P1_JOYSTICKLEFT_UP">
	<newseq type="standard">KEYCODE_8_PAD</newseq>
	</port>
	<port type="P1_JOYSTICKLEFT_DOWN">
	<newseq type="standard">KEYCODE_2_PAD</newseq>
	</port>
	<port type="P1_JOYSTICKLEFT_LEFT">
	<newseq type="standard">KEYCODE_4_PAD</newseq>
	</port>
	<port type="P1_JOYSTICKLEFT_RIGHT">
	<newseq type="standard">KEYCODE_6_PAD</newseq>
	</port>

	<port type="P1_BUTTON1">
	<newseq type="standard">KEYCODE_J</newseq>
	</port>
	<port type="P1_BUTTON2">
	<newseq type="standard">KEYCODE_K</newseq>
	</port>
	<port type="P1_BUTTON3">
	<newseq type="standard">KEYCODE_L</newseq>
	</port>
	<port type="P1_BUTTON4">
	<newseq type="standard">KEYCODE_U</newseq>
	</port>
	<port type="P1_BUTTON5">
	<newseq type="standard">KEYCODE_I</newseq>
	</port>
	<port type="P1_BUTTON6">
	<newseq type="standard">KEYCODE_O</newseq>
	</port>
	<port type="P2_JOYSTICK_UP">
	<newseq type="standard">KEYCODE_UP</newseq>
	</port>
	<port type="P2_JOYSTICK_DOWN">
	<newseq type="standard">KEYCODE_DOWN</newseq>
	</port>
	<port type="P2_JOYSTICK_LEFT">
	<newseq type="standard">KEYCODE_LEFT</newseq>
	</port>
	<port type="P2_JOYSTICK_RIGHT">
	<newseq type="standard">KEYCODE_RIGHT</newseq>
	</port>
	<port type="P2_BUTTON1">
	<newseq type="standard">KEYCODE_DEL OR KEYCODE_0_PAD</newseq>	
	</port>
	<port type="P2_BUTTON2">
	<newseq type="standard">KEYCODE_END OR KEYCODE_._PAD</newseq>
	</port>
	<port type="P2_BUTTON3">
	<newseq type="standard">KEYCODE_PGDN OR KEYCODE_3_PAD</newseq>
	</port>
	<port type="P2_BUTTON4">
	<newseq type="standard">KEYCODE_INS OR KEYCODE_1_PAD</newseq>	
	</port>
	<port type="P2_BUTTON5">
	<newseq type="standard">KEYCODE_HOME OR KEYCODE_/_PAD</newseq>
	</port>
	<port type="P2_BUTTON6">
	<newseq type="standard">KEYCODE_PGUP OR KEYCODE_*_PAD</newseq>
	</port>
```

I also use 
```

<remap origcode="KEYCODE_UP" newcode="KEYCODE_8_PAD" />

``` to have one-to-many mapping.

Here is the complete ~/.mame/cfg/default.cfg of mine
```
<?xml version="1.0"?>
<!-- This file is autogenerated; comments and unknown tags will be stripped -->
<mameconfig version="10">
    <system name="default">
	<input>
	<remap origcode="KEYCODE_UP" newcode="KEYCODE_8_PAD" />
	<remap origcode="KEYCODE_DOWN" newcode="KEYCODE_2_PAD" />
	<remap origcode="KEYCODE_LEFT" newcode="KEYCODE_4_PAD" />
	<remap origcode="KEYCODE_RIGHT" newcode="KEYCODE_6_PAD" />
	<remap origcode="KEYCODE_DELETE" newcode="KEYCODE_0_PAD" />
	<remap origcode="KEYCODE_END" newcode="KEYCODE_._PAD" />

	
	<port type="UI_UP">
	<newseq type="standard">KEYCODE_UP OR KEYCODE_8_PAD</newseq>
	</port>
	<port type="UI_DOWN">
	<newseq type="standard">KEYCODE_DOWN OR KEYCODE_2_PAD</newseq>
	</port>
	<port type="UI_LEFT">
	<newseq type="standard">KEYCODE_LEFT OR KEYCODE_4_PAD</newseq>
	</port>
	<port type="UI_RIGHT">
	<newseq type="standard">KEYCODE_RIGHT OR KEYCODE_6_PAD</newseq>
	</port>
	<port type="UI_SELECT">
	<newseq type="standard">KEYCODE_ENTER OR KEYCODE_LCONTROL</newseq>
	</port>

	<port type="UI_CONFIGURE">
	<newseq type="standard">KEYCODE_TAB OR KEYCODE_1 KEYCODE_3</newseq>
	</port>
	<port type="UI_CANCEL">
	<newseq type="standard">KEYCODE_ESC OR KEYCODE_2 KEYCODE_4</newseq>
	</port>

	<port type="START1">
	<newseq type="standard">KEYCODE_1</newseq>
	</port>
	<port type="START2">
	<newseq type="standard">KEYCODE_2</newseq>
	</port>
	<port type="COIN1">
	<newseq type="standard">KEYCODE_5</newseq>
	</port>
	<port type="COIN2">
	<newseq type="standard">KEYCODE_4</newseq>
	</port>
	<port type="START3">
	<newseq type="standard">KEYCODE_3</newseq>
	</port>
	<port type="START4">
	<newseq type="standard">KEYCODE_6</newseq>
	</port>

	<port type="P1_JOYSTICK_UP">
	<newseq type="standard">KEYCODE_W</newseq>
	</port>
	<port type="P1_JOYSTICK_DOWN">
	<newseq type="standard">KEYCODE_X</newseq>
	</port>
	<port type="P1_JOYSTICK_LEFT">
	<newseq type="standard">KEYCODE_A</newseq>
	</port>
	<port type="P1_JOYSTICK_RIGHT">
	<newseq type="standard">KEYCODE_D</newseq>
	</port>
	<port type="P1_JOYSTICKRIGHT_UP">
	<newseq type="standard">KEYCODE_R</newseq>
	</port>
	<port type="P1_JOYSTICKRIGHT_DOWN">
	<newseq type="standard">KEYCODE_F</newseq>
	</port>
	<port type="P1_JOYSTICKRIGHT_LEFT">
	<newseq type="standard">KEYCODE_D</newseq>
	</port>
	<port type="P1_JOYSTICKRIGHT_RIGHT">
	<newseq type="standard">KEYCODE_G</newseq>
	</port>
	<port type="P1_JOYSTICKLEFT_UP">
	<newseq type="standard">KEYCODE_8_PAD</newseq>
	</port>
	<port type="P1_JOYSTICKLEFT_DOWN">
	<newseq type="standard">KEYCODE_2_PAD</newseq>
	</port>
	<port type="P1_JOYSTICKLEFT_LEFT">
	<newseq type="standard">KEYCODE_4_PAD</newseq>
	</port>
	<port type="P1_JOYSTICKLEFT_RIGHT">
	<newseq type="standard">KEYCODE_6_PAD</newseq>
	</port>

	<port type="P1_BUTTON1">
	<newseq type="standard">KEYCODE_J</newseq>
	</port>
	<port type="P1_BUTTON2">
	<newseq type="standard">KEYCODE_K</newseq>
	</port>
	<port type="P1_BUTTON3">
	<newseq type="standard">KEYCODE_L</newseq>
	</port>
	<port type="P1_BUTTON4">
	<newseq type="standard">KEYCODE_U</newseq>
	</port>
	<port type="P1_BUTTON5">
	<newseq type="standard">KEYCODE_I</newseq>
	</port>
	<port type="P1_BUTTON6">
	<newseq type="standard">KEYCODE_O</newseq>
	</port>
	<port type="P2_JOYSTICK_UP">
	<newseq type="standard">KEYCODE_UP</newseq>
	</port>
	<port type="P2_JOYSTICK_DOWN">
	<newseq type="standard">KEYCODE_DOWN</newseq>
	</port>
	<port type="P2_JOYSTICK_LEFT">
	<newseq type="standard">KEYCODE_LEFT</newseq>
	</port>
	<port type="P2_JOYSTICK_RIGHT">
	<newseq type="standard">KEYCODE_RIGHT</newseq>
	</port>
	<port type="P2_BUTTON1">
	<newseq type="standard">KEYCODE_DEL OR KEYCODE_0_PAD</newseq>	
	</port>
	<port type="P2_BUTTON2">
	<newseq type="standard">KEYCODE_END OR KEYCODE_._PAD</newseq>
	</port>
	<port type="P2_BUTTON3">
	<newseq type="standard">KEYCODE_PGDN OR KEYCODE_3_PAD</newseq>
	</port>
	<port type="P2_BUTTON4">
	<newseq type="standard">KEYCODE_INS OR KEYCODE_1_PAD</newseq>	
	</port>
	<port type="P2_BUTTON5">
	<newseq type="standard">KEYCODE_HOME OR KEYCODE_/_PAD</newseq>
	</port>
	<port type="P2_BUTTON6">
	<newseq type="standard">KEYCODE_PGUP OR KEYCODE_*_PAD</newseq>
	</port>
	</input>
	</system>
</mameconfig>
 
```

4) Cheat
Haven't figured this out yet. Because there seems to be a change since MAME 0.129. If anybody knows the step-by-step procedure. Please help!

---


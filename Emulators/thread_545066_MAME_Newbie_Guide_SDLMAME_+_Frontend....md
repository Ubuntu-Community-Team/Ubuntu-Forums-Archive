---
title: "MAME Newbie Guide: SDLMAME + Frontend..."
date: 2007-09-07
forum: Emulators
---

### Post by Scott00 on 2007-09-07
**[CENTER]*Configuring and installing SDLMAME and Frontend on Ubuntu*[/CENTER]**


Just a short and basic newbie guide for setting up MAME on Ubuntu using the most up-to-date packages. After much frustration in finding up-to-date MAME ports for linux that are (fairly) easy to setup, this is what I came up with. Hopefully this guide will be of use to someone wanting to play MAME on Ubuntu, or even setting up a MAME cabinet.



[COLOR="DarkGreen"][SIZE="4"]PACKAGES: [/SIZE][/COLOR]
download and install

[[COLOR="Blue"]SDLMAME[/COLOR]]("http://wallyweek.altervista.org/") -  MAME port; Ubuntu package.
[[COLOR="Blue"]WahCade[/COLOR]]("http://www.anti-particle.com/wahcade.shtml") - Frontend. Get the .deb package

[COLOR="Red"]Edit 09-15-07:[/COLOR] 
added simplier frontends
 
[[COLOR="Blue"]Loemu[/COLOR]]("http://loemu.pegueroles.com/") - Frontend (simpliest)
[[COLOR="Blue"]QMameCat[/COLOR]]("http://www.mameworld.net/mamecat/") - Frontend



[COLOR="DarkGreen"][SIZE="4"]CONFIGURING:[/SIZE][/COLOR]


_[COLOR="DarkRed"]Configuring the frontend[/COLOR]_

Open terminal and type
```
wahcade-setup
```

Switch to the Emulators tab, in the "M.A.M.E." profile, change the Application to [SIZE="3"][COLOR="DimGray"]/usr/games/sdlmame[/COLOR][/SIZE]   and verify application parameters, they should be set to [name]


Now lets set the directories, under List Generation select your roms folder and rom extension (zip), List generation can be kept as XML. Do the same for all of your the artwork directories (snaps, cab, marq, etc). Move to the "M.A.M.E. Only" tab and click generate next to XML field, this will generate the XML list of available games. You can also add your history.dat here.


Now File > Save. But don't close the window just yet.


[COLOR="DarkRed"]_Configuring SDLMAME_[/COLOR]

Open a new terminal and type
```
sudo gedit /etc/sdlmame/mame.ini
```

In WahCade Setup, copy the rom directory and replace the dir after "rompath"... You can also change any other directory you wish, otherwise save and close both.

---------------------

You can now launch Wah!Cade.. >>Applications > Games > Wah!Cade
If you get a blank screen, press Z and select emulator (press 1 to select). 2 for options.


[COLOR="DarkGreen"][SIZE="4"]CUSTOMIZATION / LAYOUT:[/SIZE][/COLOR]

WahCade layout can be customized with the layout editor. 
```
wahcade-layout-editor
```

If you are getting a white background or hard to read text you can goto screen properties and simply add a dark background image. Be sure to save any changes as a new layout file, or make a backup of the original.

[COLOR="DarkGreen"][SIZE="4"]CONTROLS:[/SIZE][/COLOR]

WahCade keys are changed within the setup. Game controls and dips are changed in game by pressing TAB.


---------------------
Check out [[COLOR="Teal"]mameworld.net[/COLOR]]("http://www.mameworld.net/") for art and support files.

---

### Post by BigSilly on 2007-09-07
Cheers for this guide. It's great for plonkers like me who are still finding their way around!

I'm having a bit of bother still though. I've followed your instructions, but I'm still getting a white background which is driving me mental. I went into the layout screen and screen properties, but it's showing that I should have a black background. I've changed it to some other colours and saved it, but I'm still getting the white background. What do you reckon I should do?

---

### Post by Scott00 on 2007-09-07
> **BigSilly said:**
> 
I'm having a bit of bother still though. I've followed your instructions, but I'm still getting a white background which is driving me mental. I went into the layout screen and screen properties, but it's showing that I should have a black background. I've changed it to some other colours and saved it, but I'm still getting the white background. What do you reckon I should do?
I haven't had a lot of time messing around with this particular frontend (or layout) yet, but I just set a background image rather than changing the color.

---

### Post by Scott00 on 2007-09-07
SDLMAME just released a new version today.   0.118u5

---

### Post by BigSilly on 2007-09-08
Cool! 

/grabs

---

### Post by trinireddman on 2007-09-09
How do you install on feisty amd64?

---

### Post by gigaferz on 2007-09-10
it always stops when is initializing, or decoding a 9x%.....(sdlmame)

someday...

---

### Post by Scott00 on 2007-09-15
I edited the original post to include a couple other frontends which are far simpler and have better UI. Also 0.119 is out.

---

### Post by BigSilly on 2007-09-15
Okay, I've got this but now suddenly my Streetfighter Alpha 3 isn't working. It says I'm missing some files, but it was fine on the last release. Can you help?

Also, what is sdlmame-tools? Is it something that helps you manage your roms, and if so is there a guide anywhere on how to use it? Cheers.

---

### Post by i23098 on 2007-09-15
> **trinireddman said:**
> How do you install on feisty amd64?

yes, please. How :confused: on an amd64 gutsy...

---

### Post by BigSilly on 2007-09-16
> **BigSilly said:**
> Okay, I've got this but now suddenly my Streetfighter Alpha 3 isn't working. It says I'm missing some files, but it was fine on the last release. Can you help?

Also, what is sdlmame-tools? Is it something that helps you manage your roms, and if so is there a guide anywhere on how to use it? Cheers.

Anyone??

:confused:

---

### Post by bokl on 2007-09-27
I've gotten SDLMame and Wah!Cade running fine. Great! Now I want to create backups of the special controls I've set through the menu inside mame, so that I can import them if I reinstall or whatever.

On windows when using MAME32, a file called "default.cfg" was created in a folder called "cfg" next to the "roms" folder. In that file I could easily create complex joystick hotkeys manually. Example:
> <port type="UI_CONFIGURE">
                <newseq type="standard">

                    NOT KEYCODE_LALT NOT KEYCODE_RALT KEYCODE_TAB OR NOT JOYCODE_1_BUTTON7 JOYCODE_1_BUTTON5 JOYCODE_1_BUTTON8 OR NOT JOYCODE_2_BUTTON7 JOYCODE_2_BUTTON5 JOYCODE_2_BUTTON8
                </newseq>
            </port>
Is there a similar file for SDLMame and if so where do I find it? (Please describe exactly where to find it since I still have a hard time understanding the Ubuntu file system)


**edit:**
Never mind, I managed to find my way thanks to this [http://linux.about.com/od/ubuntu_doc/a/ubudg24t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg24t2.htm) file system guide...
I found the file in question at : /var/games/sdlmame/cfg/default.cfg   same format as in windows it seems, so I can probably just import that file
(What i can't understand is why it doesn't show up when I do places > "search for files...", enter "default.cfg" and choose to look in "file system". Does the search skip some folders for some reason?)

---

### Post by nellistc on 2007-12-07
> **BigSilly said:**
> Anyone??

:confused:

If you upgraded sdlmame, you may have to get a newer copy of the rom.

[MAWS]("http://mameworld.net/maws") will help you determine the last time any given rom was updated.

---

### Post by BigSilly on 2007-12-07
Yeah I figured this one out thanks. I've now got MAME version 0.120 and a full set of 0.120 roms, and everything that I want works brilliantly. Including SFIII3rd Strike. What a game!

---

### Post by disturbedite on 2007-12-07
i still prefer to use sdlmame with kxmame, which development has picked up on again, fwiu.

---

### Post by keyboardslave on 2008-01-03
> **disturbedite said:**
> i still prefer to use sdlmame with kxmame, which development has picked up on again, fwiu.

well after trying several of your ideas Disturbedite from many of your posts, i still cant seem to follow your directions. You seem to post a lot of "one line comments" (explaining several things about your bean count). 

These directions were fantastic... WONDERFULL, if you are going to try and teach people things make sure you structure your tutorials like this one.  everything is working 100% thanks you kindly.
Kindest Regards,

---

### Post by disturbedite on 2008-02-06
> **keyboardslave said:**
> well after trying several of your ideas Disturbedite from many of your posts, i still cant seem to follow your directions. You seem to post a lot of "one line comments" (explaining several things about your bean count). 

whatever.  i don't know wth you're talking about.

DoktorSeven has created an updated deb package of kxmame (from svn) with sdlmame support, you might consider adding it to the list of frontends.
its here:
[http://sdcofer.googlepages.com/home](http://sdcofer.googlepages.com/home)

---

### Post by diskotek on 2008-02-11
everything worked fine with your instructions. i can log on wah!cade, i can select the game, the game is loaded but the screen screwed up! there is sound but only glitching on the screen.

i'm using gutsy (with ati radeon x200) with 1440x900 LCD screen

---

### Post by diskotek on 2008-02-12
any solution for that glitching screen?

---

### Post by stevetsc on 2008-02-14
> **i23098 said:**
> yes, please. How :confused: on an amd64 gutsy...

you need to have the amd64 version of gutsy installed on an amd64 compatible system.  If you're running the i386 version of gusty on amd64 platform you won't be able to install the amd64 package.

---

### Post by motoperpetuo on 2008-02-15
For what it's worth, my performance in sdlmame was awful at first, very slow, and very choppy sound. I fixed this by opening mame.ini and changing the autoframeskip parameter (under CORE PERFORMANCE OPTIONS) to 1. 

Not sure what systems that would be necessary on, but it worked wonders on my six-year-old Gateway laptop. Speed is perfect now and audio is almost perfect (just a few crackles and pops here and there). Best of all, the games are now full screen size, something I could never get consistently in kxmame.

Now, does anyone know how to get games to open up in a separate window, rather than just taking over the entire screen? The version of MAME i use in Windows does this. You can even "pause" a game by right-clicking on it.

---

### Post by Zzzach on 2008-02-15
left alt+enter to get it out of full screen.

I still can't get sdlmame to lower the volume

---

### Post by jputman on 2008-02-22
>> I found the file in question at : /var/games/sdlmame/cfg/default.cfg same format as in windows it seems &#8220;   

For reference I think the SDLMAME config file lives at:
/etc/sdlmame/mame.ini

---

### Post by killstheweak on 2008-02-25
> everything worked fine with your instructions. i can log on wah!cade, i can select the game, the game is loaded but the screen screwed up! there is sound but only glitching on the screen.

i'm using gutsy (with ati radeon x200) with 1440x900 LCD screen

Same here, with gutsy radeon mobile, there is a solution tho, if you compile it from source, it runs fine, something must be enabled in the debs that ati drivers dont like, in my compile i just enabled pentiumpro optimizations. Or maybe different versions of SDL used? No idea :P

---

### Post by MarshallClan on 2008-03-16
BIG THANKS... 
 The instructions were On The Money! Say "so long to productivity"... right down the MAME drain!

---

### Post by MaindotC on 2008-03-21
I followed your directions and it worked like a charm with Wahcade, but I think Wahcade is gross so I'm testing out the other frontends.  Why can I not give OP thanks?

keyboardslave don't get too bent out of shape about disturbedite - I know his directions are sometimes cryptic but I think he's helping us develop a methodology for solving a problem and that has the better interests of the open source community in mind.

---

### Post by fletch33 on 2008-04-03
any chance i could get mame working on gutsy ppc? i am trying to find a way to get mame working on my xubuntu ps3 install andi have been searching for an answer for hours.

thanks

---

### Post by Ohwii on 2008-07-09
> **diskotek said:**
> everything worked fine with your instructions. i can log on wah!cade, i can select the game, the game is loaded but the screen screwed up! there is sound but only glitching on the screen.

i'm using gutsy (with ati radeon x200) with 1440x900 LCD screen

I have the same probleme can please someone help

---

### Post by FetalShinobi on 2009-07-23
I got everything installed and i even get the options of running the 2 games i have but when it loads it goes to 99% and takes me to the option screen all over again.....what do i do?

---

### Post by X1R1 on 2009-10-08
same problem as the guy above. everything works but as soon as it loads takes me back to the game selection.

---

### Post by williamts99 on 2009-10-24
> **FetalShinobi said:**
> I got everything installed and i even get the options of running the 2 games i have but when it loads it goes to 99% and takes me to the option screen all over again.....what do i do?


Some games need extra bios roms like neogeo and stvbios added to your roms folder.

Also I had a 99% issue because of pulseaudio, and the fix was to install libsdl1.2debian-pulseaudio

sudo apt-get install libsdl1.2debian-pulseaudio

Hope that helps.
Williamts99

---

### Post by WarrenSH on 2010-05-06
> **Scott00 said:**
> [B][CENTER]*Configuring and installing SDLMAME and Frontend on Ubuntu*[/CENTER]
[/B]


Just a short and basic newbie guide for setting up MAME on Ubuntu using the most up-to-date packages. After much frustration in finding up-to-date MAME ports for linux that are (fairly) easy to setup, this is what I came up with. Hopefully this guide will be of use to someone wanting to play MAME on Ubuntu, or even setting up a MAME cabinet.



[COLOR=DarkGreen][SIZE=4]PACKAGES: [/SIZE][/COLOR]
download and install

[[COLOR=Blue]SDLMAME[/COLOR]]("http://wallyweek.altervista.org/") -  MAME port; Ubuntu package.
[[COLOR=Blue]WahCade[/COLOR]]("http://www.anti-particle.com/wahcade.shtml") - Frontend. Get the .deb package

[COLOR=Red]Edit 09-15-07:[/COLOR] 
added simplier frontends
 
[[COLOR=Blue]Loemu[/COLOR]]("http://loemu.pegueroles.com/") - Frontend (simpliest)
[[COLOR=Blue]QMameCat[/COLOR]]("http://www.mameworld.net/mamecat/") - Frontend



[COLOR=DarkGreen][SIZE=4]CONFIGURING:[/SIZE][/COLOR]


_[COLOR=DarkRed]Configuring the frontend[/COLOR]_

Open terminal and type
```
wahcade-setup
```Switch to the Emulators tab, in the "M.A.M.E." profile, change the Application to [SIZE=3][COLOR=DimGray]/usr/games/sdlmame[/COLOR][/SIZE]   and verify application parameters, they should be set to [name]


Now lets set the directories, under List Generation select your roms folder and rom extension (zip), List generation can be kept as XML. Do the same for all of your the artwork directories (snaps, cab, marq, etc). Move to the "M.A.M.E. Only" tab and click generate next to XML field, this will generate the XML list of available games. You can also add your history.dat here.


Now File > Save. But don't close the window just yet.


[COLOR=DarkRed]_Configuring SDLMAME_[/COLOR]

Open a new terminal and type
```
sudo gedit /etc/sdlmame/mame.ini
```In WahCade Setup, copy the rom directory and replace the dir after "rompath"... You can also change any other directory you wish, otherwise save and close both.

---------------------

You can now launch Wah!Cade.. >>Applications > Games > Wah!Cade
If you get a blank screen, press Z and select emulator (press 1 to select). 2 for options.


[COLOR=DarkGreen][SIZE=4]CUSTOMIZATION / LAYOUT:[/SIZE][/COLOR]

WahCade layout can be customized with the layout editor. 
```
wahcade-layout-editor
```If you are getting a white background or hard to read text you can goto screen properties and simply add a dark background image. Be sure to save any changes as a new layout file, or make a backup of the original.

[COLOR=DarkGreen][SIZE=4]CONTROLS:[/SIZE][/COLOR]

WahCade keys are changed within the setup. Game controls and dips are changed in game by pressing TAB.


---------------------
Check out [[COLOR=Teal]mameworld.net[/COLOR]]("http://www.mameworld.net/") for art and support files.



Is this still up to date?

---

### Post by BigSilly on 2010-05-06
I dunno, but GMAMEUI in the repo's does the trick brilliantly for me. Give it a go.

:)

---

### Post by WarrenSH on 2010-05-10
> **BigSilly said:**
> I dunno, but GMAMEUI in the repo's does the trick brilliantly for me. Give it a go.

:)


I will b trying this out. I hope that it does what I would like it to do. I only want to play a few games when I am on break from class or work.

---

### Post by BigSilly on 2010-05-10
I think you'll really like GMAMEUI. :)

However, if you don't, you could try just creating a desktop launcher to usr/games/sdlmame and just type the game in that you want when you launch it. It is quicker that way, without a front end. I used to do that before GMAMEUI turned up. :)

---

### Post by WarrenSH on 2010-05-11
how do you uninstall this?

---

### Post by BigSilly on 2010-05-11
Uninstall what? GMAMEUI? Just pop into Synaptic, type in gmameui, click completely remove, then apply.

No? Something else?

---

### Post by kai4785 on 2010-08-06
I have GMAMEUI working great, and it runs all my MAME roms fine. However, we're trying to build a cabinent for the machine, and we'd like to play old Nintendo games as well, a mouse-less UI is desirable. Wah!Cade seems to be configurable enough to make this work, but roms that require the NeoGeo bios aren't working properly. 

This is my first real attempt at MAME. I haven't been able to find any good documentation on how to make sdlmame detect and load the appropriate bios.

Anybody have any help on this one? I sorely miss Marvel Vs. Capcom :(

---

### Post by kakyoism on 2010-08-08
I think I should share my experience here.

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

### Post by snide_tripod on 2010-12-23
Help.   Noob here.   I tried the above method from August 8,  2010, and after entering the first sudo command I get this : 

[COLOR=SeaGreen]The following partially installed packages will be configured:
  man-db 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up man-db (2.5.7-4) ...          
Updating database of manual pages ...

      You have to configure "localepurge" with the command

          dpkg-reconfigure localepurge

      to make /usr/sbin/localepurge actually start to function.

      Nothing to be done, exiting .[/COLOR]..

[COLOR=Black]I run the dpkg-reconfigure localepurge[/COLOR], it comes to a blue screen that says configure localepurge and asks me to select language files?  i select ok after choosing en, then it goes on to ask more blabber.   it returns to the terminal screen and prints this:

[COLOR=SeaGreen]Replacing config file /etc/locale.nopurge with new version[/COLOR]

[COLOR=Black]When I try to run the sudo command again it just says the same thing again[/COLOR] :

[COLOR=SeaGreen]The following partially installed packages will be configured:
  man-db 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up man-db (2.5.7-4) ...          
Updating database of manual pages ...
  
      You have to configure "localepurge" with the command
  
          dpkg-reconfigure localepurge
  
      to make /usr/sbin/localepurge actually start to function.
  
      Nothing to be done, exiting .[/COLOR]..

[COLOR=Black]What to do, What to do.[/COLOR]  I need help.  Somebody Please!!!

---

### Post by eternal_sage on 2012-03-10
just realized how old this thread is, so i should make a new thread for my issue, i suppose. the new thread [is here]("http://ubuntuforums.org/showthread.php?p=11760190").

---


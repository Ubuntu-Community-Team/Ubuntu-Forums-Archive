---
title: "xmame Problems"
date: 2007-01-10
forum: Gaming &amp; Leisure
---

### Post by jlacroix on 2007-01-10
Hello everyone, I am trying to get assistance with xmame. 

Basically I want to use xmame with the command line. The reason for this is so I could make a desktop icon for each individual game. For example, one such shortcut would have the command "xmame mk2" etc, so all I would have to do is click on the icon to play the game.

Right now the command works in Konsole. However, the games run small screen and my gamepad will not function.

How can I set up xmame to run full screen and utilize my game pad? Also, I downloaded xmame-sdl to see if that works better but what command do I use to use that version instead of the original one?

---

### Post by DoktorSeven on 2007-01-11
Use **xmame --help** to see all the options available.  You're looking for **-fullscreen** and **-joytype x** where x is what type of input driver method is used: 1 for standard joystick or 5 for xmame.SDL's SDL joystick.

SDL version is **xmame.SDL**.

Better way to launch games is to download **kxmame** and properly configure that -- that is a proper front-end for XMAME.

---

### Post by jlacroix on 2007-01-11
Those options aren't working for me. The -fullscreen option does make it full screen, but in a small window with scanlines. The option to not use any effects (so I won't have scanlines) doesn't work, neither does the joystick option.

Kxmame is okay, however the joystick option there does not work either. I want to avoid opening a program to open a game, I just want to create a shellscript or something for each game with the commands that do work.

Any other ideas? :(

---

### Post by jlacroix on 2007-01-13
Anyone?

Another reason that I can't use Kxmame is because it has no option for Ultimate Mortal Kombat 3. I can run UMK3 from the commandline. 

Here is the command I have so far:
```

xmame.SDL -fullscreen -effect 0 -joytype 5 umk3

```

My joystick now works, and it is full screen now as well. The problem is that even though it is full screen, the resolution is small as there are black borders around the screen. It's running at a resolution that's something like 720 but my resolution is 1280x1024. 

If I run a game in Kxmame, it runs PERFECT full screen at the PERFECT speed. Just no way to use a joystick, as the Kxmame options for joystick do not work. (And it has no UMK3 listed which is definitely a supported game).

So basically I just need the display of xmame to stretch to match my resolution. I checked the help files and almost none of the options has an effect.

Perhaps if I knew what command kxmame uses to run the games, that would probably solve my problem. Kxmame is using xmame.x11 which could be an issue since it won't work with my gamepad, only xmame.SDL will.

---

### Post by Zoyx on 2007-11-28
kxmame problem...

How do you set the resolution?  At full screen, the arcade games appear as a smallish box in the center of the screen.  I have a 1280x1024 LCD.

Within the display properties of each game, there is a "scale video to height:"  selection, but no corresponding "scale video to width:" selection.  So I am able to stretch the game screen vertically, but not horizontally.

Any help would be appreciated.

---

### Post by jlacroix on 2007-11-28
Use the command line and set up an icon to go into the game. On my KDE desktop I create a launcher for Ultimate MK3 for example, and this is the command that works for me:

```

xmame -video-mode 2 -fullscreen -glbilinear -joytype 1 -antialias -joydevname /dev/input/js0 -samplefreq 48000 -dsp-plugin alsa -nocursor umk3

```

Making desktop icons works better for me than frontends, and the command above when placed in a launcher icon activates the game and sets it up the way I need it.

Wow, this topic is a year old almost! I figured it all out since then.

---

### Post by Zoyx on 2007-11-28
I like my GUIs... especially with over 4500 games.  Yeah, I found this thread using google fu.

---


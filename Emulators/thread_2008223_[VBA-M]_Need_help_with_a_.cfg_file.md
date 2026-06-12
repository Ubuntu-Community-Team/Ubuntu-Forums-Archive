---
title: "[VBA-M] Need help with a .cfg file"
date: 2012-06-22
forum: Emulators
---

### Post by doestergaard on 2012-06-22
Hi,

I have tried to figure out how to setup my gamepad to work with emulators. Normally it goes smooth but with the VBA-M emulator, it is harder to crack!

Keep in mind that i use a SDL-version (means non-gui)

So, this emulator has a .cfg file: /etc/vbam.cfg


In this file you put everything in you want, but I don't get this for the controller part:

```
#
# Key configuration (all numbers are in hexadecimal!)
#
# Keys values are in the format YYYYXXXX where YYYY is the device number.
# 0 means keyboard and XXXX is the SDL define for the desired key
# (read SDL_keysym.h).
#
# If YYYY is greater than 0, it means joystick number YYYY-1 and it uses the
# following format for XXXX:
#
# - if XXXX < 20, XXXX is the axis number multiplied by 2. An even number means
#   movement to the negative side (on the X axis, it means left). An odd
#   number means movement to the positive side (on the X axis, it mean
#   right). For the Y axis, negative means up and positive means down.
#   X axis is usally axis number 0 and Y is axis number 1.
# - if 20 >= XXXX > 30, then XXXX is the HAT number multiplied by 4 plus the
#   direction: 0 for up, 1 for down, 2 for right and 3 for left. Example:
#   0021 is HAT 0 down, 0026 is HAT 1 right.
# - if 80 >= XXXX > 100, XXXX is the joystick button number (XXXX-0080).
#
# Default key configuration is (value in parenthesis):
#
# Left          Left Arrow  (00000114)
# Right         Right Arrow (00000113)
# Up            Up Arrow    (00000111)
# Down          Down Arrow  (00000112)
# A             Z           (0000007a)
# B             X           (00000078)
# L             A           (00000061)
# R             S           (00000073)
# Start         ENTER       (0000000d)
# Select        BACKSPACE   (00000008)
# Speed up      SPACE       (00000020)
# Capture       F12         (00000125)
# Auto A        Q           (00000071)
# Auto B        W           (00000077)
#
Joy0_Left=0114
Joy0_Right=0113
Joy0_Up=0111
Joy0_Down=0112
Joy0_A=007a
Joy0_B=0078
Joy0_L=0061
Joy0_R=0073
Joy0_Start=000d
Joy0_Select=0008
Joy0_Speed=0020
Joy0_Capture=0125
Joy0_AutoA=0071
Joy0_AutoB=0077

```

I have also SDL-tested my gamepad and got the proper keycodes - but it doesn't seem to work. I have a feeling its because i don't get the YYYY-XXXX part.

I hope that someone with a better knowledge than me can help with this.

Thanks in advance! :)

/Daniel

---

### Post by scottbrandenburg on 2012-08-23
I've been struggling with this for the past couple of days myself. Finally got it working.

I got my gamepad (ps2 controller connected to USB adapter) working fine in gvbam, but wouldn't work from the command line.

I found the following in ~./config/gvbam :

```
[Input]
active_joypad=0
joypadSDL0_left=65536
joypadSDL0_right=65537
joypadSDL0_up=65538
joypadSDL0_down=65539
joypadSDL0_A=65665
joypadSDL0_B=65666
joypadSDL0_select=65672
joypadSDL0_start=65673
joypadSDL0_L=65670
joypadSDL0_R=65671
joypadSDL0_speed=65669
joypadSDL0_capture=65668
joypadSDL0_autoA=65664
joypadSDL0_autoB=65667
```

So I translated the decimal values to hex and put them into vbam.cfg

```
Joy0_Left=10000
Joy0_Right=10001
Joy0_Up=10002
Joy0_Down=10003
Joy0_A=10081
Joy0_B=10082
Joy0_L=10086
Joy0_R=10087
Joy0_Start=10089
Joy0_Select=10088
Joy0_Speed=10084
Joy0_Capture=10085
Joy0_AutoA=10080
Joy0_AutoB=10083
```

Hope this helps!

---

### Post by outlaw2k5 on 2013-06-22
Python Script for generating keymaps in text. It is quick and dirty.


Somewhat unrelated to the original intent of this thread; but I post it in case its useful to someone out there who wants to conf their keyboard. Its a quick a dirty script to generate the keymappings. Especially if you don't want to browse SDL_keysym.h.

you can pipe it to a textfile  like so

```
$ ./<python-script> > <keymap-file>
```

then paste it into your vbam.cfg

or if you use Vim open your: vbam.cfg

```
:r! python /path/to/pyhon/script 
```

and it will be inserted into the file.

```
#!/usr/bin/python

#
#    put whatever key you want to map in the ord('') call.
#

keyconf = {
    'left': ord('a'),
    'right':ord('d'),
    'up':ord('w'),
    'down':ord('s'),
    'A':ord('g'),
    'B':ord('h'),
    'L':ord('t'),
    'R':ord('y'),
    'start':ord('v'),
    'select':ord('b'),
    'speed':ord('`'),
    'capture':125,
    'auto-a':ord('u'),
    'auto-b':ord('j')
}

conftpl = '''
Joy0_Left={left:04X}
Joy0_Right={right:04X}
Joy0_Up={up:04X}
Joy0_Down={down:04X}
Joy0_A={A:04X}
Joy0_B={B:04X}
Joy0_L={L:04X}
Joy0_R={R:04X}
Joy0_Start={start:04X}
Joy0_Select={select:04X}
Joy0_Speed={speed:04X}
Joy0_Capture={capture:04X}
Joy0_AutoA={auto-a:04X}
Joy0_AutoB={auto-b:04X}
'''.format(**keyconf)

print(conftpl)

# will generate the correct keymapping for the keyboard


```

---


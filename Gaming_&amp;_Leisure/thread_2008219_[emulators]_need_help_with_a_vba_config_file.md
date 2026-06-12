---
title: "[emulators] need help with a vba config file"
date: 2012-06-22
forum: Gaming &amp; Leisure
---

### Post by doestergaard on 2012-06-22
Hi,

I have tried to figure out how to setup my gamepad to work with emulators. Normally it goes smooth but with the VBA-M emulator is a hard to crack!

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

Thanks in advance! :)

/Daniel

---

### Post by doestergaard on 2012-06-22
Whoops. moderators can close this, i made a repost in the correct sub forum.

link: [http://ubuntuforums.org/showthread.php?p=12045937#post12045937](http://ubuntuforums.org/showthread.php?p=12045937#post12045937)

---

### Post by coffeecat on 2012-06-22
> **doestergaard said:**
> Whoops. moderators can close this, i made a repost in the correct sub forum.

Done! :)

---


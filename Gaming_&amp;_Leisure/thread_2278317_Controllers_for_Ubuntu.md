---
title: "Controllers for Ubuntu?"
date: 2015-05-15
forum: Gaming &amp; Leisure
---

### Post by Tadaen_Sylvermane on 2015-05-15
For Kubuntu. Looking for a controller, similar to the Xbox 360 controller although the analog sticks are not needed. I discovered SuperTux and find it very addicting. I would prefer wireless that can be mapped to keyboard keys. I can deal with wired if I need to though. Any suggestions?

---

### Post by efflandt on 2015-05-16
Logitech F710 seems to work fine with Linux including Steam Big picture. Haven't used it that much except to qualify for Steam Machine beta test drawing and for a space game that was under development (Salvation Prophecy). It had a keyboard config gui, but no gamepad config gui (assumed XBox 360 controller). The only thing that did not work as expected was that D-pad worked in menus, but not for zoom and weapon switch in space flight. But I fixed that by pressing D-pad directions for some unused things in keyboard config gui, then transferred those results from the keyboard config text file to the gamepad config file for zoom and weapon switch, then everything worked. I just used the gamepad for space combat and still used familiar WASD keys and mouse for ground movement.

I also tried the F710 with a RC flight simulator and it worked.

If you actually want to have the gamepad work keys instead of gamepad aware games, you might look at **joy2key** package (have not tried it).

PS: I guess the first step in seeing if your controller/gamepad is recognized would be to install **jstest-gtk**, see what it shows for your device, then see what response you get in **Properties** to pressing buttons, triggers, and moving joysticks. From there you can **Calibrate** or change **Mapping** of controls.

For example my F710 is recognized as :

Generic X-Box pad
Device: /dev/input/js0
Axes: 8
Buttons: 11

Although, I have to press a button once on this wireless F710 (which does not have an on/off switch) to wake something up initially before jstest-gtk sees any joystick movement.

---

### Post by mastablasta on 2015-05-19
the xbox controler works in Linux I believe.

---

### Post by aramil248 on 2015-05-22
> **mastablasta said:**
> the xbox controler works in Linux I believe. yes it does i use one for euro truck simulator 2 and it runs great.

---

### Post by oldrocker99 on 2015-05-23
The drivers for the (at least wired) Xbox controller are right in the Linux kernel, and it works perfectly for me.

Not that I'm a big fan of controllers; you can have my mouse and keyboard when you pry them from my cold, dead fingers.;-)

---

### Post by Francesco_Verlato on 2015-05-26
I have a playstation controller but i can't use it and i don't find a driver that work, can anyone help me?

---

### Post by MaxAlexQNEI on 2015-05-29
Hi everybody! Please, help me.
I have **Genius MaxFire Grandias 12V**, but not be work how should.

[IMG]http://www.hwp.ru/Joysticks/Genius.mfgrandias12v/13sm.jpg[/IMG]

I start play in Left4Dead2 through Steam, and I _enable support the gamepad in settings_.
But.
But the key in the settings, the _game__ responds only to press the buttons 1, 2, 3, 4, and sticks_. But Axis 5, 6 (ABS_HAT0X and ABS_HAT0Y) no reaction at all.

_Drivers are only for Windows._

I install the **xboxdrv** and make my config.

```
**[COLOR=#800000][xboxdrv][/COLOR]**
**[COLOR=#008080]evdev[/COLOR]**=/dev/input/event4
[COLOR=#008080]**silent**[/COLOR]=[COLOR=#ff0099]true[/COLOR]

[COLOR=#800000]**[evdev-absmap]**[/COLOR]
[COLOR=#008080]**ABS_X**[/COLOR]=X1
[COLOR=#008080]**ABS_Y**[/COLOR]=Y1
[COLOR=#008080]**ABS_Z**[/COLOR]=Y2
[COLOR=#008080]**ABS_RZ**[/COLOR]=X2
[COLOR=#008080]**ABS_HAT0X**[/COLOR]=Black
[COLOR=#008080]**ABS_HAT0Y**[/COLOR]=White

[COLOR=#800000]**[ui-axismap]**[/COLOR]
[COLOR=#008080]**X1**[/COLOR]=REL_X:[COLOR=#ff0099]10[/COLOR]
[COLOR=#008080]**Y1**[/COLOR]=REL_Y:-[COLOR=#ff0099]10[/COLOR]
[COLOR=#008080]**X2**[/COLOR]=KEY_A:KEY_D
[COLOR=#008080]**Y2**[/COLOR]=KEY_S:KEY_W
[COLOR=#008080]**Black**[/COLOR]=KEY_LEFT:KEY_RIGHT
[COLOR=#008080]**White**[/COLOR]=KEY_UP:KEY_DOWN

[COLOR=#800000]**[evdev-keymap]**[/COLOR]
[COLOR=#008080]**BTN_TRIGGER**[/COLOR]=A
[COLOR=#008080]**BTN_THUMB**[/COLOR]=B
[COLOR=#008080]**BTN_THUMB2**[/COLOR]=X
[COLOR=#008080]**BTN_TOP**[/COLOR]=Y
[COLOR=#008080]**BTN_TOP2**[/COLOR]=RT
[COLOR=#008080]**BTN_PINKIE**[/COLOR]=RB
[COLOR=#008080]**BTN_BASE**[/COLOR]=LT
[COLOR=#008080]**BTN_BASE2**[/COLOR]=LB
[COLOR=#008080]**BTN_BASE3**[/COLOR]=Back [COLOR=#0000ff]#select[/COLOR]
[COLOR=#008080]**BTN_BASE4**[/COLOR]=Start
[COLOR=#008080]**BTN_BASE5**[/COLOR]=TL
[COLOR=#008080]**BTN_BASE6**[/COLOR]=TR

[COLOR=#800000]**[ui-buttonmap]**[/COLOR]
**[COLOR=#008080]A[/COLOR]**=BTN_LEFT
**[COLOR=#008080]B[/COLOR]**=BTN_RIGHT
[COLOR=#008080]**X**[/COLOR]=KEY_E
[COLOR=#008080]**Y**[/COLOR]=KEY_G
[COLOR=#008080]**RT**[/COLOR]=KEY_Q
[COLOR=#008080]**RB**[/COLOR]=KEY_E
[COLOR=#008080] **LT**[/COLOR]=KEY_SPACE
[COLOR=#008080]** LB**[/COLOR]=KEY_LEFTCTRL
[COLOR=#008080]**Back**[/COLOR]=KEY_ESC
[COLOR=#008080]**Start**[/COLOR]=KEY_ENTER
[COLOR=#008080]**TL**[/COLOR]=BTN_RIGHT
[COLOR=#008080]**TR**[/COLOR]=BTN_LEFT

[COLOR=#0000ff]# EOF #[/COLOR]
```

Almost all works. Only one BUT! LT button is pressed after the first seized, and the cursor is constantly rises at a rate of approximately 10 pixels per second.

**!!! **_**I use Ubuntu 15.04**_

P.S. > Sorry for my English. I use translator.

---

### Post by MaxAlexQNEI on 2015-06-02
Hello everybody! **Don't use joy2key, qjoypad and other.**

**_My recipe..._**

Configuration, settings, setups, installing, install joystick/gamepad Genius MaxFire Grandias 12V, Steam BigPicture, Left4Dead2, Linux Ubuntu 12.04+

**01.** Ctrl+Alt+T - TERMINAL
**02.** *sudo apt-get -y install joystick*
**03.** Ctrl+Alt+F1 - CONSOLE
**04.** *sudo su*
**05.** *service lightdm stop*
**06.** Xorg -configure
**07.** *service lightdm start*
**08.** Goto TERMINAL
**09.** *sudo gedit /root/xorg.conf.new*
**10.** Add this text after all content and SAVE, after Close:
```
Section "InputClass"
    Identifier "joystick catchall"
    MatchIsJoystick "on"
    MatchDevicePath "/dev/input/event*"
    Driver "joystick"
    Option "StartKeysEnabled" "False"       #Disable mouse
    Option "StartMouseEnabled" "False"      #support
EndSection
```
**11.** Goto TERMINAL
**12.** *mv /root/xorg.conf.new /etc/X11/xorg.conf*
**13.** Goto CONSOLE
**14.** *service lightdm restart*
**15.** Run Steam in BigPicture mode, before open a "Controller" and setup this.

You can play!

!!! OR, you can make other file "/etc/X11/xorg.conf.d/50-joystick.conf", and write in this file from the step 10.

Thnx for watching! :)

---


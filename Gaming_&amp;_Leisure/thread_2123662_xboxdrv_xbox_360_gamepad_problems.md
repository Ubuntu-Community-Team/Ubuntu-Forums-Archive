---
title: "xboxdrv xbox 360 gamepad problems"
date: 2013-03-08
forum: Gaming &amp; Leisure
---

### Post by pancakefacecake on 2013-03-08
Hi, im ashamed to say im pretty useless with general terminal stuff, but want to learn. any help, if you could explain why you do certain things would be appreciated.

right, when i run ```
sudo xboxdrv
``` i get
```
Error couldn't claim the USB interface: LIBUSB_ERROR_BUSY
Try to run 'rmmod xpad' and then xboxdrv again or start xboxdrv with the option --detach-kernel-driver.
```
when i run ```
rmmod xpad
```
i then get ```
ERROR: Removing 'xpad': Operation not permitted
```

however if run ```
sudo xboxdrv --detach-kernel-driver
```
it then works, i.e. i get all the garbel which means its picking up my pad.

my problem i cant figure out how to then customise the pad, cos i want to do the function ```
sudo xboxdrv --trigger-as-button
```
so i can then use the qjoypad gui to map the triggers as mouse buttons so i can play shooters and stuff. but if i try and write code in after doing the above nothing happens.

im also well out of my head after trying to figure out a way of making a 'daemon' [i dont really know how they work] so that when i plug in the pad it automatically picks it up and i then use the qjoypad thing / play games straight off. 

anyone who has ever bought a 360 pad to use to play games [mostly just 1st person games, and emus/arcades] and could walk me through giving me advice would be well helpful.

if you help me i will most likely love you forever.

thanks a lot for reading!!!!!

---

### Post by xREDEMPTIONx on 2013-03-08
I might be able to help you, while I don't have an actual 360 pad, I  have a logitech F710, which emulates a 360 pad and has all the same  buttons etc. I use xboxdrv on a daily basis for my gaming needs. Lets  start with xpad. To remove the xpad module run the same command with  root permissions.```
sudo rmmod xpad
``` Then you won't need to run xboxdrv with sudo or use the --detach-kernel-driver flag. A more permanent solution would be to blacklist the module from loading at all, described here [http://dev.man-online.org/man1/xboxdrv/](http://dev.man-online.org/man1/xboxdrv/) under the "Running xboxdrv" section.
 Now I would suggest creating a config file. There are many examples included with the xboxdrv source code which you can download here [https://github.com/Grumbel/xboxdrv](https://github.com/Grumbel/xboxdrv) look in the "examples" folder. Here is a the basic config file I use. 
```

[xboxdrv]
silent = true
ui-clear = true
deadzone=4000
deadzone-trigger = 15%
#trigger-as-button = true

[ui-buttonmap]
A=BTN_A
B=BTN_B
X=BTN_X
Y=BTN_Y

START=BTN_START
GUIDE=BTN_MODE
BACK=BTN_SELECT

LB=BTN_TL
RB=BTN_TR

#LT=
#RT=

TL=BTN_THUMBL
TR=BTN_THUMBR

[ui-axismap]
X1=ABS_X
Y1=ABS_Y

X2=ABS_RX
Y2=ABS_RY 

LT=ABS_Z
RT=ABS_RZ

DPAD_X = ABS_HAT0X
DPAD_Y = ABS_HAT0Y

# EOF #

```

 As you can see any flags you would usually run with the xboxdrv command  can be placed at the top of the config file. To run this you would save  this code into an empty text document, give it a name such as  myconfig.xboxdrv, save it somewhere i.e.(/home/yourname/Documents/myconfig.xboxdrv) and  execute the command ```
xboxdrv -c /home/yourname/Documents/myconfig.xboxdrv
``` You should have a working controller now, you can test it jstest-gtk, I recommend installing that if you don't have it.
 So for your particular case of wanting to emulate mouse buttons and such, this can all be done within the config file. I actually have several that I use depending on what games Im playing so you can set stuff up exactly the way you want. Mouse buttons are described as BTN_LEFT,BTN_RIGHT etc.. you would enter that into the config file after the "equals" sign next to the button you want to use. So to make the Right Trigger be mouse button 1 enter RT=BTN_LEFT in your config file. Keyboard buttons are KEY_SPACE,KEY_ENTER etc...
 Here is config I use for my controller when I am surfing the web or watching movies
```

[xboxdrv]
ui-clear=true
silent = true

[axis-sensitivity]
X2=-0.5
Y2=-0.5

[ui-axismap]
x2^dead:4000 = REL_X:750:-1
y2^dead:4000 = REL_Y:750:-1


y1^dead:6000^invert = rel-repeat:REL_WHEEL:1:50
x1^dead:6000 = rel-repeat:REL_HWHEEL:1:50

lt = KEY_VOLUMEDOWN:20
rt = KEY_VOLUMEUP:20

[ui-buttonmap]
a = BTN_LEFT
b = BTN_RIGHT
x = BTN_MIDDLE
y = KEY_ENTER

rb = BTN_LEFT
lb = BTN_RIGHT

tl = KEY_BACKSPACE
tr = KEY_SPACE

dl = KEY_LEFT
dr = KEY_RIGHT
du = KEY_UP
dd = KEY_DOWN

start = KEY_FORWARD
back  = KEY_BACK
guide = KEY_ESC

# EOF #


```
 I cant help with the daemon stuff as I don't use it but all the info is on the help site I linked to above. Feel free to ask anymore questions and I'll try to help!

---

### Post by pancakefacecake on 2013-03-09
Thanks, this is really helpful, so i can use these config files instead of the qjoypad GUI. but if i wanted to run a config that left the buttons blank [so i could use qjoypad to map buttons and advanced settings] but still made the triggers buttons like you did with the, #trigger-as-button = true, line. i could leave the ui-buttonmap lines blank for example
```

[COLOR=#000000][FONT=Ubuntu Mono][ui-buttonmap][/FONT][/COLOR]
a =
b = 
x =  
```

and so BTN are all mouse buttons, like BTN_MIDDLE is the middle mouse button? 

sorry for being needy.

---

### Post by pancakefacecake on 2013-03-09
Also, i added the xpad to blacklist config. but i still get the 
```
-- [ ERROR ] ------------------------------------------------------ Error couldn't claim the USB interface: LIBUSB_ERROR_BUSY
Try to run 'rmmod xpad' and then xboxdrv again or start xboxdrv with the option --detach-kernel-driver.
```

thanks for your patience

---

### Post by xREDEMPTIONx on 2013-03-09
About the xpad module, did you reboot after adding the module to the blacklist? If so and it's still not working just go back to using --detach-kernel-module flag at the end of your command. 
 So yes there is really no need for qjoypad because you can do everything you want within the config file. If you want something to be ignored in the config file though just put # symbol in front of the line or remove it completely. So for the first config I posted, to have the triggers act as buttons instead of axis you would _remove_ the # in front of trigger-as-button = true line. Then notice I have LT and RT under both [ui-axismap] and [ui-buttonmap]. Remove the # from LT and RT under buttonmap and put them in front of LT and RT under axismap. Your triggers are now recognized as buttons. Note that this actually isn't needed to make them act as mouse buttons or keyboard keys though. Just adding the BTN_LEFT or KEY_SPACE while they are still recognized as axis will still make them emulate those keys or mouse buttons. BTN_ can be mouse or gamepad buttons, but BTN_MIDDLE is for the middle mouse button. So a config that makes the triggers act as buttons and emulate mouse button left and middle would look like this
```

[xboxdrv]
silent = true
ui-clear = true
trigger-as-button=true

[ui-buttonmap]
LT=BTN_MIDDLE
RT=BTN_LEFT

# EOF #


```

---

### Post by pancakefacecake on 2013-03-09
yeah ill just add that tag everytime. not that much hassle. 

yeah thanks about all this, think i understand enough to use the guides on xboxdrv website now. all working nicely.

thanks again!

---

### Post by xREDEMPTIONx on 2013-03-09
your welcome! :)

---


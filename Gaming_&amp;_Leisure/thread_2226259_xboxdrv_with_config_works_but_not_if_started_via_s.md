---
title: "xboxdrv with config works but not if started via shell script."
date: 2014-05-26
forum: Gaming &amp; Leisure
---

### Post by thenephilim10 on 2014-05-26
Hello All

I am currently playing Oolite and having started with keyboard control then going on to mouse control I eventually dug out an original xbox controller to use.

I had modded it 5 years ago, when I first changed to Linux, to have a bash with. I have installed xboxdrv and blacklisted xpad. All other requirements have been met.

It's taken a couple of weeks for me to get the hang of it but I have a working config file to use the controller with for Oolite.
All well and good.

So to use it and call up the game in terminal I use this -

```
sudo xboxdrv --config ~/oolite.xboxdrv ~/GNUstep/Applications/Oolite/oolite.app/oolite-wrapper
```

I enter my password and it all works great.

But for my final victory I want to have a menu entry that I click to do the same. I am partway there. Using this -

```
#!/bin/sh

# Start xboxdrv and remember its PID in the variable XBOXPID
xboxdrv --config ~/oolite.xboxdrv &amp;
XBOXPID=$!

# Give xboxdrv a second to startup and create the device
sleep 1

# Launch your favorite game
/home/fenris/GNUstep/Applications/Oolite/oolite.app/oolite-wrapper

# Kill xboxdrv and wait for it to finish
kill $XBOXPID
wait $XBOXPID

# EOF #
```

This too works. BUT, There had to be one somewhere, there is one slight problem and this is the difference between running with the terminal or with the script:

When running with the script -- Y2, used for yaw control on the controller, DOESN'T work. All other buttons and functions do. When running from the terminal -- Y2 DOES work as do all other buttons and functions. 

I am at a loss as to why this is the case. Can anybody help me sort this issue out please? This is my config file -

```

```
[xboxdrv]
ui-clear=true
silent=true
#deadzone=4000
dpad-as-button=true
trigger-as-button=true

#The sticks. Left is x/y1 Right is x/y2
[ui-axismap]
X1^dead:4000^sen:0.3^resp:-32768:-29365:-26139:-23080:-20180:-17431:-14824:-12353:-10011:-7789:-5683:-3687:-1794:0:1794:3687:5683:7789:10010:12353:14824:17430:20180:23079:26138:29364:32767 = ABS_X
Y1^dead:4000^sen:0.3^resp:-32768:-29365:-26139:-23080:-20180:-17431:-14824:-12353:-10011:-7789:-5683:-3687:-1794:0:1794:3687:5683:7789:10010:12353:14824:17430:20180:23079:26138:29364:32767 = ABS_Y
X2^dead:4000^sen:0.3^resp:-32768:-29365:-26139:-23080:-20180:-17431:-14824:-12353:-10011:-7789:-5683:-3687:-1794:0:1794:3687:5683:7789:10010:12353:14824:17430:20180:23079:26138:29364:32767 = ABS_RX

#The coloured buttons
[ui-buttonmap]
a=KEY_T
b=KEY_I
x=KEY_U
y=KEY_Y

#The white and black buttons. As per the original Xbox controller
[ui-buttonmap]
lb=KEY_S
rb=KEY_W

#The Triggers
[ui-buttonmap]
lt=KEY_M
rt=KEY_A

#The Dpad
[ui-buttonmap]
dl=KEY_E
dr=XK_backslash
du=KEY_C
dd=KEY_J

#The Back/Start buttons
[ui-buttonmap]
#back=
start=KEY_ESC

#The thumbstick buttons
[ui-buttonmap]
tl=KEY_KPASTERISK
#tr=

# EOF #

regards

Neph

---

### Post by thenephilim10 on 2014-05-30
Hi all

I eventually worked out what was going on.

The difference is 'sudo'. With the CLI command xboxdrv has root and can, I believe the term is, 'parse' the config files settings into oolite. The joystick page will show all the settings when you look at it.

With the shell script there is a small issue. To get this to work I had to do the following to xboxdrv -

```
sudo chown root /usr/bin/xboxdrv
sudo chmod +s /usr/bin/xboxdrv
```

This allows the shell script to run xboxdrv and bypass the sudo requirement. But it is imperfect. When run only the Common Joystick axis work X1/Y1. X2/Y2 is not parsed and non of the config button settings will show in the joystick page of oolite. But the button strokes will work regardless.

The YAW control, on X2, you have to set in the joystick page. This is like turning it on so oolite knows there is an X2 present and in fact once done the settings you give X2 in the config file are used. The only other issue I had was wanting to use the 'pitch/roll precision' setting in the oolite joystick page. In my xboxdrv config file I had to set  -

```
ui-clear=true
```

This would normally clear any settings in the oolite joystick page in favour of your config settings to

```
ui-clear=false
```

So you may have to clear any settings found in oolites joystick page to prevent conflicts between it and your config file, except X1/Y1 oddly, and you can then select the 'pitch/roll precision' to function with your controller. With it set to true the joystick page does not list your config settings as mentioned before and although you can activate the YAW control you cannot set any button controls such as the precision pitch/roll.

Until some clever person comes up with a shell script that pops up a little window for your password this is the best I have been able to cobble together from googling. I did find a script that was supposed to ask for your password but it didn't work and I don't know enough to know why and fix it.

Neph

---

### Post by Ranko Kohime on 2014-05-30
gksudo, kdesu, and a variety of other graphical sudo wrappers are available, and at least one is probably already installed on your rig.

---


---
title: "360 controller key mapping.. 4 hours of research and still failing.."
date: 2012-02-03
forum: Gaming &amp; Leisure
---

### Post by MarcosCosmos on 2012-02-03
I'm trying to use my xbox 360 controller to play The Binding of Isaac on steam, it doesn't recognise the xbox controller and so I need to remap the controller inputs as keystrokes. And from what I've read I should be using xboxdrv to do it. So I went and got and I prevented xpad from loading and got it to the point where I can use --help etc, but it won't pick up the controller because I'm missing the uinput and joydev modules, which I have tried to find and researched how to get them but I can't find anything.. So now I'm stuck with absolutely no support for the controller because I can't unblacklist xpad because the file won't save in text editors..

Long story short I'm a noob who understands computers/programming a little, I can write python for example.. But I'm new to linux and am completely clueless regarding bash/terminal.. Could someone please help me get xboxdrv working?

##Edit##

I am trying to run it with this:
```

#!/bin/sh

exec xboxdrv
  --daemon
  --config ./home/isaac.xboxdrv 

# EOF #

```
Where isaac.xboxdrv is:

```

[xboxdrv]
silent=true
deadzone=6000
dpad-as-button=true
trigger-as-button=true

[ui-axismap]
x2=REL_X:10
y2=REL_Y:-10
x1=KEY_A:KEY_D
y1=KEY_W:KEY_S

[ui-buttonmap]
a=KEY_LEFTSHIFT
b=BTN_C
x=BTN_EXTRA
y=KEY_C

[ui-buttonmap]
lb=BTN_RIGHT
rb=KEY_SPACE

[ui-buttonmap]
lt=KEY_Z
rt=BTN_LEFT

[ui-buttonmap]
dl=KEY_4
dr=KEY_2
du=REL_WHEEL:-1:150
dd=REL_WHEEL:1:150

[ui-buttonmap]
back=KEY_TAB
start=KEY_ESC

# EOF #

```

Thanks in advanced,
Marcos Cosmos

---

### Post by MarcosCosmos on 2012-02-03
If people are skipping this under the assumption I have been to lazy to properly look stuff up, I would like to point out that I have researched it, and tried to use 5 different tutorials, but I cannot find ANYTHING on uinput ;-;

---

### Post by MarcosCosmos on 2012-02-09
So.. why is everyone ignoring this? ._.

---

### Post by Perfect Storm on 2012-02-09
> **MarcosCosmos said:**
> So.. why is everyone ignoring this? ._.

It's not ignored. 
1) People don't have the answer(s).
2) People don't understand what you're writing.
3) your question have nothing to do with Ubuntu gaming, better try eg. Xbox360 forum(s).

---

### Post by MarcosCosmos on 2012-02-10
> **Artificial Intelligence said:**
> It's not ignored. 
1) People don't have the answer(s).
2) People don't understand what you're writing.
3) your question have nothing to do with Ubuntu gaming, better try eg. Xbox360 forum(s).

What?! But I'm specifically asking about an ubuntu program, Xboxdrv? And two other modules which apparently I should have but I don't.

How on earth did you draw the conclusion it had nothing to do with ubuntu? It has less to do with the xbox360 than it does to do with ubuntu... Or did in fact ignore my first post?...

It's likely I'm completely misunderstood, I seem to be good at that on forums... But I mean, it appears to be a very basic thing to do, installing this xboxdrv thing, and I can't find one mention of my problem anywhere...

Thanks for saying something though,

---

### Post by MarcosCosmos on 2012-02-20
Ok so it to start up but it isn't sending any input to the game? 

I am trying to run it with this:
```

#!/bin/sh

exec xboxdrv
  --daemon
  --config ./home/isaac.xboxdrv 

# EOF #

```
Where isaac.xboxdrv is:

```

[xboxdrv]
silent=true
deadzone=6000
dpad-as-button=true
trigger-as-button=true

[ui-axismap]
x2=REL_X:10
y2=REL_Y:-10
x1=KEY_A:KEY_D
y1=KEY_W:KEY_S

[ui-buttonmap]
a=KEY_LEFTSHIFT
b=BTN_C
x=BTN_EXTRA
y=KEY_C

[ui-buttonmap]
lb=BTN_RIGHT
rb=KEY_SPACE

[ui-buttonmap]
lt=KEY_Z
rt=BTN_LEFT

[ui-buttonmap]
dl=KEY_4
dr=KEY_2
du=REL_WHEEL:-1:150
dd=REL_WHEEL:1:150

[ui-buttonmap]
back=KEY_TAB
start=KEY_ESC

# EOF #

```
What am I doing wrong? ._.
Thanks in advanced,
Marcos Cosmos

---

### Post by renanyoy on 2012-05-20
did you success in getting your wireless controller working on ubuntu ?

---

### Post by MarcosCosmos on 2012-05-21
Yes I did, sorry that I didn't remember to post to say I had~

Thanks,
Marcos Cosmos

---

### Post by jman0591 on 2012-07-10
Why in the name of all that is good would you not post the solution to your problem?  I'm in the exact same boat that you were.

---

### Post by Geezanansa on 2012-09-19
It would be a good thing if you could share how you got your config file working from script MarcosCosmos.

After copying and  editing your config file then  simply running
```
sudo xboxdrv -s --deadzone 6000 --dpad-as-button --trigger-as-button --ui-axismap "x2=REL_X:10,y2=REL_Y:-10,x1=KEY_A:KEY_D,y1=KEY_W:KEY_S" --ui-buttonmap "a=KEY_LEFTSHIFT,b=BTN_C,x=BTN_EXTRA,y=KEY_C" --ui-buttonmap "lb=BTN_RIGHT,rb=KEY_SPACE" --ui-buttonmap "lt=KEY_Z,rt=BTN_LEFT" --ui-buttonmap "dl=KEY_4,dr=KEY_2,du=REL_WHEEL:-1:150,dd=REL_WHEEL:1:150" --ui-buttonmap "back=KEY_TAB,start=KEY_ESC"
```in terminal will get controller started with those mappings.

That is after ```
 sudo rmmod xpad #to remove xpad module
sudo modprobe uinput #to load uinput module
sudo modprobe joydev #to load joydev module

``` when xboxdrv tells you to.

All this information is from xboxdrv manual available by ```
man xboxdrv
```

Having a script to 1) unload xpad 2) load uinput and joydev 3) launch xboxdrv 4) launch application 5) shutdown xboxdrv when application closed - all automagically would be awesome.

Did you work out the start up script MarcosCosmos?  Please do share!

---


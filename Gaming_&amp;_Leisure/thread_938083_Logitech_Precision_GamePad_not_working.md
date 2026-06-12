---
title: "Logitech Precision GamePad not working"
date: 2008-10-04
forum: Gaming &amp; Leisure
---

### Post by ynell on 2008-10-04
I've scavenged forums/google for answers and have yet to find anything that completely fixes the problem. I've gone through setups with gameports and tried jscalibrator(then uninstalled after reading all the horrible complaints people had). 

I'm trying to use my gamepad with ZSNES. It lets me map the buttons and everything using the controller but it doesn't work in-game. 





I tried to use jscal and couldnt figure it out, now it gives me this:

jeremy@jeremyE:~$ jscal /dev/input/js0
Joystick has 2 axes and 10 buttons.
Correction for axis 0 is broken line, precision is 0.
Coeficients are: 255, 255, -2147483648, -2147483648
Correction for axis 1 is broken line, precision is 0.
Coeficients are: 128, 128, -2147483648, -4227201




Most of what I have changed/tried/done, were according to the instructions here: [http://ubuntuforums.org/showthread.php?t=338457](http://ubuntuforums.org/showthread.php?t=338457)





Any help would be greatly appreciated! :]


Thanks

---

### Post by ynell on 2008-10-05
I just fiddled with it for about an hour, to no avail.. so i'm still open to any suggestions


Thanks :]

---

### Post by dli8ilb on 2008-10-05
this might not be helpful to you, but i have the same controller working (under parsix linux - ubuntu's distant cousin, twice removed)  
don't remember exactly how i got it going, but here's a look at the input of .zinput.cfg located in ~/.zsnes:

```
; Player 1 Input
; Input Device: 0 = Unplugged, 1 = KEYBOARD/GAMEPAD
pl1contrl=1
; Keys for Select, Start, Up, Down, Left, Right, X, A, L, Y, B, R
pl1selk=268
pl1startk=269
pl1upk=259
pl1downk=258
pl1leftk=257
pl1rightk=256
pl1Xk=263
pl1Ak=262
pl1Lk=266
pl1Yk=260
pl1Bk=261
pl1Rk=267
; Turbo Keys for A, B, X, Y, L, R
pl1Atk=0
pl1Btk=0
pl1Xtk=0
pl1Ytk=0
pl1Ltk=0
pl1Rtk=0
; Diagonal Keys for Up-Left, Up-Right, Down-Left, Down-Right
pl1ULk=0
pl1URk=0
pl1DLk=0
pl1DRk=0
```

this controller didn't work right off the bat, and i remember compiling rejoystick and adding a few other packages (don't remember which) and it was ok.

hope this helps you and doesn't add any confusion..
i'm still learning linux, so be careful taking advice from me ;-)

---

### Post by ynell on 2008-10-05
Thanks for the reply :]

I just tried it but unfortunately it didn't work.. and then I tried to just reset the buttons all together and it ended up hanging on me -_- haha

Thanks for your help tho, it was worth a try haha

---

### Post by dli8ilb on 2008-10-05
did you try starting zsnes from a terminal? see if you get any errors.
maybe try deleting the ~/.zsnes folder and reinstalling zsnes.

---

### Post by ynell on 2008-10-05
Yeah i was actually having some problems with my video drivers and wasn't getting any feed back from the forum, so i just reinstalled hardy amd64 and just now finished reinstalled zsnes.. and still no luck :/

would i need to go through calibration.. with a program besides jscalibrator? 

it seems kinda weird to me that i can plug it in and get right to mapping the buttons using the gamepad, but it still not work in game ='(

---

### Post by ynell on 2008-10-05
Oh yeah i forgot, i ran zsnes through terminal and got this:

jeremy@jeremy-desktop:~$ zsnes32
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

Audio Opened.
Driver: OSS audio driver output 
Channels: 2
Rate: 32000

Device 0 Logitech Logitech(R) Precision(TM) Gamepad
  2 axis, 10 buttons, 0 hats, 0 balls





So according to the last part.. it looks like it detects it? o.0

---

### Post by dli8ilb on 2008-10-05
yeah, odd! the terminal output looks the same as mine, so that's no help..hmmm
i'll just keep throwing some ideas at you...:-)
in zsnes > config > devices, is game pad selected?
have you tried using a different USB port?
how about different roms?
does the game pad work with any other games/emulators (i.e. snes9x)?
run ```
modprobe evdev
``` from the terminal and see if it works then.

---

### Post by ynell on 2008-10-05
Thanks for your replies :]

i just tried those things and still to no avail ='( 

Would it make a difference if my js0 files in /dev/ and /dev/input are owned by root?

---

### Post by SunnyRabbiera on 2008-10-06
I never liked logitech in terms of controllers, if possible try to find a saitek online,

---

### Post by ynell on 2008-10-06
haha yeah i had been wanting to get a gamepad for a while.. and saw this one at GameStop for 10$ and figured why not.. haha more of an impulse-buy xD

---

### Post by dli8ilb on 2008-10-06
try creating another user account and see if it works there.
i'm not sure about the js0 files, but when in doubt try becoming root and running zsens, ya never know.  hey when you set the keys in zsnes, you say they are recognized..but what do they say next to up down left right etc..mine are J03, J02 etc.

how about just posting the contents of ~./zsnes/zsnesl.cfg for comparison.

running out of ideas here, mate :-)  anyone else want to chime in?

---

### Post by ynell on 2008-10-06
I tried running as root.. didn't help.. just got the weird sound issue haha

yeah my zsnesl.conf says the same thing as yours >.< i'm running out of ideas as well :/

You said before that you installed some other packages or something to get yours to work... any chance you remember what they were?

Maybe the precision just isn't compatible or something

---

### Post by ynell on 2008-10-06
Oh and i did uhh... i think its "cat -c /dev/js0" or something like that, and it worked just fine..

so i dunno :/

---

### Post by dli8ilb on 2008-10-06
the packages i mentioned earlier were the dependencies for compiling rejoystick: [http://rejoystick.sourceforge.net/](http://rejoystick.sourceforge.net/)
i think i installed a few others like xserver-xorg-input-joystick and libjsw2 off the top of my head.


hmm..did you try creating another user account?  
maybe do ```
modprobe joydev
```

---

### Post by ynell on 2008-10-06
hmm well i installed the packages besides rejoystick.. which i can't seem to find a 64 bit for.. and its not letting me force install ='( so i'm lost with that one


the others worked fine but still no working gamepad >.<

Thanks for the suggestions tho haha i think after a while we'll figure it out.. just from having nothing else to try

---

### Post by ynell on 2008-10-06
ok i lied i got it to install.. now i'm having trouble how to get the dumb thing to work -_- i mean i can press buttons and stuff lights up.. but it doesn't seem to make much sense >.<

and now its giving me a seg fault when trying to run it :/

---

### Post by klikklak on 2008-10-06
The precision works just fine, I've got one.  I think I didn't have to configure it at all, it just worked.  You could try checking links from /dev/js0 -> /dev/input/js0, to see if that makes a difference.  Otherwise return it to the store and get a new one.

---

### Post by dli8ilb on 2008-10-06
not sure how relevant this is, but in the folder: /dev/input/by-id there is a link to character device called usb-Logitech_Logitech_R__Precision_TM__Gamepad-joystick leading back to /dev/input/js0

---

### Post by ynell on 2008-10-06
Thanks for your replies guys :]

@klik - I'd return it, but it seems to be working in every aspect.. except in games haha. and somewhere along the lines i remember doing that link haha thanks tho :]

@dli8 - Yeah i have that too..



Sense it worked for you without having to config anything.. maybe i have something pre-installed that keeps it from working.. is it possible it doesn't work for 64 bit.. or is that a stupid question lol


Again, thanks for your replies

---

### Post by dli8ilb on 2008-10-06
it's too bad no one from high up with more knowledge/experience hasn't addressed this issue yet or made any suggestions..
hopefully it will catch the attention of a developer/linux guru.  have you filed a bug with launchpad?

sounds more and more like a new controller is in your future..heh
and just to show how 'out of ideas' i am..if you really want to spend some time on this, what you could try is grabbing a bunch of different linux distros, older version(s) of ubuntu and testing in the live cd environment.  that would be pretty extreme for a $10 gamepad though.  but on the other hand, that's how i learned what little i know about computers/linux in the first place.  roll the sleeves up and get dirty.  oh and break stuff in the process :-) 

distros i can recommend to you are parsix, sabayon, wolvix, xubuntu, damn small linux, puppy and arch.  good luck
:guitar: & don't give up!

---

### Post by ynell on 2008-10-06
ehh the distro idea is to much work for me lol xD thanks for all your help tho dli8, its appreciated :]

But yeah.. some advice/suggestions from more experienced users would be nice :/

---

### Post by ynell on 2008-10-07
If anyone out there can give me blunt, cut and dry set of directions on how to do this, without directing me to, or quoting an already posted "how-to" or something, it would be pretty amazing haha :]   and don't be afraid to treat me like i'm a tard xD

I've tried most everything.. So if someone wants me to terminal something and post it or whatever... id be happy to

maybe amd64 comes with packages that keep gamepads from working in certain programs and all i need to do is uninstall them.. like the way jscalibrator and other calibration programs do.

Everything else so far seems to work just fine tho.. I've gone through most every "how-to" and such i can find online, and i always get the output i'm supposed to.. its just that when it comes time to play the game.. it doesn't work.



Any suggestions at all are appreciated :]



Thanks

---

### Post by ynell on 2008-10-07
perhaps someone knows of another forum i could post this for a good response? not that there aren't extremely smart people at ubuntuforums, just figured might as well try and incrase my chances of finding a solution

---

### Post by ynell on 2008-10-10
problem solved!! just.. in a different manner..

i ended up returning my logitech precision and buying a dual action, and it worked out of the box..

so whether the precision was defected or not compatible in some way, i'm not sure..

But thanks for the help nonetheless :]

---


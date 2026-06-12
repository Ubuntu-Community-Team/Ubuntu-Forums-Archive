---
title: "USB controller issues"
date: 2007-06-28
forum: Gaming &amp; Leisure
---

### Post by El Flavio on 2007-06-28
I just got a NES to PC controller adapter to play my roms on emulator (GFCE ultra nes), but I am having some trouble. I put in the input buttons (it does recognize i press the button) and when I press execute to play the rom, only the D pad buttons respond. I have tried this on 2 or 3 emulators in Ubuntu and I get the same result. It is not the controller, it works fine in my Windows emulator program. If it helps, when I configure the buttons in GFCE, If I press A, B, Start, or Select, the configuration window thinks it is multiple presses and go through half the list of buttons, so I have to barely tap the button to get to the next button input. Help would be appreciated :)

---

### Post by po0f on 2007-06-28
El Flavio,

Have you tried using [jscalibrator](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=jscalibrator&searchon=names&subword=1&version=all&release=all) to calibrate it?  The kernel possibly thinks that the buttons are axes.  (jscalibrator is in the universe repo so if it isn't already enabled you'll have to enable it to install through apt/synaptic.)

---

### Post by El Flavio on 2007-06-29
> **po0f said:**
> El Flavio,

Have you tried using [jscalibrator](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=jscalibrator&searchon=names&subword=1&version=all&release=all) to calibrate it?  The kernel possibly thinks that the buttons are axes.  (jscalibrator is in the universe repo so if it isn't already enabled you'll have to enable it to install through apt/synaptic.)

I installed the program and calibrated my controller, but when i got to input the buttons in the emulator, it wont recognize when I press a d-pad button (also it still does  the thing when I press A, B, Start, or Select). I was looking on the forums and a person had a similar problem[ here]("http://ubuntuforums.org/showthread.php?t=356883&highlight=GFCE+controller").
I tried to do what they did and i got this when I ran the command in terminal 
> austin@austin-desktop:~$ sudo rmmod analog
ERROR: Module analog does not exist in /proc/modules


what do I need to do?

EDIT: attached is my .joystick file from the jscalibrator.

---

### Post by AR_Kozz on 2007-06-30
if you tried to "rmmod" the analog module, and you got a "does not exist" message, it's because the analog module wasn't active. It would be if you'd typed 

sudo modprobe analog

in the past.

I am having similar troubles to you with my ps3 sixaxis controller, which is so suped-up that feisty says it has 28 axes. jscalibrator recognizes and calibrates both thumbsticks, the d-pad and all the buttons (feisty can't do the motion-sensing axes yet) but in a game, like bzflag, the only things that work are the d-pad, the two bottom shoulder buttons and the start button. Dang!

---

### Post by El Flavio on 2007-06-30
> **AR_Kozz said:**
> if you tried to "rmmod" the analog module, and you got a "does not exist" message, it's because the analog module wasn't active. It would be if you'd typed 

sudo modprobe analog

in the past.

I am having similar troubles to you with my ps3 sixaxis controller, which is so suped-up that feisty says it has 28 axes. jscalibrator recognizes and calibrates both thumbsticks, the d-pad and all the buttons (feisty can't do the motion-sensing axes yet) but in a game, like bzflag, the only things that work are the d-pad, the two bottom shoulder buttons and the start button. Dang!

by what do you mean "in the past"? I restarted my computer and did the "sudo modprobe analog" command and terminal did not give me a message > austin@austin-desktop:~$ sudo modprobe analog
Password:
austin@austin-desktop:~$

Then I tried the "sudo rmmod analog" command and got the same error message. I don't think I'm udnerstanding what you are trying to say...

---

### Post by El Flavio on 2007-07-01
I found this program for windoze called[ joytokey]("http://www.electracode.com/4/joy2key/JoyToKey%20English%20Version.htm") which converts joystick input into keyboard input. Is there a program like this for Linux (and would it solve my problem)?

[COLOR="Red"]**EDIT**[/COLOR]: I found a program called [qjoypad]("http://qjoypad.sourceforge.net/"), and got it running. I inserted the keys that I wanted to correspond with the gamepad and did the same in the emulator. I started up my ROM and had one problem. It was with the A. B, Start, Select buttons. When I press one of those buttons, they seem to act as if they were on Autofire. Its not the emu or qjoypad. Is there a way to "calibrate" (don't know if that is the right word for it) the A. B, Start, Select buttons? Or am I missing any drivers?

---

### Post by El Flavio on 2007-07-07
Bump

Does anybody know how to fix my problem?

[COLOR="Red"]UPDATE:[/COLOR] I got a pic of what happens when I press a button (a,b, start, select) "[IMG]http://i141.photobucket.com/albums/r71/Austin_is_cool_2006/screenshot4.png[/IMG]" in jscalibrate. Hope this can help someone help me.

---

### Post by El Flavio on 2007-07-14
Bump. 

Please any help? I'm dying to play my nes games in all their 8-bit gloriness with my controller.

---

### Post by tenkamuteki82 on 2007-10-18
me too!

---

### Post by acoustibop on 2007-10-18
@El Flavio: if you're still having these issues (and I'd hope that, by now, you're not), get rid of jscalibrator.  A number of people (myself included) have found that it kills the directional pad and analog sticks of controllers.

You didn't say what controller and adapter you're using, so it's difficult to say anything about your pre-jscalibrator issues.  However, Gutsy is supposed to have much improved controller recognition, and may well fix things like this - certainly people have posted that pre-release versions have done so.

@tenkamuteki82: you too what?

---


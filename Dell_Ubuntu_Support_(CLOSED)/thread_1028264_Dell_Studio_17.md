---
title: "Dell Studio 17"
date: 2009-01-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cloudslayer on 2009-01-02
Hello,

I've recently bought a dell Studio 17 laptop, and I've been trying to get linux working on it properly, it mostly works, but there still are some problems. I some of these are nitpicking, but some are quite important (especially 2 and 3, and possibly 1 and 4):

1) Reboot doesn't work (a regular shutdown works as it should, but when I try to reboot the system just hangs on a black screen)

2) I think my colours are too limited... gradients are quite visible, and I believe more visible than those in Vista (256MB ATI Mobility RADEON HD 3650, restricted drivers been installed)

3) I'm not really sure about this one, but I have the feeling that the screen 'flashes' a bit which I don't have with vista... Could this be cause by some power setting?

4) Compositing effects seem to be quite slow compared to Vista's compositing (which is quite odd)

5) When compositing is turned on and i click on some menus it first shows some grapical garbage before showing the menu (I already had this on my previous laptop and I have a hunch this could be a buffer which isn't emptied before use)

6) Finally when the computer starts and shuts down a screen is shown with a progress bar and the kubuntu logo, but for some odd reason there are some glitches on the screen as parts of the logo are repeating

A few technical details:
	Intel® Core™2 Duo Processor T9400 (2,53 GHz, 1066 MHz FSB, 2 MB L2-cache)
	4096MB 800MHz Dual Channel DDR2 SDRAM [2x2048]
	256MB ATI Mobility RADEON HD 3650
	17,0-inch WUXGA+ CCFL (1.920 x 1.200) 

thanks,

---

### Post by jrobbo on 2009-01-26
Hi,

I also have a Dell Studio 17 running Ubuntu 8.10, and am having some of the same problems as you, as well as a few others. Did you find any solutions any of the issues that you posted?

1) Reboot is working fine for me, that's a strange one, maybe something wrong in the BIOS settings?
2) I don't have any problems with colours, also running the restricted drivers with the same ATI 3650 card
3) Not getting any screen flashes
4) I agree, compositing is quite slow compared to vista
5) I get exactly the same symptoms sometimes when opening a menu, but not always
6) I get exactly the same problem on startup, and you're the first person i've found that has mentioned it, I thought it was just me! :)

In addition, I also have problems with:
1) My microphone doesn't work. The Studio 17 came with 2 different sorts of microphone, i'm using the built in webcam with the microphone array
2) When I adjust the screen brightness using fn+UpArrow and fn+DownArrow, this works fine, except that the little brightness applet stays on the screen and does not go away, and this prevents me from starting new programs etc. The only workaround I have discovered so far is to hit CTRL+ALT+F1 to go to terminal mode, and then CTRL+ALT+F7 to go back to the X Server. 

Does anyone have any hints on any of these issues please?

Cheers

John

---

### Post by cloudslayer on 2009-02-03
I'm really starting to look into the problems now (a few weeks ago I was having exams so I didn't really have the time...)

3) The flashing screen is Kubuntu-related, and was caused by a screen detection service. Turning it off solved the problem and I have since upgraded to KDE 4.2 in which the problem is gone

4) Everything is relatively smooth (I'm guessing bad drivers cause the relatively low framerate), EXCEPT for opening and resizing windows, which takes a small eternity.

I haven't used a microphone yet so I don't know whether it works, but I don't think the volume is as loud it should be, and the speaker doesn't shut up when headphones are plugged in...

Is it just me or is the touchpad placed in a VERY bad location on the keyboard? I keep clicking stuff while I'm typing...

---

### Post by Sanatori on 2009-02-23
If there is one thing that is annoying with the build of the laptop, it is the fact that you do get a lot of accidental clicks when typing. At least I notice I do, too. :D

---

### Post by PyrosBrother on 2010-01-02
hello,

Yes I also have trouble when typping with mouse click that occurs anormaly.
Is there any solution for that point ?

Since few days I could not shutdown the 17 dell studio from panel menu. I should run a sudo shutdown -h now command to get it worked.
Is there any solution for that point too ?


thanks for your help.
regards
Stéphane

---


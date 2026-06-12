---
title: "Mouse settings, Resolution, cannot open games, .exe,any maps, drivers"
date: 2009-05-07
forum: General Help
---

### Post by xeroz23 on 2009-05-07
i dont know where to post this but i have downloaded Ubuntu 9.04 and im totally new to linux
i just wanna know if ubuntu is faster than windows xp?
is opengl better than directx? because im gonna program games.
DirectX = a library which got everything, DirectDraw, Direct3D,DirectInput, etc.
So whats the name of all those in opengl?
i think opengl, glu, etc?

anyway, i got a 32 " LCD screen and as fast as i start it up i get a blank screen because the resolution is 2 high and i cannot change it.

i had 1920x1080
preferred settings: 1368x768 (doesnt seem to work on ubuntu)

is it also possible to change mouse sensitivity?
also i cannot install any drivers or open folders/games
it says some strange errors like, "must open in root" or something
why cant it run any games or .exe's?

---

### Post by ajhunte on 2009-05-07
Your post is slightly vague. 

As far as the mouse sensitivity:
Go to the top bar and goto: Systems>Preferences>Mouse and adjust the settings there.

Running .exe's on linux requires Wine. You can download this by opening a terminal window from the top bar: Accessories>Terminal

As far as drivers go, that is a different story. Do you have an internet connection on that machine currently?

---

### Post by ajhunte on 2009-05-07
sorry, I forgot to type in the command in terminal.

To get wine, once you have a terminal window, type:
$ sudo apt-get install wine

You will be prompted for your password, and then the program will download. It can be found in the same place as accessories and all the other apps. It might take some playing around with to get certain programs to run. When I run wine, I usually just open the terminal window and type:

$ wine nameofprogam.exe

This usually does the trick. Make sure that you are in the same directory as the .exe.

---

### Post by chriskin on 2009-05-07
> **xeroz23 said:**
> i dont know where to post this but i have downloaded Ubuntu 9.04 and im totally new to linux
i just wanna know if ubuntu is faster than windows xp?
is opengl better than directx? because im gonna program games.
DirectX = a library which got everything, DirectDraw, Direct3D,DirectInput, etc.
So whats the name of all those in opengl?
i think opengl, glu, etc?

anyway, i got a 32 " LCD screen and as fast as i start it up i get a blank screen because the resolution is 2 high and i cannot change it.

i had 1920x1080
preferred settings: 1368x768 (doesnt seem to work on ubuntu)

is it also possible to change mouse sensitivity?
also i cannot install any drivers or open folders/games
it says some strange errors like, "must open in root" or something
why cant it run any games or .exe's?

1)yes, if taken care of , almost all linux distros would be faster than xp, and most of the times better in terms of performance.
2)opengl and directx are different, none is better none is worse - my opinion at least
3)for the names, google is your friend, no need to ask something that a simple search can find , right?
4)did you install the drivers on system/administration/hardware drivers?
5)system/prefernces/mouse (did you...try, at least??)
6)drivers for windows are drivers for windows, driver for linux are drivers for linux, thus it is Obvious why you can't install them
7)playing games needs either windows or a way to "emulate" (not the best word , i use it for lack of a better one)windows, possible via wine, which can be found in the synaptic
8 )same reason for the exe files, you can't open windows files in linux without wine or some derivative
9)must open in root is not a bug , it is a feature. it means that you have limited accessibility in order to not screw everything

[B]10)PLEASE in the future SEARCH google and/or the forums first, All of your questions can be found with a simple search - some of them with just common sense (like the mouse thing)
[/B]
11)by the way, welcome to the linux trip, hope you like it


12)wine can open the windows files with just double click or right click and open with wine

---

### Post by xeroz23 on 2009-05-07
Thanks:)but,I forgot to add, whats the best linux operating system for gaming and stuff?
and yes i checked systems, hardware, and it found 1 driver (the Nvidia Graphic driver which i believe is outdated), it says its working but when i change resolution it says it got errors etc so i cant change anything, its like my driver didnt work, i see i have no drivers (i just got internet)
Also my graphic sucks so its very hard to do anything on this OS, i need a new one thats working correctly (a linux based)

---

### Post by chriskin on 2009-05-07
> **xeroz23 said:**
> Thanks:)but,I forgot to add, whats the best linux operating system for gaming and stuff?
and yes i checked systems, hardware, and it found 1 driver (the Nvidia Graphic driver which i believe is outdated), it says its working but when i change resolution it says it got errors etc so i cant change anything, its like my driver didnt work, i see i have no drivers (i just got internet)
Also my graphic sucks so its very hard to do anything on this OS, i need a new one thats working correctly (a linux based)

asking in ubuntu forums which linux distro is better will get you a strangely predictable answer, after all there is a reason that we use ubuntu enough to be on the forums :P

but having the latest wine and some of its derivatives (check wikipedia for the derivatives, most will be propriety though - wine can do a hell of job by itself, and how-to-s can be found at its site), will get you to work as good as possible on any distro.

---


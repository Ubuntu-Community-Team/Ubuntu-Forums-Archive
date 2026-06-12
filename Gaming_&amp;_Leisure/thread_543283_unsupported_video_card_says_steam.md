---
title: "unsupported video card says steam"
date: 2007-09-04
forum: Gaming &amp; Leisure
---

### Post by kubilaycan on 2007-09-04
when i start cs source from steam using wine 9.41 it says my video card is unsupported. to be exact it says in description: Direct3d HAL

dunno what that means

i am using feisty  and have a radeon 9600xt. i have the restricted drivers installed and enabled. i have successfully installed and have been using compiz fusion for weeks now just for information, i dunno it might help.

this might help aswell: 
[email]kubi@k-linux:~/.wine[/email]/drive_c/Program Files/Steam$ cd ~/.wine/drive_c/Program\ Files/Steam && WINEDEBUG=-all wine steam -applaunch 240
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".

the above is the command line for launching cs source as recommended on the wine forum. i dont know if the xfree86 missing thing is ok so i decided to mention it here.

also when i type glxinfo it says direct rendering: no.

this is all the useful info i can think of now... 

now people help meeee

ps. i can run cs source when i ignore the warning message but then even the menu is slow but it does connect to servers.. at least to the testing server for sound and video. it also runs the game in directx 6

---

### Post by disturbedite on 2007-09-05
you prolly need to get direct rendering working.

---

### Post by kubilaycan on 2007-09-05
yeah i think so too. but unfortunately i just cant. can you help me? can anyone help?

---

### Post by disturbedite on 2007-09-05
there are plenty of tutorials, search the board, & google.
for me, it was easy, on an intel integrated chip.  (i can't guarantee that this method will be exactly the same for you).
i just:
1.  installed the appropriate driver.  (intel driver not i810 driver, although one can have both installed now, even though the intel driver obseletes the i810 driver as i understand it).
2.  edited my xorg.conf to add the appropriate info, and switched the video card driver from i810 to intel.
3.  restarted the the xserver, and boom, direct rendering was enabled.

---

### Post by kubilaycan on 2007-09-06
ok thx guys.

i know what the problem was.

direct rendering and xgl dont work together...

so i can log into a normal gnome session without xgl and it says direct rendering enabled...

but now im having troubles actually running cs source.. but i just have to read up some more threads..

cheers

---


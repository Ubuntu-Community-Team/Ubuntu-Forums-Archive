---
title: "Logitech Dual action gamepad drivers?"
date: 2007-08-03
forum: Gaming &amp; Leisure
---

### Post by Hawk__0 on 2007-08-03
Hey i cant get either of my logitech game pads to work under ubuntu.  I am trying to play gridwars and its not working :(

If i go to the device manager, i see my game pad listed.  anything i can do?

---

### Post by cogadh on 2007-08-03
Weird, I have the same Dual Action pad and it has always "just worked" but I just tried GridWars and I have the same problem you do. It seems like the game recognizes the presence of the game pad, but doesn't recognize input from it.

---

### Post by Hawk__0 on 2007-08-03
damn that sucks, does anybody know of a fix?

---

### Post by skore on 2007-09-26
> **mccord said:**
> hi 
i had the same problem with my logitech dual action joypad and grid wars.
grid wars looks for /dev/js0 for the first gamepad, but my pad was under /dev/input/js0
a simple 'sudo ln -s /dev/input/js0 /dev/js0' (the command creates a symbolic link) solved the problem and the pad works now with grid wars :)

I was so happy when I found that myself... Although with the joypad, GW sometimes seem to crash...

---

### Post by vanbeethoven on 2009-03-30
I'm looking at getting the Logitech Dual Action so my kids can play Supertux, Planet Penguin Racer and all the SNES emulated games. So, I get mixed reviews. Is it overal a Ubuntu friendly joypad? Thanks

---

### Post by mancimailman on 2009-05-17
I havent been able to get my dual action logitech to work 
:( I TOO am tryng to play grdwars !!!!!!! but it does not work on others as well

---

### Post by dragon99 on 2009-05-28
I'm getting the exact same problem with jaunty and the game Racer. The logitech dual action has js0 located within /dev/input, yet the game is looking for the js0 in /dev. This doesnt seem to be a problem with other games like torcs, tileracer, vdrift. Logitech, madcats wheel, psx controllers via usb adapter or parallel port all work reasonably well.

I have been trying various workarounds for a couple of weeks now but when I make changes in the current session, shutdown, reboot - the changes I made in the previous session have disappeared. As root is the owner of the file, I did these changes as root, yet the changes only affect the current session. This is true even when I make a link to the /dev/input/js0.

I did these changes from the desktop by opening the dialog box with ALT + F2, and then entering the command gksudo nautilus. This opens a root browser, and I was able to easily change file permissions, make links etc. But the problem is not resolved, as these changes are lost on the next startup. Its no big deal but its very annoying to have to redo the changes everytime I want to play the game.

dragon

---

### Post by jesuansito on 2009-10-31
> **dragon99 said:**
> I'm getting the exact same problem with jaunty and the game Racer. The logitech dual action has js0 located within /dev/input, yet the game is looking for the js0 in /dev. This doesnt seem to be a problem with other games like torcs, tileracer, vdrift. Logitech, madcats wheel, psx controllers via usb adapter or parallel port all work reasonably well.

I have been trying various workarounds for a couple of weeks now but when I make changes in the current session, shutdown, reboot - the changes I made in the previous session have disappeared. As root is the owner of the file, I did these changes as root, yet the changes only affect the current session. This is true even when I make a link to the /dev/input/js0.

I did these changes from the desktop by opening the dialog box with ALT + F2, and then entering the command gksudo nautilus. This opens a root browser, and I was able to easily change file permissions, make links etc. But the problem is not resolved, as these changes are lost on the next startup. Its no big deal but its very annoying to have to redo the changes everytime I want to play the game.

dragon


In my case i manage to work around the problem by changing the snes9x config file:
sudo gedit /etc/snes9x/snes9x.conf
then in the [Unix] section edit the line Joydev1 = (null) to:
Joydev1 = "/dev/input/js0"      
save the file and thats it.

---

### Post by locote on 2010-03-05
ok i got a logitech game pad and Ubuntu sees it, and I'm trying to play second life and it sees it.  But how do i get profiler that comes with the software?

---

### Post by tomas_maly on 2012-06-03
Make sure you have the tiny black switch on the back (of the controller) set to 'X' instead of 'D', so this emulates a generic XBox controller. I had it on 'D' and couldn't get any input response from "cat /dev/input/js0". I Just unplugged it, switched the mode to 'X', plugged it back in, and then it responded from moving the buttons. Using the 'cat' command above should show you extra characters every time you press a button on the controller. If it doesn't respond from your joystick movements, then it's in the wrong mode.

---


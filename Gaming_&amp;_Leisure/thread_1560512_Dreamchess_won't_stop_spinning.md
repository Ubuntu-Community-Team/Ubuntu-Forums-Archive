---
title: "Dreamchess won't stop spinning"
date: 2010-08-24
forum: Gaming &amp; Leisure
---

### Post by Chris1274 on 2010-08-24
When I try to start a new game of Dreamchess, the board just won't stop rotating. Does anyone know of a way to stop it spinning so I can actually play a game?

---

### Post by Chris1274 on 2010-08-25
Am I the only one who plays Dreamchess, or just the only one with a rotating board? :(

---

### Post by zmartant on 2011-02-18
I too am having this issue.  I installed Dreamchess on my AMD custom build PC, running Ubuntu 10.10, without issues.  I installed Dreamchess on my Compaq 2510p laptop and the board just keeps spinning.  I do not know if the cause of the continuous spinning of the board is due to keyboard mapping or the hardware (video (custom=Nvidia, laptop=Intel GMA X3100)).  I will create a dual boot with Windows, as the present OS is Ubuntu 10.10, on the laptop and will post back with the results.

---

### Post by zmartant on 2011-02-19
I did a Windows 7 dual boot install and there were no issues with Dreamchess in Winodws 7.  I believe that Ubuntu is passing on how Ubuntu interprets the keys on my laptop to Dreamchess and for some reason there is a simulation that the CTRL+Left arrow are pressed as those are the key combination to rotate the chess board couter-clockwise.  I have 84 keys on the laptop, but Ubuntu has 105-keys in the setting for the keyboard.  I tried several of the other options (standard 101) with no avail.  I will continue to try and find a resolution for this issue and will post back should I find one.

Update Feb 18,2011 @ 11:16 PM PST:
I found a similar keyboard, Apple->Laptop-->Apply system wide. I noticed that choosing Apple laptop changed the letter casing to opposites, where caps were in lower casing and vise-versa.  I had to set the lock on caps to type in lower case (implementation of new keyboard layout required me to type in the password), BUT the board in Dreamchess stopped spinning!  I then reverted back to 105-key and set that for system wide and then rebooted.  Everything is now functioning as suppose to!  No spinning board in Dreamchess and capitalisation is back to normal.  I do not know what the kink was, but by doing what I did seems to have resolved the issue.

So, if you too are having this issue, the issue is most likely with the layout of your keyboard.

:guitar:

---

### Post by brencameron on 2011-02-20
I also have this same issue. It's fine on the Windows version, as said above. It is a little better than at first - when I tried to play Dreamchess for the first few times, the game crashed completely. Now the board just spins.

---

### Post by Belfry on 2012-08-29
Workaround for some HP/Compaq laptops: change exec line in /usr/share/applications/dreamchess.desktop to Exec=sh -c 'SDL_JOYSTICK_DEVICE=/dev/null dreamchess'. Based on [this]("http://www.dreamchess.org/74.html") page.

---


---
title: "HELP! UBUNTU not working"
date: 2005-12-12
forum: General Help
---

### Post by serlex on 2005-12-12
just turned my VM ubuntu, was good until login screen. when i loged in

this came up, [CLICK ME]("http://server3.uploadit.org/files/serlex-ubuntu.JPG")

i can move around the desktop, but dont know the problem, any ideas? :(

---

### Post by ustrucx on 2005-12-12
It's the X server resolution, is too big. You should try 800x600 or less.

---

### Post by linbetwin on 2005-12-12
[quote=serlex]just turned my VM ubuntu, was good until login screen. when i loged in

this came up, [CLICK ME]("http://server3.uploadit.org/files/serlex-ubuntu.JPG")[/quote]

Pitty, the background seems nice...

---

### Post by serlex on 2005-12-12
[QUOTE=ustrucx]It's the X server resolution, is too big. You should try 800x600 or less.[/QUOTE]

ok, i would i get to change it? 

can not see much, my menu bar is on the left (going downwards)

---

### Post by linbetwin on 2005-12-12
[quote=serlex]ok, i would i get to change it? 

can not see much, my menu bar is on the left (going downwards)[/quote]

ALT+F2 and type the command (ex. gnome-terminal).

---

### Post by serlex on 2005-12-12
:s didnt work, cant see much, isnt there a way of doing it from the menu like windows, rather than going into the terminal (so wanna cry)

---

### Post by Ocxic on 2005-12-12
boot in recovery mode and edit your xorg.conf file to use lower resolutions, by deleting higher ones. then reboot.

---

### Post by serlex on 2005-12-12
just tried that, did lot of stuff at boot, but stoped, last line was 'root@sercan:~#  _' :(

---

### Post by serlex on 2005-12-12
oops didnt know it was a terminal. ok i got the xorg file open, which bit do i need to change and how do i save it? thanks

---

### Post by Ocxic on 2005-12-13
find the screen section and remove the resulutions that you don't want xserver to use crtl-x and prees y to save changes then enter to write to the file, you'll see a list of commands at the bottom of the screen for nano

---

### Post by serlex on 2005-12-13
done thanks, learned alot on the way

---

### Post by serlex on 2005-12-15
ok, my screen went back to  "messed screen" mode. so i had to edit the xorg file again. do you know why it goes back every time i restart

EDIT: can not restart GNOME Display manager either, it 'fail's

---

### Post by serlex on 2005-12-16
anyone? how can i change my refresh rate, atm its 150 :s, cant find it in the xorg file. can someone show me there xorg file plz thanks

---

### Post by serlex on 2006-01-31
hi, im trying to boot my ubuntu on 800x600, but does not work.
 i have edited the Xorg file by changing all the 640x480 to 800x600, but the screen goes all funny.

any ideas?

---

### Post by Ocxic on 2006-01-31
run  sudo dpkg-reconfigure xserver-xorg 
and select your options from there.

---

### Post by serlex on 2006-01-31
tried that did not work. i edited the xorg file as
```
SubSection "Display"
                Depth           16
                Modes           "800x600" "640x480"
EndSubSection
```

the login screen is 800x600, after i login it goes back to 640x480.

---


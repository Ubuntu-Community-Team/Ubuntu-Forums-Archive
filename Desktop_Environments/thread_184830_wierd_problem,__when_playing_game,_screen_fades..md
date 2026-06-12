---
title: "wierd problem,  when playing game, screen fades."
date: 2006-05-30
forum: Desktop Environments
---

### Post by graigsmith on 2006-05-30
When i play tremulous. ill be playing. then the screen will fade  and fade. like im not actually pressing the buttons and using the mouse as if it were the screensaver.

is there a way to disable the fade? so i can test if this is the problem?

---

### Post by graigsmith on 2006-05-30
perhaps the problem is with gnome-screensaver?

is anyone else having this problem?

---

### Post by disturbed1 on 2006-05-30
Have you recently changed your clock settings, say from non UTC to UTC?

---

### Post by graigsmith on 2006-05-30
hmm, not that i know of. i only have ubuntu installed on my computer.

i tried a reboot, mabey that will fix it.

---

### Post by BoyOfDestiny on 2006-05-30
[QUOTE=graigsmith]When i play tremulous. ill be playing. then the screen will fade  and fade. like im not actually pressing the buttons and using the mouse as if it were the screensaver.

is there a way to disable the fade? so i can test if this is the problem?[/QUOTE]

System -> Preferences -> Power Management, change the delay for shutting down the display (the end of the bar sets it to never.)

---

### Post by cmarker on 2006-05-30
I am having the same problem using fceu.  I will be playing a rom using a game pad and then the screen will start to fade and it will take about 10 seconds for it to come back after I press a button or something. I tried the thing suggested above but it is still happening.

---

### Post by chorca on 2006-05-30
It looks like for whatever reason gnome-screensaver isn't being agressive enough about detecting idle time on the computer. It seems that while playing fullscreen 3d games such as Planet Penguin Racer or others, the screen will start to fade out even though the input devices are being used. The only solution right now that i know of is to disable the screensaver while you're playing them.

---

### Post by joepotter on 2006-05-30
[QUOTE=graigsmith]perhaps the problem is with gnome-screensaver?

is anyone else having this problem?[/QUOTE]

I am with 18 boxes at school. Seems "frozen bubble" is the worst offender. 

Another old box was fine with Breezy but now it just fades out every so often even as you use it. Sometimes it comes back, sometimes you must pull to power cord.

Weird.

---

### Post by popkid on 2006-05-30
I also see this behaviour with zsnes, almost like gnome doesn't recognize activity within the application and starts the screensaver

pK

---

### Post by graigsmith on 2006-05-30
Does anyone know if this bug will be fixed? Since dapper is released are they only doing security patches? or will something like this get fixed?

---

### Post by crane on 2006-06-04
Just want to confirm this problem also happens with Quake4. Once it fades out I have to restart the computer to get it back up again.

---

### Post by malacandra on 2006-06-04
OK...this has happened to me twice....but only when logging in from a locked, blank screen (after the screensaver has "blanked"). I get the login window, and it seems like it wants to fade back to life, but it doesn't. Can't get around it and have to hard reset the box.

I should point out: I'm on a desktop, AMD 2400 running 1/2 G of RAM and the Nvidia Drivers.

---

### Post by Megatog615 on 2006-06-20
Confirmed on my box. I have the same problem as the original poster.

---

### Post by fakie_flip on 2007-06-06
I have the same problem in the amd64 Ubuntu.

---

### Post by fakie_flip on 2007-06-06
I found a fix.

[http://ubuntuforums.org/showthread.php?p=1524621](http://ubuntuforums.org/showthread.php?p=1524621)

---


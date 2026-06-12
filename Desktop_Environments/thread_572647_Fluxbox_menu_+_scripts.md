---
title: "Fluxbox menu + scripts"
date: 2007-10-10
forum: Desktop Environments
---

### Post by PurposeOfReason on 2007-10-10
Is there any way at all to make fluxbox run scripts? I know I've seen one where they had it show the time, but it'd be cool to have it run weather scripts and other things conky can do.

---

### Post by TeaSwigger on 2007-10-10
Pardon my newbie-ness but do you mean run as in, having Fluxbox run scripts at startup? If so I'd suppose you might try a safe bash script for a test, and indicate that script in ~/.fluxbox/startup file, with & at the end of the command if it's to run background.

---

### Post by PurposeOfReason on 2007-10-10
I know how to do that, but I'm more looking for the menu to show a script such as, when right clicked  menu comes up, there is a weather option and when I go over that, out pops the weather information.

---

### Post by TeaSwigger on 2007-10-10
Something along the lines of the old Fortune popup (sh -c 'while /usr/games/fortune | col -x | xmessage -center -buttons OK:1,Another:0 -default OK -file - ; do :; done') maybe? That's about all I can point to. Nifty idea. Way beyond me tho'. Good luck :)

---


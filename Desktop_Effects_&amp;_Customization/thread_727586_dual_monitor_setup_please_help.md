---
title: "dual monitor setup please help"
date: 2008-03-17
forum: Desktop Effects &amp; Customization
---

### Post by setotitan on 2008-03-17
hey guys i'm having an issue that i'm hoping is just an easy fix. i'm running a dual monitor setup and i want to make it so that my second monitor is just an extension of my desktop, like i have one big desktop. i've done this a thousand times on windows, but i'm really new to unix and gutsy is making it hard on me. if i have just one monitor on 1024x768 it's fine. but if i go in and check secondary monitor on my screen 2, then set it for 1024x768 when i log out and log back in both monitors work but i have this GIANT screen. i have to scroll really far up to see the navigation bar and i have to scroll really far left or right to find the screens end. i've tinkered around with it for as long as i can take, can anyone help me out?

---

### Post by mrmiserable on 2008-03-17
one possible option is add this to your xorg.conf

open a terminal

enter this 

sudo gedit /etc/X11/xorg.conf

then scroll down to screen

add this 

	SubSection "Display"
		Depth		24
		Modes		"2048x768"  "1024x768"
	EndSubSection
EndSection

save file and close

reboot or ctrl alt backspace log back in and goto 

system/preferences screen resolution there should be a setting now for 2048x768

hope this helps

---

### Post by durand on 2008-03-18
If you have an nvidia card, nvidia-config works a charm...

---

### Post by setotitan on 2008-03-18
OK i got it, just needed to run "sudo nvidia-settings" activate the display, then activate twin view. my only question is the task bars at the top and bottom only extend the length of my main monitor. is there a way to make it so they stretch across the length of both screens?

---

### Post by durand on 2008-03-19
Sorry, I did mean nvidia-settings. I'm not sure about the stretching. Are you using twin view or making them work as separate screens?

---

### Post by setotitan on 2008-03-19
twin-view..

---

### Post by durand on 2008-03-20
hmm...it works here...

---


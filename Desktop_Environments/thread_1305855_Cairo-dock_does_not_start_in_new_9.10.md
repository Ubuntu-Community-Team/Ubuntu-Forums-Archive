---
title: "Cairo-dock does not start in new 9.10"
date: 2009-10-30
forum: Desktop Environments
---

### Post by Malfet on 2009-10-30
Cairo-Dock always displays settings window. Once I close it - ot immediatelly pop up again and the cairo itself does not start. Is it a common bug for everyone after the upgrade?

---

### Post by megamania on 2009-10-30
> **Malfet said:**
> Cairo-Dock always displays settings window. Once I close it - ot immediatelly pop up again and the cairo itself does not start. Is it a common bug for everyone after the upgrade?
It works for me on Karmic, but I clean-installed the Beta and then clean-installed Cairo (i.e. I didn't use the previous settings).

---

### Post by pi4r0n on 2009-10-30
Works fine for me after an upgrade. If it does not for you just re-install it :)

Ta

pi4r0n

---

### Post by xjb2003x on 2009-10-30
I had a problem with cairo-dock autostarting after a reboot. I wasn't able to find anything in the dock settings where you could make it autostart, so I just added it to the startup applications.  cairo-dock -c is the command I used.

---

### Post by Cavsfan on 2009-10-31
> **Malfet said:**
> Cairo-Dock always displays settings window. Once I close it - it immediatelly pop up again and 
the cairo itself does not start. Is it a common bug for everyone after the upgrade?

Same exact thing for me. I upgraded to 9.10 yesterday and afterwards the cairo-dock which worked
perfectly before, did not start.
When I clicked on the Open GL icon, it brought up the maintenance settings window. When I close it,
it comes back over and over again. I tried installing it and re-installing it, it still does the same thing.
Not sure if I did it right, so I will try some things and report back.

Forgot to mention that it is now in Applications > Accessories and it used to be in Applications > System Tools.

---

### Post by Cavsfan on 2009-10-31
I un-installed cairo dock, rebooted, then installed the Karmic Koala version from this updated page:
[Here]("https://help.ubuntu.com/community/CairoDock")
And still I get the same thing.
I am getting some other strange errors like when I open a window it goes to the top of the screen
and I cannot resize or move it.
How can I go back to Ubuntu 9.04 w/o doing a re-install? I can do that as I have all my DEBs on DVD.
Just wondering if there is an easier way.
Thanks

---

### Post by Cavsfan on 2009-10-31
:popcorn:Got ti to work! I did not want to go back from Karmic to Jaunty! I found a thread that said to enter
"cairo-dock -o -i" to start it up and then it had all of these tabs that were white (no label) and I could not tell 
what they were until I closed them. So I killed that and tried Cairo Dock w/o Open GL and it looks good.
So, I closed that and opened Cairo Dock with Open GL and it looked good! Maybe it had to many gadgets 
on it because it went all across the whole bottom of my screen.
I am now going to restart and see if all is well.

---

### Post by Cavsfan on 2009-10-31
8-) Yes, everything is back to being cool! There must have been too many items in the dock.
I had added several before I did an update and it mentioned that I could upgrade to Karmic Koala,
so I did. That is when the problem started, but all if well now.

Sometimes you just have to try things until something works. I know I was lucky though!
Hope my meanderings help someone else.
:popcorn:

---

### Post by arashmansouri on 2010-03-30
hey, am new in Forum, sorry if it is a wrong post, i had a problem , after i install ubuntu 9.10 i set cairo-dock and it was work fine, but i close the cairo-dock simply by right-click on clock bar and close it, now i don't have any access to nothing just a background , how could i make the bar back?!!!

---


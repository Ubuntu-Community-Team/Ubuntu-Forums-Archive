---
title: "Problem:  Keys produce incorrect output!!!"
date: 2005-12-27
forum: General Help
---

### Post by weltall on 2005-12-27
This problem does not happen all the time.  It occurs when I install something...usually with automatix but not always the case.  I type in an [m] and [0] shows up on my screen.  I type in [@] and ["] shows up.  Although not limited to these instances, my keys will produce different outputs than what I type in.  I cannot even put in my passwords or log in correctly!  Extremely annoying.  

The only way I have found to temporarily fix the problem (for about 2 min) is to switch to the console [ctrl-alt-F1] and then back to GNOME [ctrl-alt-F7].  Unforunately, the keys will revert back to the "messed up state" in a few mins and I have to repeat this process.

I have a asus z70va laptop.  I have scoured the forums and found one person with a similar problem but no replies.  Please give any leads!  Getting tired of installing ubuntu repeatedly.

---

### Post by ingo on 2005-12-28
hm, " and @ sound like an issue with US and UK keyboard

try this:

open a shell and type "sudo kcontrol"

select "Regional & Accessability"

select "Keyboard Layout"

change your keyboard layout and see whether it made any difference. If not there is also a drop down menu to select the keyboard model. Try the 105 intl and see. However, before you make the last change, make a backup of your /etc/X11/xorg.conf just to be on the safe side

---

### Post by anil_robo on 2005-12-28
He posted the question under GNOME support - I guess he doesn't need kcontrol.

Go to system--> Preferences--> Keyboard. Click on the second tab (laybouts). Install the correct keyboard config if required, select it and press "up" button till that keyboard config moves to the topmost. Close this window, and type a test document in text editor.

Post here if it was successful.

---

### Post by weltall on 2005-12-28
Thanks for the input.  I just recently reformatted my drive and ubuntu is working fine now...but I am sure it will pop up again.  When it does I will give these suggestions a try. :p

---

### Post by anil_robo on 2005-12-29
[quote=weltall]Thanks for the input. I just recently reformatted my drive and ubuntu is working fine now...but I am sure it will pop up again. When it does I will give these suggestions a try. :p[/quote]

Just as death puts all worries to an end, so does a format put all problems to end! :D

---


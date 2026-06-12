---
title: "Ubuntu's panels--vanished"
date: 2008-08-21
forum: Desktop Environments
---

### Post by Jaded Misanthrope on 2008-08-21
When I booted up Ubuntu earlier, I found that whilst my desktop and its icons loaded as they should, the top and bottom panels (the ones with the Applications menu and active applications respectively) were not present. I could enter the file browser from desktop shortcuts, and the panels were present just a few hors before--what could be the problem? (rebooting did not bring them back)

I haven't altered the desktop environment at all, by the way, if it's relevant.

---

### Post by Vadi on 2008-08-21
Odd. Try doing alt+f2 and "killall gnome-panel", do they come back?

---

### Post by dhinchak on 2009-05-26
i m having the same problem, and the solution suggested also did not work at all.. please give me a good solution, my work is all stopped since i m new to linux and cant do away without the panels....

---

### Post by Vadi on 2009-05-26
Try alt+f2 and "gnome-panel".

---

### Post by dhinchak on 2009-05-26
still, no results with.. alt+f2 and 'gnome-panel' :(

---

### Post by Vadi on 2009-05-26
Do "killall gnome-panel" in the terminal. What does it say?

---

### Post by UbuntuNerd on 2009-05-26
> **dhinchak said:**
> still, no results with.. alt+f2 and 'gnome-panel' :(

if you can still get to a terminal try this command it should restore your panels:```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by dhinchak on 2009-05-27
@Vadi: "killall gnome-panel" in terminal does not show any message..

@UbuntuNerd: your method worked perfectly!! thanx a lot.:KS please explain how it worked, if its not too geeky to understand :P

---

### Post by UbuntuNerd on 2009-05-28
well there's no way of knowing for sure but basically the "killall gnome-panel" should have restarted your panels but my guess is that for some reason the problem you were having require to reset your panels to default instead of restarting them, that command I gave you does that. keep it for future use in case it happens again, if it keeps happening make a new thread because Im seeing this problem reoccurring :)

---

### Post by dhinchak on 2009-06-01
oh.. no, this problem did not reoccur.. n thnx for the explanation, il save the code..

---

### Post by Spirobranchus on 2009-06-13
I am new to Ubuntu and I am having the same problem with my brand new MSI Wind and UNR. When I type "gnome-panel" as recommended in this threat, the panels come back BUT the terminal window freezes in the process of adding all the applets back. 

I type this:

$ gnome-panel

and the terminal prints this:

** (gnome-panel:3168) DEBUG: Adding applet 0
** (gnome-panel:3168) DEBUG: Initialized Panel Applet Signaler

(gnome-panel:3168): libglade-WARNING **: Unexpected element <requires-version> inside <gladeinterface>.
** (gnome-panel:3168) DEBUG: Adding applet 1
** (gnome-panel:3168) DEBUG: Adding applet 1
** (gnome-panel:3168) DEBUG: Adding applet 2
** (gnome-panel:3168) DEBUG: Adding applet 3
** (gnome-panel:3168) DEBUG: Adding applet 4

Then the terminal window freezes here. If I close the termianl, the panels disappear again. Any thoughts? My computer is completely unusable, and I cannot transfer my files to it for fear of having to re-install ubuntu for the 5th time in 2 days. Please help, I am typing this from a Windoze machine because my Ubuntu is not working!

Also, those are not supposed to be smileys in there. That is the number eight followed by a end parentheses and then a colon. like this 8 ) :  So the line is 

** (gnome-panel:3168 ) : DEBUG:  

minus the spaces. I don't know how to make it so that does not automatically turn to smileys when I post this. Is nothing easy?

Thanks

---

### Post by asmoore82 on 2009-06-13
the '&' tells BASH - the terminal command interpreter - to run something in the background;

try ```
gnome-panel &
```
then you should be able to safely close the terminal.

---

### Post by Vadi on 2009-06-13
It's all good, just don't do it in the terminal - open alt+f2 and type that in there.

---

### Post by Spirobranchus on 2009-06-13
> **asmoore82 said:**
> the '&' tells BASH - the terminal command interpreter - to run something in the background;

try ```
gnome-panel &
```then you should be able to safely close the terminal.


 Unfortunately that did not work. It brings back some of the panels, but the terminal (or xterm, doesn't matter where I type it) still freezes and cannot be closed, and the windows are still lacking headers and therefore cannot be moved or closed. For example, if a window opens and blocks the terminal or the shutdown button, there is no way to do anything.... Oh well, will have to wait for a patch or update, I guess...

---

### Post by Vadi on 2009-06-14
Sounds like you're trying to enable desktop effects on low-end hardware? The window borders are created with "gtk-window-decorator".

---


---
title: "Alien Arena 2007 - 640x480 Only &amp; Changes desktop too!"
date: 2007-08-20
forum: Gaming &amp; Leisure
---

### Post by crjackson on 2007-08-20
so I just installed Alien Arena from getdeb.net and it runs but has this problem.

when launching, it's in 640x480 and won't accept anything else.  when I try to change the resolution, then click the accept button it kicks me back to the desktop.  It changes my desktop resolution to 640x480 too and it won't change back until I reboot.

If I leave it at 640x480 the game plays fine, but when I exit the game, I'm looking at a 640x480 desktop again.

I don't want to reboot every time I play this game, and I don't want a but ugly 640x480 screen or game.

Is there anything I can do to fix this?

---

### Post by soxs on 2007-08-20
this is likly to happen beacause of broken graphics acceleration drivers..
plx paste ```
fglrxinfo
``` & ```
glxinfo | grep render
``` output

---

### Post by crjackson on 2007-08-20
> **soxs said:**
> this is likly to happen beacause of broken graphics acceleration drivers..
plx paste ```
fglrxinfo
``` & ```
glxinfo | grep render
``` output
[B]
charles@MSI-K8N-Neo4-SLI-Platinum:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON X800 XL
OpenGL version string: 2.0.6747 (8.40.4)

charles@MSI-K8N-Neo4-SLI-Platinum:~$ [/B]

[B]charles@MSI-K8N-Neo4-SLI-Platinum:~$ glxinfo | grep render
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: ATI RADEON X800 XL
charles@MSI-K8N-Neo4-SLI-Platinum:~$
[/B]

---

### Post by mobad on 2007-08-20
I have had these types problems (stuck at a crazy resolution and changes the desktop too) with games a bunch and I just think its a problem with fglrx as I've noticed these types of problems with other games (not all though so it may be a problem with AA2007). 

I am aware of no fix but you could try running it in a windowed mode (try checking the website or see if there is an option in the settings).

Although, I have been able to fix the resolution afterwards by going to System>Preferences>Screen Resolution and changing the resolution to the one desired.

---

### Post by dmn_clown on 2007-08-20
> **crjackson said:**
> I don't want to reboot every time I play this game, and I don't want a but ugly 640x480 screen or game.

You only **need** to reboot after a kernel update.  That having been said, there is more than one way to return to your default desktop resolution.

The easiest way for you would be:  ```
ctrl + alt + backspace
``` this will kill X and drop you back at the login prompt.

---

### Post by crjackson on 2007-08-21
> **dmn_clown said:**
> You only **need** to reboot after a kernel update.  That having been said, there is more than one way to return to your default desktop resolution.

The easiest way for you would be:  ```
ctrl + alt + backspace
``` this will kill X and drop you back at the login prompt.

Actually I didn't really mean rebooting the computer, I should have said rebooting X.  I'm going to work on it this weekend and see if I can find a better solution.  Perhaps there is a config file I can edit so it will start with a decent resolution.  Playing the game in 640x480 doesn't appeal to me.  It's the ONLY game that does this to me, and if I have to pass this one over it won't kill me.  I would just like to be able to run it at my desktop resolution and it won't let me.  To add insult to injury, it mucks up the desktop.

---

### Post by crjackson on 2007-08-21
> **mobad said:**
> I have had these types problems (stuck at a crazy resolution and changes the desktop too) with games a bunch and I just think its a problem with fglrx as I've noticed these types of problems with other games (not all though so it may be a problem with AA2007). 

I am aware of no fix but you could try running it in a windowed mode (try checking the website or see if there is an option in the settings).

Although, I have been able to fix the resolution afterwards by going to System>Preferences>Screen Resolution and changing the resolution to the one desired.

Is there a Linux commad you know of that I insert into the launcher command line that will force a windowed mode by chance?

My resolution applet won't work after exiting the game.  It will open and present me with the choices, but after selecting them they just won't apply or have any effect at all.

---

### Post by crjackson on 2007-08-22
I did some testing after work tonight.  It's the application not the system.  I tried many games setting very high resolutions and textures.  Each one of them exited clean to a normal desktop.

I tried everything I could think of for Alien Arena and it always results the same.

Finally resolve the issue using synaptic package manager to UNINSTALL!
[B][U]
Problem solved![/U][/B]

---

### Post by BigSilly on 2007-08-22
Gah! I was hoping for a resolution to this since I have a variation of the same problem. The game plays fine, as long as I use 640x480 as the OP says. If I go to select any other screen setting it takes me to a command prompt from within the game, and I don't know what to do. I also got the game from GetDeb, and I have no problems with any other titles.

It's a shame, because it's a blinding game. I don't really want to remove it so I'll just stick with the low res if I have to.

EDIT: Sorry, I'm an idiot. I just had to press ESC to go back to the game properly from the console. Sheesh. It's fine now.

---


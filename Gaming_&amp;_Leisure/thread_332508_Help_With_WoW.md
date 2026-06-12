---
title: "Help With WoW"
date: 2007-01-06
forum: Gaming &amp; Leisure
---

### Post by kcakalinuxnub on 2007-01-06
Hi,  I have a problem my WoW game constantly crashing on me, and it's not just that it's crashing but I cannot interact with objects or people or click on anything in the WoW world.  I can click on my character info and anything on that Toolbar but no my spells.  Also, the terrain is odd, and I took a screen shot so you could get an idea of what it looks like... 
[IMG]http://i84.photobucket.com/albums/k38/pmpcrmbhtmn/Screenshot.png[/IMG] 
As you can see, the terrain is all f-ed up.  I'm pretty sure this is a problem with my configuration but if it isn't then just let me know.  Any help is appreciated. 
Thanks, Kc

---

### Post by Afteraffekt on 2007-01-06
first how are you starting wow? are you using -opengl? have you done the tweaks

---

### Post by kcakalinuxnub on 2007-01-06
OpenGl and WinE. I did the WTF config tweak as well as the open gl tweak using regedit.  Also the mozilla activex is installed.(but it doesnt show in Mozilla firefox, Tools, Extensions.)

---

### Post by Afteraffekt on 2007-01-06
i disnt even do that mozilla tweak, but it seems you forgot something, and i cant pin point what it is :(

---

### Post by kcakalinuxnub on 2007-01-06
Yep, I think I installed everything and did the right tweaks but I still have this error.... Can Anyone else help me out here./

---

### Post by Sammi on 2007-01-07
Either there's a problem with your grafics card driver or you're running WoW in d2d mode instead of opengl.

Try reinstalling you driver and triple checking if you're running in opengl mode.

---

### Post by kcakalinuxnub on 2007-01-07
How can I check to make sure its running in d3d and not d2d and if it is running in d2d how can i change settings to run in d3d?

---

### Post by Sammi on 2007-01-07
Woops. Typo on my part :D

There's nothing called d2d :-#

You are NOT supposed to use d3d. Use opengl. You set this in the file /WTF/confid.wtf file found in your WoW game directory or by running WoW with the -opengl flag instead of the default -d3d.

See the section called [SIZE=2][FONT=Verdana]"Configuring WoW"[/FONT][/SIZE] in our community WoW/Wine howto for instructions on editing config.wtf: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by kcakalinuxnub on 2007-01-07
Ok yes, I did that configuration already.  You set it up through regedit and all that but im still getting these problems and my graphics card is set up fine.  Perhaps should I try using a different Windows Emulator or would just solve nothing.

---

### Post by Ferrat on 2007-01-08
> **kcakalinuxnub said:**
> Ok yes, I did that configuration already.  You set it up through regedit and all that but im still getting these problems and my graphics card is set up fine.  Perhaps should I try using a different Windows Emulator or would just solve nothing.

The fix they are talking about got nothing to do with regedit.. 

Just launch the game like

yourname@yourcomp:/home/mylogin/games/wow$  [B][COLOR="Red"]wine WoW.exe -opengl
[/COLOR][/B]

If that doesn't work then reinstall your grafic drivers and try again

---

### Post by Afteraffekt on 2007-01-09
Wine (Wine is not Emulator) = P But you must also take into account if your using ATI's or X.Orgs Driver, what are you using?

---


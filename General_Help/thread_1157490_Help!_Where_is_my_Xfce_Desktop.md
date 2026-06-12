---
title: "Help! Where is my Xfce Desktop?"
date: 2009-05-12
forum: General Help
---

### Post by J_Stuhr on 2009-05-12
okay so, I just updated my linux system to 8.10 from 8.04 from 7.10 today. all was going well until I hit 8.10, after I signed in on my user account, I was given an error message which read:

'cannot find Xfce Trash, make sure you have Thunar' or something similar to this. basically I had no real desktop enviroment, just some kind of filler desktop with nothing on it.
so, I downloaded and installed Thunar via: sudo apt-get install thunar
which worked no problem. 

I restarted my PC, this time with no error message, but still no desktop enviroment it would seem. 
how do I fix this? 

here is what my desktop currently looks like incase any of you have seen this happen before:


[IMG]http://i3.photobucket.com/albums/y93/Hitsoku/Screenshot.png[/IMG]

---

### Post by kerry_s on 2009-05-12
that is the desktop, that star thing at the top is the panel, it's just empty.

there have been a lot of changes in xfce4 from 7.10 to 8.10, i recommend deleting the config folders and start from scratch.

hold on i got to switch to the other computer to tell you what files.
i'll be back.

---

### Post by kerry_s on 2009-05-12
alright, click on your home icon, press ctrl+h to see hidden if you don't have them showing.
go into .config, delete xfce4 and xfce4-session
then press ctrl+alt+backspace to restart the session, you might want to select xfce4 in the menu just incase.

good luck.

---

### Post by J_Stuhr on 2009-05-12
(feels like a major noob)
Ok I'll try that! thanks for the help!
I'll post here again shortly and let you know how I get on. =)

---

### Post by Dr.Vista on 2009-05-12
> **J_Stuhr said:**
> (feels like a major noob)
Ok I'll try that! thanks for the help!
I'll post here again shortly and let you know how I get on. =)
Try pressing alt-f2 and type in xfce4-panel.

---

### Post by J_Stuhr on 2009-05-12
ok, I deleted the files you said, and restarted the session, but its still the same. =( 
and I tried alt+f4 but nothing happens.

---

### Post by Dr.Vista on 2009-05-12
> **J_Stuhr said:**
> ok, I deleted the files you said, and restarted the session, but its still the same. =( 
and I tried alt+f4 but nothing happens.
Sorry it's alt-f2.

---

### Post by J_Stuhr on 2009-05-12
nevermind! problem fixed! 
just had to grab all the updates from the update manager. =P

---

### Post by SLmanDR on 2009-06-02
[FONT="Garamond"][COLOR="Teal"]Just in case someone else stumbles into here looking for an answer to the missing desktop toolbars (they are called panels, I learned) Open a terminal, right click on the desktop is one way. Then type or paste this into the termninal window: "xfce4-panel" (without quotes) & then press return. Your toolbars (panels) will load up. :)[/COLOR][/FONT]
[SIZE="4"]**[COLOR="DarkRed"]SL[/COLOR]**[/SIZE]

---


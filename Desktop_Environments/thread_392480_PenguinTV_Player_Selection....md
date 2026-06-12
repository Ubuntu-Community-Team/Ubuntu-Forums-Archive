---
title: "PenguinTV Player Selection..."
date: 2007-03-24
forum: Desktop Environments
---

### Post by FXWGBill on 2007-03-24
In my infinite wisdom, earlier today, I decided to play around with the 'view' settings in PenguinTV.  Mannnnnnnnnnnnnn I wish I had never touched it; it was working fine! Now all I get is the list of feeds on the left, and that's it.   I was Using the 'standard' setting and was able to watch in the viewer to the right of the list; no more...  :(  I know I saw a quick line of code to set it to the Mozilla renderer, I think it was.  I'm not positive that that was what it was using, when it was working.  I have dug through the code trying to find a place to change the 'view' setting to no avail; I am permanently stuck on 'Planet Style Layout' and it is useless.  Anyone got any ideas on this???  Oh...  I tried downloading the latest version from Sourceforge and it just made it worse; Won't come up 'PERIOD', crashes before it even starts!!  Which reminds me... Need to say that too; everytime I try to change the 'View' settings, it crashes; I get the apport crash report thingy.  Funny thing is, the 'window' stays on the screen.  If I look at the "view' setting, it's on standard like I was trying to change it to.  I have to force it closed with the 'system monitor' and then when I start it back up again, it is right back on 'Planet Style Layout'   Think that is about it...   Helpppppppppp  please :)

---

### Post by HasratUSA on 2007-03-25
Hmm I have neither heard of Penguine TV nor used it. Let me download and see what it's all about. Even if I can't solve your problem, I would at least thank you for unintentionally introducing me and some other people (who might want to watch TV on their GNU/Linux distribution) to Penguine TV (LOL)

---

### Post by FXWGBill on 2007-03-25
PenguinTV and DemocracyPlayer are more for viewing Vlogs, (video blogs) podcasts and such.  If you have a tv card in your box, though, there are several tv viewing apps available in the repo's

---

### Post by quicktime1 on 2007-04-08
Im in the same situation as you, I've tried everything I can think of. I guess I'll just have to find something else.

---

### Post by RancidLM on 2007-05-07
in the same situation even after deleting   .penguintv
***bump***

---

### Post by RancidLM on 2007-05-07
Ok i fixed it.. heres the process to get this working.
obtain the latest version in my case 2.94
[http://penguintv.sourceforge.net/#download]("http://penguintv.sourceforge.net/#download")
install it.. (the deb package was the easiest) 
remove 
~/.penguintv
run it penguintv..
it will not show up.. you will have to kill the  process
(this will now create the new settings in ~/.penguintv)
then inside of ~/.penguintv/gecko/
create a empty text filed called
prefs.js
then try running it again.. it works for me now :)

Best of luck!

------------------
RancidLM
[Linux Gamer Guide Wiki]("http://linux.strangegamer.com")

---

### Post by ABrownPearn on 2007-05-17
I had the same problem. What worked for me however was- 

alt-f2 to launch "run application"
typed in gconf-editor 
expanded the "apps" tab
selected "penguintv"

the first value on the list was app_window_layout- i just changed it from planet to standard

---


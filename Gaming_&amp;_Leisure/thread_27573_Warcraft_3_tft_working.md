---
title: "Warcraft 3 tft working?"
date: 2005-04-16
forum: Gaming &amp; Leisure
---

### Post by coldturkey on 2005-04-16
Im wondering if Warcraft 3 tft works with Wine/Cedega on Ubuntu without any flaws/problems.

---

### Post by jdodson on 2005-04-16
[QUOTE=coldturkey]Im wondering if Warcraft 3 tft works with Wine/Cedega on Ubuntu without any flaws/problems.[/QUOTE]

i run it great on my hoary box!

blizzard games work the best in cedega.

---

### Post by zwaardmeester on 2005-04-17
I have installed Warcraft 3 ROC but there seems to be a problem. I can start warcraft but when i try to change resolution (default is 800x600 16 bit  :-? ) it quits to desktop. I use cedega 4.3.1 and the Ati fglrx drivers (those work fine in Doom3).  Any suggestions?

Edit: It works now, you must start with warcraft III.exe --opengl

---

### Post by no-success on 2005-05-08
when i try to install wc3:tft it cant find my original install of wc3 and it wont/cant install. how do i get wc3:tft to see my wc3 install? anyone else had this prob? any help would be greatly appriciated.

---

### Post by gil-galad on 2005-05-08
[QUOTE=no-success]when i try to install wc3:tft it cant find my original install of wc3 and it wont/cant install. how do i get wc3:tft to see my wc3 install? anyone else had this prob? any help would be greatly appriciated.[/QUOTE]


You need to edit your registry to point to your wc3 install.  Edit user.reg in your wine/transgaming config directory and put in something like this:

> [Software\\Blizzard Entertainment\\Warcraft III] 1115591174
"InstallPath"="D:\\games\\war3"


---

### Post by no-success on 2005-05-09
[QUOTE=gil-galad]You need to edit your registry to point to your wc3 install.  Edit user.reg in your wine/transgaming config directory and put in something like this: 

[Software\\Blizzard Entertainment\\Warcraft III] 1115591174
"InstallPath"="D:\\games\\war3"[/QUOTE]

can you be a little more discriptive? 

for example is: "D:\\games\\war3" how do i find out my exact Warcraft III install location under p2p/cedega?

and is: "[Software\\Blizzard Entertainment\\Warcraft III] 1115591174" correct? how can i verify that that is in fact the structure in my file system? and what are the numbers after and do they matter at all?

i know these are quite a few questions and i really appriciate your input by far the most promising answer ive com accrost so far.  :grin:

---

### Post by gil-galad on 2005-05-09
The install path is the location where your game is installed.  The home directory is set for D:\\ by default in cedega, fill in the path for your install, my directory was just an example.  You probably have it installed in C:\\Program Files\Warcraft III or something. That should be enough information for frozen throne to find your copy.

[Software\\Blizzard Entertainment\\Warcraft III]
Is the registry key that wc3 uses.  You need that.  I am not sure what the numbers are, I think you can ignore those.  What you have to have in user.reg is:

[Software\\Blizzard Entertainment\\Warcraft III]
"InstallPath"="Path to game directory"

I hope that clears it up.

---

### Post by no-success on 2005-05-09
[QUOTE=gil-galad]The install path is the location where your game is installed.  The home directory is set for D:\\ by default in cedega, fill in the path for your install, my directory was just an example.  You probably have it installed in C:\\Program Files\Warcraft III or something. That should be enough information for frozen throne to find your copy.

[Software\\Blizzard Entertainment\\Warcraft III]
Is the registry key that wc3 uses.  You need that.  I am not sure what the numbers are, I think you can ignore those.  What you have to have in user.reg is:

[Software\\Blizzard Entertainment\\Warcraft III]
"InstallPath"="Path to game directory"

I hope that clears it up.[/QUOTE]
 ill give it a shot thanks!

---

### Post by no-success on 2005-05-09
i added:

[Software\\Blizzard Entertainment\\Warcraft III]
"InstallPath"="C:\\Program Files\Warcraft III"

with no success  :-) 

is there some process to installing that im not following? or am i just sol?

---

### Post by gil-galad on 2005-05-09
hmmm, is it installed in C:\\Program Files\Warcraft III ?  Have you tried reinstalling the original warcraft III?

You can pm me if you need to.

Warcraft III is really the only game I play at the moment.  I know all about running it in linux  ;-)

---

### Post by no-success on 2005-05-09
great got it working thanks for the help!

---

### Post by lastsamurai on 2005-09-06
Warcraft III works well with cedega 4.4 and -opengl. Can also play LAN games with windows machines.  :smile:

---

### Post by wombat20 on 2005-09-09
But will it work conntecting to battle.net??

That's the only reason to play once you've done the campaign game...

---

### Post by gil-galad on 2005-09-09
[QUOTE=wombat20]But will it work conntecting to battle.net??

That's the only reason to play once you've done the campaign game...[/QUOTE]
 yes....

---

### Post by seethru on 2005-09-09
[QUOTE=lastsamurai]Warcraft III works well with cedega 4.4 and -opengl. Can also play LAN games with windows machines.  :smile:[/QUOTE]
 love doing that with friends over, so glad I've eliminated all reasons to boot into windows.

---

### Post by raldge on 2005-09-16
Guys need your help on this.I successfully run Warcraft:Frozen Throne,i've played campaign games it worked fine,but when i play DOTA map,it loads terribly slow and when the progress bar reaches 75% it exited..
Thank you...

---

### Post by itechph on 2005-09-24
[QUOTE=raldge]Guys need your help on this.I successfully run Warcraft:Frozen Throne,i've played campaign games it worked fine,but when i play DOTA map,it loads terribly slow and when the progress bar reaches 75% it exited..
Thank you...[/QUOTE]
 Help!
I'm new to Ubuntu Linux,  I sucessfully installed Warcraft III using WINE/CEDEGA.  But the problem is that...when I start Warcraft, it's very slow and even the mouse is almost not moving...Is there any configuration needed so that I can play with Warcraft III - Frozen Throne smoothly?  Thanks

---


---
title: "[SOLVED] Compiz Fusion Start up"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by isaacj87 on 2007-06-23
Hello all...

I've been trying for hours to get fusion to start up successfully. Fusion runs beautifully  on my i915 (!!) laptop, but everytime I try to get it to startup from a restart or shut down my screen goes black (with the exception of my mouse cursor). I've tried everything...'compiz --replace' in the sessions pref. all the way to using the beryl manager. I downloaded a script, but I really don't know where to put it or what to call it. If anyone could help me out it would be much appreciated!

Oh and BTW...Fusion is soooo cool. I can only imagine how smooth it would be on my XP Comp with my nvidia card, because it's silky smooth on my intergrated graphics laptop!

Thanks!:p

---

### Post by c.dric on 2007-06-23
i have the same problem when i log out and log back in ... only a cursor and a black screen ...

but after restarting the computer it works fine again ... my gnome session starts up normally and i can launch compiz... strange.

i've used this how-to : 
[http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion](http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion)

for the record: i have only 500mb of ram and 64mb of video ram on this comp, but i've used compiz & beryl successfully in the past.

---

### Post by crimesaucer on 2007-06-23
I just changed my Beryl Settings Manager back to the default XFWM for xubuntu, then I took Beryl and the Beryl Startup script off of my Start Up Apps.

Then I added Compiz Fusion with the "compiz --replace" command, and Emerald with the "emerald --replace" command, into my Start Up Apps, now everything starts perfectly after re-booting my computer.

---

### Post by isaacj87 on 2007-06-23
Are you saying you left the beryl-manager in the start apps? I never put beryl specifically in the startup...I put beryl-manager.

---

### Post by isaacj87 on 2007-06-23
> **c.dric said:**
> i have the same problem when i log out and log back in ... only a cursor and a black screen ...

but after restarting the computer it works fine again ... my gnome session starts up normally and i can launch compiz... strange.

i've used this how-to : 
[http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion](http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion)

for the record: i have only 500mb of ram and 64mb of video ram on this comp, but i've used compiz & beryl successfully in the past.

I'm in a similar boat, I have decent specs on my comp and I've successfully ran beryl/compiz too. The only differences is I have to log in as a different user and then log out to get fusion to work. I get the black screen with mouse cursor when I come from a reboot or boot up. Oh and for the record I too used that guide. Worked perfectly.

---

### Post by crimesaucer on 2007-06-23
> **isaacj87 said:**
> Are you saying you left the beryl-manager in the start apps? I never put beryl specifically in the startup...I put beryl-manager.

I had Beryl Manager and a Beryl Start up script in my Start Up Apps list, just like it said to in the Beryl install wiki page for Beryl AiGLX for xubuntu xfce.

...So I un-clicked them, and then opened up my Beryl Settings Manager and changed my Window Manager back to XFWM for XFCE.

...Then I added the two new commands for compiz and emerald and re-booted and everything worked perfectly. I didn't even have a problem with my conky start up script.

---

### Post by isaacj87 on 2007-06-23
Yeah I did exactly that...except with Metacity..and sometimes my desktop comes up...but 90% of the time it doesn't..

---

### Post by isaacj87 on 2007-06-24
Can someone give me another suggestion about Fusion startup? Has anyone else had luck with the startup script?

---

### Post by blueBin on 2007-06-28
Update:

Seemed like they just fixed this problem in the new update today.


So, the below solution doesn't work now.

*****************************************************************

Been having same problem for 2 days and finally figure it out! 
 As newbie, don't know if what I did is correct, but it works....

Here is my solution:

1) create compiz_startup.sh file in /usr/local/bin

$ sudo gedit /usr/local/bin/compiz_startup.sh

type in the code:
[INDENT]
#!/bin/bash
#
# Start up compiz-fusion with compiz --replace
#

sleep 30
compiz --replace[/INDENT]


2) change permission of the file:
$ sudo chmod a+x /usr/local/bin/compiz_startup.sh

3) add compiz_startup.sh to startup:
goto System->Preferences->Session
create new startup, and point the command to the compiz_startup.sh 

4) restart

Thank you crimesaucer for the tips, and I also use [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL#Adding_Beryl_to_Session_Startup]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL#Adding_Beryl_to_Session_Startup")
for my reference

---

### Post by isaacj87 on 2007-06-28
I appreciate the tip and the startup script. I'll see it I can just add it to my sessions and if that doesn't work I'll try your solution. Once again, thanks for your time :p

---

### Post by isaacj87 on 2007-06-28
okay so I used your tip...but not only did I have to create a startup script for Compiz, I also had to do one for Emerald...apparently the two don't like each anymore after the update

I tried using "compiz --replace -c emerald &" and it was a no go. I also tried adding compiz and emerald separately to my sessions...also a dead end.

I used your script idea just gave Compiz a 10 sec sleep and Emerald a 15 sec sleep. Now it works...it's a bit hackish but in the end it works.

---

### Post by throwingks on 2007-06-28
^
I used 'compiz --replace -c emerald &' with sleep 10 in the script and it works fine for me.

---

### Post by isaacj87 on 2007-06-28
haha you beat me to it...but with the update I received today I too also use that and it works perfectly for me.

---


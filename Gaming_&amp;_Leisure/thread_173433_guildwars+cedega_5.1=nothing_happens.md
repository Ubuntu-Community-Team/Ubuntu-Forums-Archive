---
title: "guildwars+cedega 5.1=nothing happens"
date: 2006-05-10
forum: Gaming &amp; Leisure
---

### Post by nldavepc on 2006-05-10
Hi all,

I'm a reasonably noob ubuntu user, and am trying to get GW to work with cedega. 
The installation went fine, but now if I select Guild Wars and press play nothing happens.

I would apreciate any sugestions you guys might have. If I can get GW and eve working I'm dumping windows forever he he he

thanks in advance

---

### Post by Thoop on 2006-05-10
Are you using XGL? If so, it won't work, you'll have to open a new session without xgl and it'll work.

Otherwise I wouldn't know what the problem is ;)

---

### Post by nldavepc on 2006-05-10
I assume XGL is related to the type of X I'm running, but I have no Idea how to start a session without it. Could you explain further please?

---

### Post by Perfect Storm on 2006-05-10
Use vedega v4.4.3 instead, it works like a charm.
Go to the transgaming tab ---> Install previous versions. Pick the 4.4.3 version.
You can actually have all of the version installs if you like, it's smart if some games work better on an another engine. ;)
 
Select guild wars and hit the properties button and click Profile Management.

A new windows appear. Click Cedega_4.4.3 and click edit.
unselect DXgrab and change Desktop to 800x600, winversion 98. click apply

Back to the Profile Management (you still have 4.4.3 selected)
move guild wars to "applications using this profile" and click close.

Now you can start Guildwars first time, when you're logged in with your character log out again and change Desktop to "no".

That should do it.
There's a bug where you have to triple click with right mouse button everytime you entering a new place but it's nothing ;)


Edit, ah you have XGL installed very bad if you like to gaming ;)
Other than that you should give 4.4.3 a try. I can run a high graphic with 1600x1200 with that.

---

### Post by Thoop on 2006-05-10
[QUOTE=nldavepc]I assume XGL is related to the type of X I'm running, but I have no Idea how to start a session without it. Could you explain further please?[/QUOTE]
well if you were using XGL you'd probably know. If you use it, just open a new login (you can select that in System Tools in GNOME) and you'll have the choice to start the standard X server or a server with XGL.

---

### Post by nldavepc on 2006-05-11
Thank you both for the tips. I'm a bit further now. After I install GW It either loads but outputs a black screen, or nothing happens. That's with cedega 5.1-1

I downloaded version 4.4.3 in rpm, deb and tgz, but if I try to install (say with dpkg -i for the deb) it overwrites my entire 5.1-1 installation instead of just adding the version to my existing install.

From snooping around on the net I found out that I need a cpkg file, but I haven't been able to find one for download. 

any other sugestions would be very welcome :)

---

### Post by nldavepc on 2006-05-11
with 5.1.3 It starts up, downloads updates from arena net and crashes. Still better than when nothing happens, but not quite the result I was looking for :)

edit: Now all of a sudden some graphics start loading, but then it crashes.

---

### Post by Perfect Storm on 2006-05-12
No, within cedega gui you can download the diffrent version of the cedega engine.
Just startup cedega. I've adeed a screenshot to show:

---

### Post by nldavepc on 2006-05-12
for some reason that option is greyed out for me even though I have a transgaming account.

---

### Post by Perfect Storm on 2006-05-12
Make sure that your subscribtion isn't ran out, also that your account is correct.

---

### Post by nldavepc on 2006-05-12
my account is fine, after a couple reinstalls the option became clickable (go figure) and I finally managed to download and install 4.4.3. 

Installed it and now I'm a bit further than I was before. But still not working.
I get a black screen with a mouse in it and if I move it over a certain area I the mouse changes to a cursor. 
Tried typing id and password. After pressing enter my computer starts churning about, as if it's going to load something but the screen stays black

---

### Post by handy on 2006-05-12
Firstly, I am a beginner with Ubuntu ( linux ) too.

I have been happily playing GW for 4 months via Cedega 4.4.3.  My trials & tribulations can be found [**here**]("http://ubuntuforums.org/showthread.php?t=123715").  There is as you have gathered a very happy ending!  I also enjoyed the trip.

What kind of graphic card do you have, I hope that it is nVidia?  If so have you got the nVidia closed source drivers installed?  If not the easiest way is to use [**Automatix**]("http://ubuntuforums.org/showthread.php?t=138405") to do it for you.

If you do go down the Automatix route, do an update all via synaptic first.  If you don't go down the Automatix route make sure everything is upto  date anyway!

Your system specifications might be helpful?  Ram?  CPU?  Free space on your Hard Disk Drive?

You could backup your **/home/.cedega/configuration_profiles/cedega_4.4.3**  file.  & then copy mine in & see if it helps.  You will need to change settings to suit the amount of graphics memory your system has.  You can do that through the Cedega GUI anyway.  You do not have to edit the settings file, that is what the GUI is for.

My cedega settings file is tagged on my GW summary found at the bottom of [**this page**]("http://ubuntuforums.org/showthread.php?t=123715&page=5").

I will be in & out a bit today, I will check for your posts from time to time, to see if I can help you get GW going on your system.

Don't give up, it's worth it! :KS

---

### Post by nldavepc on 2006-05-12
I'm not giving up he he

as to my system specs:
amd athlon 2400
ATI radeon 9600 pro (setup as described [here]("http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html#install") in section 5 ---it passes all the cedega tests)
1gig ram

I'll check out your thread... thanks for the advice :)

---

### Post by nldavepc on 2006-05-13
it's working guys. it was my video card after all. after reading about all the problems people have with ATI, I just plugged in an old nvidia card (geforce4 mx440) and now it works :) 

Thanks for taking the time to explain things.

---

### Post by handy on 2006-05-13
[QUOTE=nldavepc]it's working guys. it was my video card after all. after reading about all the problems people have with ATI, I just plugged in an old nvidia card (geforce4 mx440) and now it works :) 

Thanks for taking the time to explain things.[/QUOTE]

Great stuff!!

Let the game begin! :KS

---


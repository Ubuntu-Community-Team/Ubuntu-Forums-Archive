---
title: "Ton of newbie questions :)"
date: 2006-01-05
forum: General Help
---

### Post by Sopranosmainman on 2006-01-05
Ok guys all of ur help so far has been great. Now im just gonna ask a ton of questions that hopefully you can answer.

1. How do i go about updating programs that may not be on the adept list....

2. How do i go about unistalling any program i dont want?

3. How do i know if i have my ATI graphics drivers installed?
 -  and if i dont have them, where can i get them from.

4 In Firefox... when i want to watch a streaming WMV, mplayer shows it loading, then plays the file for a second and stops. Same thing with streaming audio...how do i go about fixing this. 

5. How do i make firefox my default browser... and how come in version 1.5 the check for updates is not able to be selected?

6. How do i have other media programs have mp3, xvid, etc capabilities... mplayer seems to play it all, but was wonderin why no other program packaged with kubuntu do?

7. I have an external wireless linksys card. How do i have it activated?

8. Windows has network connections, where i can enable, disable wireless and do alot of other things... does linux have somethign comparable that do the same things... if so how can i find it?

9. Is there a disk defragger in linux... and is it even needed in this OS?

10. What programs does everyone recommend to do the following:
     Chat... such as aim, yahoo, etc....
     Media player... that plays mp3s, everything u name it
     CD/DVD burning software....
  - I know kubuntu comes with some already but are they the best ones, or can i find better...


I know its alot of questions but i hope u can answer what ever u can. Again i thank you in advance.

---

### Post by rjwood on 2006-01-05
1) what programs--if they came with ubuntu or are from synaptic ```
 sudo apt-get update
``` then ```
sudo apt-get upgrade
```

2)go to synaptic---find it--uncheck it- and hit apply

3)from a terminal ```
less /etc/X11/xorg.config
``` go to the section labled "devices" and check your driver. If not correct search the forums for "ati" or "drivers"

4)?? sry

5)systems>preferences>perferred applications

6)?? sry

7)?? sry

8)?? sry

9)not needed

10)?? sry

---

### Post by Zelut on 2006-01-05
Well I'm feelin lucky so I'll take a shot at a few of the questions (only at work another half-hour, don't think I could get ALL of them lol).

8. System > Admin > Networking should be the equivalent to your XP network connections.

9. There is a disk defragger (not sure the command).  I know however that it'll auto run & scan after x boots by your machine.. if you need it, it'll run it for you.

10.  Best program in the free world for chat is gaim.  Should come pre-installed for you.  It supports AIM, MSN, Yahoo, and like 500 more.
My preference for .mp3 & other audio is [xmms]("http://ubuntuguide.org/#xmms") / for CD/DVD I like [gnomebaker]("http://ubuntuguide.org/#gnomebaker") (or K3B in KDE).

5. Edit > Preferences > should be a checkbox for 'default browser' (unless its moved in 1.5).

---

### Post by Sopranosmainman on 2006-01-05
There is no system > admin.... anywhere.... i checked under system and system settings..... plz tell me what im doing wrong..... 

and for the default browser... in what do i hit edit... preferences.... in konquerer... sorry if i sound stupid....


plus how come to make any changes it says i need **root access**.... how do i get root access. Please help... and any help to my previous questions will be much appreciated. Thanks

---

### Post by rjwood on 2006-01-05
nothing----your obviously on kubuntu not gnome. Sorry, I didn't realize that. In firefox preferances, there shoud be a box somewhere for it to make sure it is your default browser.

---

### Post by Sopranosmainman on 2006-01-05
[QUOTE=rjwood]nothing----your obviously on kubuntu not gnome. Sorry, I didn't realize that. In firefox preferances, there shoud be a box somewhere for it to make sure it is your default browser.[/QUOTE]

Its set as default...  but it wont even let me check now.... it doesnt do anything.. same as if i go to help... check for updates..... it is not able to be clicked... its greyed out.

---

### Post by Billquinn1 on 2006-01-05
Anything you need to change the default of: Go to the K menu, settings>KDE components>File Associations. For the web stuff type html in the search box and move firefox up and kongueror down or viceversa. I think it is under text and and something else in there.
I think the current ubuntu version of Firefox is still at 1.0.7 so if you have 1.5 it may not be fully functional. The update thing may not be working yet.

---

### Post by Sopranosmainman on 2006-01-05
KDE Resources and Service managers are the only thing i find in KDE components... nothing relating file associations. Am i retarted... or do i have a problem with Kubuntu??

---

### Post by Billquinn1 on 2006-01-05
On my K menu there is a "settings" under a header that says "actions" . Drill down from that "settings" if you have that. I will look around if it is somewhere else to.

---

### Post by Billquinn1 on 2006-01-05
Ok. Check in your "system settings" under "user account" and "default applications". There is a place to choose the web browser there....I hope.


I would suggest you check out:
[http://doc.gwos.org/index.php/BreezyCust](http://doc.gwos.org/index.php/BreezyCust)
Good setup stuff in there.

---

### Post by Sopranosmainman on 2006-01-05
[QUOTE=Billquinn1]On my K menu there is a "settings" under a header that says "actions" . Drill down from that "settings" if you have that. I will look around if it is somewhere else to.[/QUOTE]

No i do not have that... under actions i have run command.. then shutdown options

---

### Post by Billquinn1 on 2006-01-05
Ok. Check in your "system settings" under "user account" and "default applications". There is a place to choose the web browser there....I hope.


I would also suggest you check out:
[http://doc.gwos.org/index.php/BreezyCust](http://doc.gwos.org/index.php/BreezyCust)
Good setup stuff in there.

---

### Post by Sopranosmainman on 2006-01-05
[QUOTE=Billquinn1]Ok. Check in your "system settings" under "user account" and "default applications". There is a place to choose the web browser there....I hope.


I would also suggest you check out:
[http://doc.gwos.org/index.php/BreezyCust](http://doc.gwos.org/index.php/BreezyCust)
Good setup stuff in there.[/QUOTE]

OK setup the default BROWSER!!!! but for some reason i cant setup the defail messendger.... i downloaded gaim and installeld it fine...... i got rid of what the default one was... anyway on how to show gaim fromt he dropdown menu of hte default apps section for messenger

---

### Post by Billquinn1 on 2006-01-05
That does not seem to work. I think it might be a gnome/kde thing. Hopefully that won't mess you up to much.

The ATI driver thing. check out this post: [http://www.ubuntuforums.org/showthread.php?t=75378](http://www.ubuntuforums.org/showthread.php?t=75378)

About half way down he shows you how to check your drivers. 
> $ fglrxinfo
If it says something about "mesa" you need to go through the whole process. If it looks like; 
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)
then you are probably good.

---

### Post by whitesox on 2006-01-06
use synaptic/apt-get for everything.  the rule of thumb is that ONLY when a program is not in ANY available repository do you download it and install it.  Otherwise, just do:```
sudo apt-get install gaim
```
after  that, it should work.
and also, look under firefox preferences, and find the section about default browsers.  I think it works under linux.
to answer most of your other questions; use automatix. 
 [http://ubuntuforums.org/showthread.php?t=105343]("http://ubuntuforums.org/showthread.php?t=105343")

---

### Post by pgroover on 2006-01-06
Run "kcontrol" from a console or the "Run Command..." from the menu and then select KDE Components -> Component Chooser -> Web Browser, select "in the following browser:" and type in firefox.  That will ensure firefox is always used when you click links elsewhere in case you're unable to edit your Firefox preferences.

---


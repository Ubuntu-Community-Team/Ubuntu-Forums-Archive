---
title: "Fatal Server Error: no screens found - Starting XServer"
date: 2005-05-18
forum: Desktop Environments
---

### Post by sixth on 2005-05-18
Well first off, I DID SEARCH first and found a crap load of topics on this problem, but none fixed my situation. I am not sure exactly what happened but when I try:

dpkg-reconfigure xserver-xorg i get this - xserver=xorg is broken of not fully installed.

I try apt-get install xserver-xfree86 and i get that it is already installed. Any help would be greatly appreciated, hopefully i can get this working again.

Thanks!

---

### Post by dave9191 on 2005-05-18
Try 

apt-get -f install

if something didnt install properly that might fix it :)

---

### Post by sixth on 2005-05-18
when i do tat all it does is: 
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

any other ideas? :-(

---

### Post by dave9191 on 2005-05-18
Did you do a full installation from the CD, or are you trying to install stuff manually? 

And try startx

---

### Post by sixth on 2005-05-18
I already had the system up and running. I 'accidently' did something really dumb.:-( Everything was fine blah blah blah, and i was installing some programs through apt-get  and dumbass me installed xserver AGAIN and my battery died right in the middle, and well now i have nothing :-( 

i try startx and get this....
Fater server error: no screens found XIOL fatal IO error 104 (connection reset by peer) on X server ".0.0" after requests (0 Known precessed) with 0 events remaning.

And yes i did install from a CD.

---

### Post by sixth on 2005-05-18
anybody have a solution to fix this?

---

### Post by dave9191 on 2005-05-18
If you tried to install the xserver try to configure it. xorgconfig

---

### Post by sixth on 2005-05-18
[QUOTE=dave9191]If you tried to install the xserver try to configure it. xorgconfig[/QUOTE]
 I just went through the xorgconfig and i tried startx and still no go. i get the same error. 

Fatal server error: no screens found XIO: fatal IO error 104 (connection reset by peer) on X server ".0.0" after requests (0 Known precessed) with 0 events remaning.

xauthL error in locking authority file /home/sixth/.Xauthority

any other ideas?

---

### Post by dave9191 on 2005-05-18
/home/sixth/.Xauthority whats up with that file? does it exist? what are the file permissions for it? (ls -lA | grep .X)

Dave

---

### Post by sixth on 2005-05-18
I dont even see that file when i do what you said above. the only two .Xauthority files are these:
 
.Xauthority-c with -RW- - - - - 
.Xauthority-l -RW- - - -

so i have not a clue what the hell that other file is? what esle should i do? :-)

---

### Post by sixth on 2005-05-18
Here is some more things i think might help....when i type startx here is the FULL errors:

(==) Log File: "/var/log/XFree86.0.log", Time ******
(==) Using config file: "/etc/X11/XF86Config-4
Data incomplete in file /etc/X11/XF86Config-4 
         At least one Device section is required.
(EE) Problem parsing the config file
(EE) Error from xf86HandleConfigFile()

Fatal server error: no screens found XIO: fatal IO error 104 (connection reset by peer) on X server ".0.0" after requests (0 Known precessed) with 0 events remaning.

xauthL error in locking authority file /home/sixth/.Xauthority

I tried modifying the XF86Config-4 and its BLANK. I have not a clue wat to do...

---

### Post by sixth on 2005-05-18
this isnt looking good...

---

### Post by philipacamaniac on 2005-05-18
You really shouldn't have to use Xfree.
Try sudo apt-get remove xserver-xfree86

Then totally reinstall Xorg. 
1. sudo rm -r /etc/X11
2. rm ~/.Xauthority (and any similarly named files)
3. sudo apt-get install --reinstall xserver-xorg

---

### Post by dave9191 on 2005-05-18
I think that you should have an .Xauthority file in your home dir, cause its complaining about not being able to lock. But I dont really know what else to do apart from reinstall everything, but that would mean loosing any settings and files that you havent backed up. Maybe someone else has some ideas. Try asking on the irc channel perhaps. 

Dave

---

### Post by dave9191 on 2005-05-18
Eeee, you really shouldnt have XFree on there. Follow the advice above and hope that sorts it out. If not you might have to do a reinstall. But make sure that you back your files up first. 

Dave

---

### Post by sixth on 2005-05-18
well i definitly learned my lesson.

i followed the above directions , reinstalled xorg and i rebooted, and i get the kubuntu log in screen. i enter my password and it acts like it starts to log me in and it goes black and flashed right back to the login screen. Now earlier i was messing with the config file for something i dunno wat...but i think its cause i **** up my display settings. What can i do now to reconfigure everything?

---

### Post by sixth on 2005-05-18
[QUOTE=sixth]well i definitly learned my lesson.

i followed the above directions , reinstalled xorg and i rebooted, and i get the kubuntu log in screen. i enter my password and it acts like it starts to log me in and it goes black and flashed right back to the login screen. Now earlier i was messing with the config file for something i dunno wat...but i think its cause i **** up my display settings. What can i do now to reconfigure everything?[/QUOTE]
 nevermind its xorgconfig....:-) i HOPE that this is all thats wrong, anyone esle think of anything esle?

---

### Post by sixth on 2005-05-18
well now i am getting (EE) Mouse1: cannot open input device
(EE) PreInit failed for input device 'mouse1'
(EE) Couldnt load XKB keymap, falling back to pre-xkb keymap

ehhhhh close to a reinstall...:-(

---

### Post by dave9191 on 2005-05-18
I have a feeling that you did something really bad there :( I dont know how to fix those errors, sry. I would just do a full reinstall, or would you loose too much? 

I can offer one piece of amazing good advice (and I should follow this too sometime). Make a complete backup of your installation b4 you start messing, so that you can revert back to what your system was. I can never be btohered and I have paid the price once or twice. Maybe one day Ill learn. 

Dave

---

### Post by sixth on 2005-05-18
Dave,

Thanks for the help. I am going to do a full reinstall. How do you recommend is the easiest way to make a backup of my system to be able to revert back in a situation like this? Is there some type of program? thanks again for the help!

---

### Post by philipacamaniac on 2005-05-18
[QUOTE=sixth]Dave,

Thanks for the help. I am going to do a full reinstall. How do you recommend is the easiest way to make a backup of my system to be able to revert back in a situation like this? Is there some type of program? thanks again for the help![/QUOTE]

Utilities --> Konserve

---

### Post by dave9191 on 2005-05-18
Or if you have another driver big enough you could just do a cp * to copy all the files. You might have to boot from a live cd to do this tho. 

Dave

---


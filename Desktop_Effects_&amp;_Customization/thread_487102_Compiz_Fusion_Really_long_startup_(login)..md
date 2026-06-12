---
title: "Compiz Fusion: Really long startup (login)."
date: 2007-06-28
forum: Desktop Effects &amp; Customization
---

### Post by Ub1476 on 2007-06-28
First of, I installed Compiz Fusion using this nice guide: [Linky]("http://ubuntuforums.org/showthread.php?t=481615")

But now, when Ubuntu loads the startup elements (after typing in user/pasw) it takes way to long time. Like when I need to type in the password to get connected to my wireless network, it takes bout 2-3 minutes before the pop-up comes. Also the splash screen stays there for at least 1-2 minutes. No problems with this when I used Beryl. 

Also the weirdest thing is that I haven't set CF to load at startup.

Besides that CF runs great with my ATI X1400.

Help would be appreciated:)

---

### Post by kpkeerthi on 2007-06-28
I have noticed this too with my nvidia 7800gtx. Strange.. it however starts without a delay when I run from ALT+F2.

---

### Post by Ub1476 on 2007-06-29
Well, good to not be alone.

bump

---

### Post by sawjew on 2007-06-30
Same problem here.  I had no problems with the default compiz in feisty but since installing compiz-fusion my system hangs from the splash screen for a while until everything becomes active.  Any ideas?

---

### Post by Ultra Magnus on 2007-06-30
I've noticed starup takes a bit longer, I have an ATI X1400 aswell so I have to start up with XORG to get the desktop effects - Just wondering do you get a grey screen before going to the regular desktop with your ATI card?

---

### Post by coldstatue on 2007-06-30
I'm with you. same issues here. Runs w/ Alt+F2 just fine. Trying to have it autostart causes about 5 minutes of waiting, resulting in decoration-less windows, but transparent menus and such. W/ Alt+F2, all is well.

EDIT: I have tried changing the priority in current session. No luck. Also, the other startups don't usually run until it does. If they do, there is no transparency (for the widgets.) But then, after they load, I get menu transparencies.

---

### Post by smithman89 on 2007-06-30
I have that problem too, for me when i log on, it seems to hang at when nautilus starts up.  It even shows the Ubuntu startup splash on my screen well after i've started using programs.  Once it disappears after like 3 minutes, then all my startup programs run. Oh, P4 3.04 GHz with Nvidia Geforce 6600, in case anyone is wondering.

---

### Post by jogebau on 2007-06-30
Same probs here, anybody knows anything?

---

### Post by kevinbeard on 2007-06-30
This worked for me:

I had to change the default window manager back to metacity

Open up gconf (alt-f2 or terminal and run gconf-editor) and navigate to /desktop/gnome/applications/window_manager and change the value of "default" to metacity

---

### Post by coldstatue on 2007-07-01
> **kevinbeard said:**
> This worked for me:

I had to change the default window manager back to metacity

Open up gconf (alt-f2 or terminal and run gconf-editor) and navigate to /desktop/gnome/applications/window_manager and change the value of "default" to metacity

Do you just type in "metacity", or do you have to put a path? If so, what is the complete path?
Thanks

---

### Post by sawjew on 2007-07-01
I have resolved the issue by creating a startup script for compiz as follows;
```
#/bin/bash
 sleep 10
compiz --replace
```
I placed this in /home/<USERNAME>/bin made it executable then under System>Preferences>Sessions created a new startup entry pointed to this script and it now starts faster than it ever has.

---

### Post by NumberOne on 2007-07-01
So far I have tried your suggestions and encountered problems as well as other suggestions in this thread.

1.  I do not have a /home/<UserName>/bin directory.
2. How do you make a script executable??


I am running Ubuntu 7.04. 

As mentioned, there was an above thread that listed a directory that does not exixt on my system.

Is this a common problem??  Being relativly new to Linux, this gets furstrating and time consuming.

Thanks.
T.

---

### Post by walkerk on 2007-07-01
i had this issue when i first installed c-fusion but i think it was because i hadn't removed the existing compiz software.. once i removed everything compiz/beryl related and i re-installed c-fusion this problem went away..

i also load compiz with a start-up script.. just like above..

---

### Post by sawjew on 2007-07-01
Sorry for not going into more detail NumberOne, I was in a bit of a hurry when I typed that message earlier.  Here goes for a little more detail.

By default you do not have a /home/<username>/bin directory, it is a directory I created in my home directory for any executable scripts I have created, it is also used by Crossover Office and some other applications for the scripts they create.  You don't have to use that location for the script but it keeps everything in a convenient, easily located place in the system.

So you can just open your home directory with nautilus, right click anywhere in the window, select create folder and name it "bin".

[LIST]
[*]open a terminal 'Applications>Accessories>Terminal'
[*]in the terminal type
[/LIST]
```
gedit ~/bin/startcompiz

```
[LIST]
[*]In the text editor window paste
[/LIST]
```
#/bin/bash
 sleep 10
compiz --replace
```
[LIST]
[*]Save and close the file, you should now have a file named startcompiz in /home/<username>/bin
[*]To make the script executable type the following;
[/LIST]
```
sudo chmod +x ~/bin/startcompiz
```
[LIST]
[*]**[COLOR="Red"]Or[/COLOR]** you can open /home/<username>/bin in Nautilus, right click on 'startcompiz', select 'Properties', in the window which opens select the 'Permissions' tab, check the box which says 'Allow executing file as a program'
[*]Now go to the System menu, select System>Preferences>Sessions
[*]Select the 'Startup Programs' tab
[*]click the 'New' button
[*]type in 'Start Compiz' for the name (or whatever you like)
[*]then browse to your /home/<username>/bin/startcompiz script
[*]next time you login compiz should start shortly after everything else has started
[/LIST]

If you are still having problems you could try increasing the sleep time in the script,  the original script I based this on used 30 but for my system 10 was quite adequate.

[B]PS: You may already know this, but where I use <username> like this it means substitute in your own username here, for instance my username is 'stephen' therefore my /home/<username>/bin directory is actually /home/stephen/bin.

[/B]Hope this sorts the problem out for you.

---

### Post by smithman89 on 2007-07-01
I basically do the same thing, i made a script on my desktop that switches to compiz (basically i have 2 scripts, 1 for going to compiz, the other goes to metacity, i use it for when i want to run games).  My only prob is that even though i get to the compiz theme, my startup is still hanging.  Only after like 2 minutes, then all of my startup programs begin.  Its a little annoying for me, but i think its a small price to pay for compiz-fusion :D

---

### Post by NumberOne on 2007-07-01
I did what Walkerk suggested, Removing all instances relating to compiz and beryl, then reinstalling compiz-fusio,  and now my system starts normally, 
THANKS All for you help,
T.

---

### Post by Ub1476 on 2007-07-01
I had to delete the hidden .beryl folder in my home directory (ctrl+h to show hidden files).:p Works well now, and added the the command _compiz --replace -c emerald_ for it to start with borders and all.

Thanks for all replies!

---

### Post by kevinbeard on 2007-07-01
> **coldstatue said:**
> Do you just type in "metacity", or do you have to put a path? If so, what is the complete path?
Thanks

You probably don't have to but I put in the full path.  It's the same path on mine. (/usr/bin)

You can always type "which metacity" in a terminal to make sure you have the correct path.

---


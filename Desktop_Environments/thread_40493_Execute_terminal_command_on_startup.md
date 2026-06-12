---
title: "Execute terminal command on startup?"
date: 2005-06-09
forum: Desktop Environments
---

### Post by Darkelite on 2005-06-09
Hi, 

I am using OSS to load my sound, and at every boot, the command "soundon" needs to run to load it. I have made a button in the gnome bar that runs it by using the "run in terminal checkbox".  The sessions "startup" dialog does not have this option...

How would I make it autoload at startup, or even better, be loaded in the bootup process (before login), when this such as:

*Starting hotplug system
*Initializing network connections

..are being loaded?

thanks  ;-)

---

### Post by wylfing on 2005-06-09
Try using a command like the following:
```
gnome-terminal -x script.sh
``` 
That will run 'script.sh' in a terminal window.

---

### Post by Darkelite on 2005-06-09
great! but how do i make the script?

just..

#! /bin/sh
#
# blah
#

soundon

??

---

### Post by Joeb on 2005-06-09
When you say you are using OSS to "load my sound,"  what do you mean?  Do you mean that you are using the OSS drivers instead of ALSA are you issuing some kind of command?

If you are using the OSS drivers, I was under the impression that like ALSA, OSS starts automatically.

Now, if you do need to issue that command, and yes, the script you listed would be correct (you should test it however, in a terminal window, to be sure), you probably want to add that script to /etc/init.d so that it runs everytime you boot the computer instead of each time you log on.  If you go this route, you would also need to make a symlink to the script in /etc/init.d to one of the run levels, say in /ect/rc5.d/  (rc5 is for graphical logins, which means everytime you boot your computer into the graphical login it will run)

---

### Post by Darkelite on 2005-06-09
ok great, I know to put it in init.d, but do i have to do:

chmod +x /etc/init.d/soundon

or can i just put a checkmark in the box next to soundon im BUM

assuming the scripts name is "soundon"

and, what runlevels can I use, can I have it run at whatever the runlevel before the gui is loaded?

I'm using oss for my soundcard drivers, its an old Neomagic 256 in a laptop, and I use oss becuase the card is not pnp and is not listed in device manager.  It sets everything for the soundcard then I give the soundon comand to start it.

I hope that makes sense, I'm 3 days into linux  :-)

---

### Post by Joeb on 2005-06-09
[I]ok great, I know to put it in init.d, but do i have to do:

chmod +x /etc/init.d/soundon

or can i just put a checkmark in the box next to soundon im BUM
[/I]

That is a good question.  I'm won't be at a linux computer until tonight, so I can't check.  But, if you do a ls -a in the /etc/init.d, you can see if the other ones have "x" set.  I would assume they do and if so, you would need to do the chmod, too.

As for run levels, most likely, you just want 3 and 5.  Both are for multiuser booting (which is the normal booting of linux).  3 is if you boot into text mode and 5 is if you boot into graphics mode (ie x windows).

For only 3 days into linux, you sound like you've learned a lot.  Congratulations!

---

### Post by Darkelite on 2005-06-09
well, I followed the instructions you gave, and used the chmod line.  I put it in both rc3 and rc5

Im guessing on what the prefixes in the runlevel folders are, I assume K is to stop and S is to start, and the number is to specify the order.

One question though:

what is rcS.d?

Yes, the past three days has been made up of staying up until four in the morning reading this forum, ubuntuguide, asking friends who using linux questions, and experimenting myself.  Its amazing how much more I know in just three days.  :grin:

EDIT:  ok, I put it rc3 and rc5, its a no go.  I put in rc0, and i get the message error line xx, command "soundon" not found.  So I added cd /root/oss/bin, which is the exact directory that soundon is in, and still it won't work.

Any ideas?

EDIT2: If I open the run box and type : 

gnome-terminal -x /etc/init.d/soundon.sh

it just opens up a terminal and then closes.  That means the script is wrong right?

EDIT3: Ok, I decided to throw this into the sessions startup programs:

gnome-terminal --zoom=.28 -x soundon

the small zoom is because I don't really want it seen, I would be alot happier if I could find a way to make it totally hidden or minimized.

Other than that, it works great.

---

### Post by Joeb on 2005-06-09
Is soundon an actually binary file or is it also a shell script of some sort?  If it is a shell script, then after changing to the directory it is in change the soundon line to ./soundon and see if that fixes it.

You can try running it from a terminal window instead of the run box.  That way, any error messages will still be visible.  Just open gnome-terminal and type  /etc/init.d/soundon.sh  and hit enter.

Post the error message and maybe the contents of soundon.sh

---

### Post by psychicdragon on 2005-06-09
You just want to run soundon whenever you start Gnome or whatever right?
This should work, I do the same thing with esd under Xfce.

gedit ~/Desktop/Autostart/soundon.sh

Insert this:
```
#!/bin/sh

soundon
```
save and you're good.

---

### Post by Darkelite on 2005-06-09
First of all, yes, soundon is a shell script.  Joeb I'll try your ./ suggestion because I do want it to run before gdm.

My solution for now is this in the sessions startup box:

gnome-terminal --zoom=.28 --geometry=+0-0 -x soundon

and I copied the soundon script into /bin/

works perfect, but I'll try the other way.

Thanks for all the help :smile:

---

### Post by Joeb on 2005-06-09
[QUOTE=psychicdragon]You just want to run soundon whenever you start Gnome or whatever right?
This should work, I do the same thing with esd under Xfce.

gedit ~/Desktop/Autostart/soundon.sh

Insert this:
```
#!/bin/sh

soundon
```
save and you're good.[/QUOTE]

While this will work, it's not always the best solution.  Everytime you log into gnome (or xfce) it will run the code, however, depending on what you are running, that might not be what you really want.  For one thing, if what you are running is some kind a dameon and doesn't exit cleanly, you may be starting multiple instances everytime you log in and eventually you'll run out of resources.

Autostart works great for actual applications and things you want to start automatically, but should be used cautiously for system drivers, etc.

---

### Post by Joeb on 2005-06-09
[QUOTE=Darkelite]well, I followed the instructions you gave, and used the chmod line.  I put it in both rc3 and rc5

Im guessing on what the prefixes in the runlevel folders are, I assume K is to stop and S is to start, and the number is to specify the order.

One question though:

what is rcS.d?

Yes, the past three days has been made up of staying up until four in the morning reading this forum, ubuntuguide, asking friends who using linux questions, and experimenting myself.  Its amazing how much more I know in just three days.  :grin:

EDIT:  ok, I put it rc3 and rc5, its a no go.  I put in rc0, and i get the message error line xx, command "soundon" not found.  So I added cd /root/oss/bin, which is the exact directory that soundon is in, and still it won't work.

Any ideas?

EDIT2: If I open the run box and type : 

gnome-terminal -x /etc/init.d/soundon.sh

it just opens up a terminal and then closes.  That means the script is wrong right?

EDIT3: Ok, I decided to throw this into the sessions startup programs:

gnome-terminal --zoom=.28 -x soundon

the small zoom is because I don't really want it seen, I would be alot happier if I could find a way to make it totally hidden or minimized.

Other than that, it works great.[/QUOTE]


I believe rcS.d is for single user mode linux.  You shouldn't have to bother with it.  I'll have to look at what the K prefix stands for, I'm pretty sure you want to use the S prefix.  You'll notice they are all in the format SXXscript, where XX is a number.  The scripts are executed in the order the numbers, so S10script will execute before S35script, etc.  If there is anything in there that needs to load before your script, you would want to make sure yours has a higher number.

When you say you put it in rc3 and rc5, that's the symlink, right?  The actual script should be in init.d and only a symlink made to rc3 and rc5.

---


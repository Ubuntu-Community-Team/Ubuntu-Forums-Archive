---
title: "Quake 3 startup problem"
date: 2011-03-13
forum: Gaming &amp; Leisure
---

### Post by Rich3077 on 2011-03-13
I got Quake 3 installed and once I started the game and setting preferences I choose a resolution the game didnt like and it froze up.

Now I cant start the game because of the screwed up res.. it freezes my system needing a hard reboot.

What I am hoping is that there is a way to start the game with a different res with the terminal? 

Or anyone have other suggestions?

I am running Ubuntu 10.10

Edited to add: I am running an ATI 5770 video card... but I haven't found anything in catalyst control center that will help.

Edited again to add: The command  "quake3 -fullscreen -width 800 -height 600" did not work for me.
I will probably try to reinstall.

---

### Post by Rich3077 on 2011-03-13
Reinstalling didnt work.. perhaps I need to learn to uninstall now?

---

### Post by liamuk on 2011-03-13
edit ~/.q3a/q3ut4/q3config.cfg and look for r_mode. set it to -1
then look for r_customheight, set it to 600 and r_customwidth, setting it to 800, or whatever resolution you want

---

### Post by 3177 on 2011-03-13
> **liamuk said:**
> edit ~/.q3a/q3ut4/q3config.cfg and look for r_mode. set it to -1
then look for r_customheight, set it to 600 and r_customwidth, setting it to 800, or whatever resolution you want

yes and no
q3ut4 is a mod

to the OP:
follow the intructions  
but its in baseq3

---

### Post by Rich3077 on 2011-03-13
Found my problem.. the install instructions I followed had me install the game as root. If not then I didnt have permission to write to the default install folder. 

I have to log in to root before launching game and it works fine.

I would like to install this as a regular user... but I don't know how.

---

### Post by Rich3077 on 2011-03-13
[B]EDIT: Got it running. Dont really know how.. just kept messing with stuff. 


[/B]
Okay so Google tells me its a bad idea to install into /usr/local/games and to install in a local home directory so I installed into

home/dad/games/quake3

If I installed as root... then it was owned by root so I could not use the default bin location.

I created /home/dad/bin

for installing this game. Now I cannot start the game

Failed to execute child process "/home/dad/games//quake3" (Permission denied)

With over 10 hours trying to install this game I am frustrated. :(

---

### Post by Rich3077 on 2011-03-14
Okay now that I am installed I am trying to get the sound to work.. 
Google failed me.

Here is the message from the terminal

------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------

Upon checking, there is no folder or file in dev named dsp so its no wonder it cant open it.

EDIT: Info from Google

"Update (20/11/2010)
Just found out that the ubuntu developers decided the majority of people don&#8217;t need OSS support, so they compiled the kernel without it.

Quake 3 without sound in Ubuntu 10.10
Ubuntu 10.10 no /dev/dsp

Damn!!!
Posted by dirn at 11:40:00 PM"

Just in case that info helps?

---

### Post by Rich3077 on 2011-03-14
I am going to uprgade anyway because I installed the 32 bit 10.10 Ubuntu.
Would going to Ubuntu 10.04 64 bit help my problem at all?

---

### Post by Philsoki on 2011-03-14
I know it's Quake 3 you're trying to get up and running but I'll just put this here in case you might be interested/haven't hear about it: [http://openarena.ws/smfnews.php](http://openarena.ws/smfnews.php)

---

### Post by kaldor on 2011-03-14
And here's a reason why I wonder what id is up to when they port stuff to Linux. I've never gone without a fight or mildly annoying install process. What's wrong with a .run?!

---


---
title: "GOD **** IT!!! Someone PLEASE help me..."
date: 2006-03-11
forum: Desktop Environments
---

### Post by Cyclone268 on 2006-03-11
Ok, this whole linux thing is really starting to get annoying...

I installed ububtu onto my compute and everything went fine, when i go to boot up, it asks me for username and password which i give it.. THEN :evil: it comes up saying my graphica interface is not set up correctly.. and there are wierd characters all over the screen.. someone please help.

Il give some1 a few $$ for some advice that gets this working.

Thanks

Oliver

---

### Post by Sammi on 2006-03-11
Based on your temper and expectations you obviously should consider Mac OS Instead of Linux.

---

### Post by Cyclone268 on 2006-03-11
Yeah dude, sorry to all of you about that.. heh.

No, i really hate macs, and windows even more.

Thanks

Oliver

---

### Post by kseise on 2006-03-11
On the start up screen, below where you put in your name, there is a box that says "Sessions"  Click that and try to get into the failsafe mode.  From there, you can try and reconfigure your graphical interface.  I am a newbie also, so I can't walk your through that process.  

Or, if you are impatient as you seem to be (your are swearing at a group of volunteers), you can re-install Ubuntu and make sure you set everything correctly during the setup process.

---

### Post by kseise on 2006-03-11
[quote=kseise]On the start up screen, below where you put in your name, there is a box that says "Sessions"  Click that and try to get into the failsafe mode.  From there, you can try and reconfigure your graphical interface.  I am a newbie also, so I can't walk your through that process.  

Or, if you are impatient as you seem to be (your are swearing at a group of volunteers), you can re-install Ubuntu and make sure you set everything correctly during the setup process.[/quote] 
EDIT: Someone beat me to it, I don't mean to harp on you.  Apology accepted.  Try the rest of my suggestion thought.

---

### Post by kaamos on 2006-03-11
Look here: [https://wiki.ubuntu.com/CommonProblemsGraphics]("https://wiki.ubuntu.com/CommonProblemsGraphics")

---

### Post by Cyclone268 on 2006-03-11
Ok, well i dont really get a start up screen, i only get a black screen (lookslike a command prompt).. another person i saw had this same problem and a person on here told him to type in startx, and he said he gets fatal errors.. thats the ame thing with me..

Sorry,

Oliver

---

### Post by Cyclone268 on 2006-03-11
[QUOTE=kaamos]Look here: [https://wiki.ubuntu.com/CommonProblemsGraphics](https://wiki.ubuntu.com/CommonProblemsGraphics)[/QUOTE]


Thanks for that, it helped alot,everything is chugging along nicely, but it asks me for the Video Card's Bus Identifier, im not sure what to put here.. It has PCI :5:0:0 as the default, should i leave that or change it?

Thanks

Oliver

---

### Post by RJMacReady on 2006-03-11
[QUOTE=Cyclone268]Ok, this whole linux thing is really starting to get annoying...

I installed ububtu onto my compute and everything went fine, when i go to boot up, it asks me for username and password which i give it.. THEN :evil: it comes up saying my graphica interface is not set up correctly.. and there are wierd characters all over the screen.. someone please help.

Il give some1 a few $$ for some advice that gets this working.

Thanks

Oliver[/QUOTE]

Don't type startx after logging in. Type: ```
xorgconfig
```

Then follow the on-screen instructions, change settings etc. After Xorg is reconfigured, *then* type: ```
startx
```

EDIT: Whoops, already solved! Ignore.

---

### Post by Cyclone268 on 2006-03-11
Its ok, thanks for the time though. =)

---

### Post by rjwood on 2006-03-11
the detected bus id should be fine

---

### Post by Cyclone268 on 2006-03-11
Ok, I finshed all of that, now it comesup with an (EE) line sayin no devices found. Then is says no screens found

---

### Post by Cyclone268 on 2006-03-11
Pretty much tried every option availible..still, i get the error that it cant find  a screen.

Thanks

Oliver

P.S.-When i start up it says "Failed to start the X server (your grapical interface). It is likely that it is not et up correctly. Would you like to view the X server output to diagnose the problem?"

Thanks

Oliver

---

### Post by stanz on 2006-03-11
Hi All,
*Cyclone268, if your calmer now~ would ya try to change your thread title?*
I'm pretty new to linux myself, and need to remember- it's totally different, then the "point-n-click"-fix or reinstall OS.
I've messed up my 'X-server' a few times now, and it gets easier to 'remember' how to fix it!
If i remember right: right at start-up, you'll need to press 'Esc', when 'grub' starts its screen & gives ya the countdown.
you wanna get into 'Rescue' mode, which will give ya the commandline que:
***your@box:~$**  *{I believe your in 'root' at that time, what i type in is:
***sudo dpkg-reconfigure -phigh xserver-xorg**   *{and read well from there!
This code might be samething...i donno,
     *Code:   **xorgconfig***     {RJMacReady is on track.
Most of the 'default' choices, can be left alone.
Stay 'simple' when asked.
If when done, and your faced with a prompt again, type the: "***startx**"*  or "[I]**gdm**"
[/I]  (without my quotes) or i think: " ***sudo /etc/init.d/gdm start** " *works too.
Well, post how it works out for ya! Remember, i'm newbie too... \\:D/

---

### Post by Cyclone268 on 2006-03-11
[QUOTE=stanz]Hi All,
*Cyclone268, if your calmer now~ would ya try to change your thread title?*
I'm pretty new to linux myself, and need to remember- it's totally different, then the "point-n-click"-fix or reinstall OS.
I've messed up my 'X-server' a few times now, and it gets easier to 'remember' how to fix it!
If i remember right: right at start-up, you'll need to press 'Esc', when 'grub' starts its screen & gives ya the countdown.
you wanna get into 'Rescue' mode, which will give ya the commandline que:
***your@box:~$**  *{I believe your in 'root' at that time, what i type in is:
***sudo dpkg-reconfigure -phigh xserver-xorg**   *{and read well from there!
This code might be samething...i donno,
     *Code:   **xorgconfig***     {RJMacReady is on track.
Most of the 'default' choices, can be left alone.
Stay 'simple' when asked.
If when done, and your faced with a prompt again, type the: "***startx**"*  or "[I]**gdm**"
[/I]  (without my quotes) or i think: " ***sudo /etc/init.d/gdm start** " *works too.
Well, post how it works out for ya! Remember, i'm newbie too... \\:D/[/QUOTE]
Hey thanks for that... im stuck at a wierd screen.. it says:

Select the X.Org server modulesthat should be loaded by default:

Then the choices are: GLcore,bitmap,dbe,ddc,dri,extmod,freetype,glx,int10,record,type 1, v4l, vbe... =(

Which ones should I choose?

Thanks

Oliver

---

### Post by Cyclone268 on 2006-03-12
Still very confused....

---

### Post by RJMacReady on 2006-03-12
Don't pick any new modules. All the required modules are set by default, so just press enter.

---

### Post by Cyclone268 on 2006-03-12
Heh, well im an idiot and checked them all... =(

Does this really matter?

Could it be my problem?

Thanks

Oliver

---

### Post by RJMacReady on 2006-03-12
So, you reconfigured your Xorg.conf file and you still cant start an Xserver?

---

### Post by Cyclone268 on 2006-03-12
Thats how it looks, im trying ubuntu live as we speak... maybe that will be better.

Thanks

Oliver

---

### Post by stanz on 2006-03-12
Hi All,
Cyclone268~ How it coming along? Geez- look at ya...your moving right along!
I notice you need to 'read', those detailed instructions like me...2 or 3x !
It's kewl, ...we're like- learning a new language here too.
That one 'weird screen'...mentioned ya can leave 'em 'as is'. And I Do.
Your almost done with this...
Now, you'll come to a time when you'll answer a question...and your screen will flicker- kinda- 
and at the bottom of your screen- you'll notice your back in 'commandline' mode.
It'll tell ya your gonna re-write, or over-write- your config file [or something like that]  
Thats when i hit the power/restart button, on my box.
I think only once, i was able to restart gdm from there...?  Anyone know for sure?
Sooo...A Day Later, and some smiley helpful faces, wondering~ Howz it goin`??       :razz:
HA~~ Sooo?? Your in and working??

---


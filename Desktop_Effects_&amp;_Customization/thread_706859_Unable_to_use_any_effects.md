---
title: "Unable to use any effects"
date: 2008-02-24
forum: Desktop Effects &amp; Customization
---

### Post by Kasa on 2008-02-24
hi.
Every time I click to enable the normal or any effects it logs me out .
I have  used the effects before I was using the Compiz effects. 
my gfx card is a Nvida 8600.
I believe the problem to be the restricted driver.
Also my monitor seems to be changing every time i long in.
the res should be 1650x850 60hz.
This is not makeing much sense seeing I was just using it before.
(tho i found out that i was runing the effect without the restricted drive, I enabled it and this is wat happens.)
now i can have it off and run the effects.

---

### Post by overdrank on 2008-02-24
> **Kasa said:**
> hi.
Every time I click to enable the normal or any effects it logs me out .
I have  used the effects before I was using the Compiz effects. 
my gfx card is a Nvida 8600.
I believe the problem to be the restricted driver.
Also my monitor seems to be changing every time i long in.
the res should be 1650x850 60hz.
This is not makeing much sense seeing I was just using it before.
(tho i found out that i was runing the effect without the restricted drive, I enabled it and this is wat happens.)
now i can have it off and run the effects.

HI and welcome, you may look at Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Kasa on 2008-02-25
Well Now i have run into a new problem.
Resolution Out of range :/.
If there is some code that I could put into the recovery mode to fix this, please tell me.

---

### Post by overdrank on 2008-02-25
> **Kasa said:**
> Well Now i have run into a new problem.
Resolution Out of range :/.
If there is some code that I could put into the recovery mode to fix this, please tell me.

Hi and in recovery mode you can use this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` 
Then the command reboot.

---

### Post by Kasa on 2008-02-25
Will try it now then envy if I can get some GUI going.

---

### Post by Kasa on 2008-02-26
OK.
Heres a cycle of my "attempt" at this problem

Install envy
Restart

Out of range

reboot into Recov
```

Sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot

Load Ubuntu

Click Custom effect (compiz)
Please install Graphics Drive restricted
PLease reboot
reboot

Load Ubuntu 

Res out of range

reboot into Recov 
```

Sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot

 load into ubuntu 
Click Custom effects (or any other effect other then none)
Please install restricted drive
Reboot

Load Ubuntu
Res out of range

(is there any way to fix this so it will load into ubuntu with the blood drive active.)

---

### Post by Kasa on 2008-02-26
New bit of news.
Seems that I got it active and in the right res BUT
when I click on anything other then normal.
It crashes back to login.
ALSO
my gfx cards fan starts up which never happens :?
I am worried for my cards health now.
AND ARE LOOKIN BACK TO VISTA WITH HAPPY MEMORYS

---

### Post by Kasa on 2008-02-26
Worked out the problem.
I tryed uninstallin Compiz and all its files.
then clicked on normal.
it worked
reinstalled it
clicked on special
crashed and showed the login screen.
I NEED HELP

---

### Post by Therion on 2008-02-26
Are you using an LCD or CRT monitor?  Either way, I've never seen or heard of a monitor resolution of 1650 x 850; where are you getting those numbers?  Also, it appears to me Envy is telling you the resolution is "out of range" which would seem to confirm those numbers are not correct for your monitor.  I've never seen anything higher on a standard monitor than 1600 x 1200.  

Try using Envy to uninstall the nVidia driver then reinstall the driver and select a standard resolution like 1024 x 768 for starters.  If you want to adjust that later you can always edit your xorg.conf file, but for now how about we just get you to the desktop and a stable system?  Sounds like a good idea to me.

---

### Post by Kasa on 2008-02-26
Let me correct my mistake.
my current resolution (which works on vista) is 1680x1050 60hz LCD
Sorry for the confusion I was trying to remember it of the top of my head from work.
I have fixed the Out of range problem, But I will try uninstallin the drive and reinstallin it for the 12th time to make you happy.
I still don't understand why after activating Compiz it crashes back to login.

---

### Post by Kasa on 2008-02-26
I would like t0 add my Apologies, I have been very angry with ubuntu and I let it out on you. I am sorry.
and glad for you help

---

### Post by Therion on 2008-02-26
No apology necessary, but thank you.

So now, everything works until you attempt to use the advanced desktop effects.  Enable those and **BOOM** -- everything goes to hell and you find yourself at the login screen, correct?

Have you tried lowering your resolution, even if it's just to humor me?  Drop it down a couple notches and just see what happens.

---

### Post by overdrank on 2008-02-26
> **Kasa said:**
> I would like t0 add my Apologies, I have been very angry with ubuntu and I let it out on you. I am sorry.
and glad for you help

Hi and I understand your frustration and have you consider another distro? There are others that may work better on your system.

---

### Post by Kasa on 2008-02-26
I have worked out the problem.
It seems that Compiz manager hates the new 8600 cards (well not new now the 9000 are coming out)
I clicked on the "custom, Normal or any effect" boom loads into login, login again and my gfx card starts making sounds as if its about to take off.
I started to think why not totally uninstall Compiz (all drivers, everything)
So I did. rebooted, and My gfx card stop trying to take off.
I think its a lack of compatabilty with the Compiz drive and the Nvida drive.
Any Ideas of another distro to try ?
as much as I woud love to take hours reinstallin and redoing everything (which took 3 DAYS :?)
I would like to get this to work.
Unless its unfixable.
Now I will lower my res to 1024 x 768
when thats done I will install Compiz and all its drivers (fusion aswell)
If it still wont work and my gfx card takes off, I will be out of options.

---

### Post by Kasa on 2008-02-26
1. changed res to 1024 x 768
2. reinstalled Compiz
3. rebooted
4. clicked on any effect
5. crashed to login screen
6. gfx trys to take off
7. uninstalled compiz
8. going to reboot after post and reset res, and hopefully stop gfx takeing off.

---

### Post by Kasa on 2008-02-26
K, I am out of ideas.
totally out of ideas.
any help would be great.

---

### Post by Therion on 2008-02-26
You know what... Try Ubuntu Ultimate (see my sig line).  I had no end of trouble with getting a good install until I tried installing Ubuntu Ultimate Edition.  Everything worked for me (for the first and only time) right out of the box with it.

---

### Post by Kasa on 2008-02-26
1.6 gig :O
meh y not :P.
but still its going to take ages to dl ::( then install.
What system are you running it on ?
(just to see if mine could fair anybetter :p)

---

### Post by Therion on 2008-02-26
> **Kasa said:**
> 1.6 gig :O
meh y not :P.
but still its going to take ages to dl ::( then install.
What system are you running it on ?
(just to see if mine could fair anybetter :p)
:)  1.6 gig of delicious Ubuntu goodness.  I don't know why, but seriously, I tried plain old Ubuntu, Fedora 8, PCLinuxOS, Mandrake and Open SUSE.  Not one of them installed/ran on my PC worth a damn.  Then I found the Ultimate Edition and... Wow... Smooth install right from the start and it ran like a greased pig.  Always has... For me it's the magic distro that JUST WORKS.

Specs are as follows:

Asus A8N-32-SLI Deluxe mobo
AMD-64 4200+ Dual Core Proc.
nVidia 8800GTS 320MB
2 GB of Corsair RAM
Dual hard drives: 200GB SATA master & 120GB backup/slave drive

Try Ubuntu Ultimate... I'll cross my fingers for you!!!

---

### Post by Kasa on 2008-02-26
I will, Unless someone here can fix this bloody problem ;p.
I will download today, then burn install and hope to god it works ;p

---

### Post by Kasa on 2008-02-27
Ok, I installed it did everything its said.
BUT I tried ctrl+alt+f2 the page keeps refreashing with "cdrom (ioctl) error".
I am yet to try beryl I am updating it to Ultimate gamer addition (no idea what that will do, but if anything should help with gfx problems if i have one ;?)
DOOD I am still unsure about how to get the effects going as I am yet to install the restricted driver.

---

### Post by Therion on 2008-02-27
Oooookay... I have no idea what you're trying to tell me in that last post.  Can you tell me just "yes" or "no" to the following two questions, please:

1.  Did you get a clean install?

2.  Are you able to simply use this version *right now*; meaning can you get to the desktop, run applications, etc. even if things like your display are not exactly what you want?  In short, is the install *working correctly* at this point?

Assuming the answers to the above questions are "yes", we can move on to installing the Restricted Driver.  For this, I suggest you use Envy.  Envy is pre-installed so all you need to do is run it.  MOST LIKELY when you reboot, after installing the new driver, you will still need to *enable it* manually via the Restricted Driver Manager (I did).  Also, most likely, your monitor's resolution will be set at 600 x 480 and you will need to manually configure xorg.conf to get the correct screen resolution.  That's easy though.  

Post back if you have issues.

---

### Post by Kasa on 2008-02-27
Yes to both.
I installed envys driver, then clicked the restricted driver.
rebooted
"low graphics mode is active please configure display and gfx"
did so loaded in 
"CDROM (ioctl) error"

Resolution is set at 600x480
cant not change that res.
restricted driver is not active.
If I change the res the screen goes unreadable. (barcode like)
if anything I can't get it active. I will try again, after reinstallin envy (seems when restricted driver is active it deletes envys drive.

---

### Post by Kasa on 2008-02-27
Got it working only one thing not,
Extra wont work "could not be activated"
normal works but thats all.
anyideas now ?

---

### Post by Kasa on 2008-02-27
Ok I got it working, Now would I have to install Compiz-fusion or is it install atm.
I can see emerald and the compiz-fusion logo but cant click or use the compiz-fusion logo.
Should I dl the csm

---

### Post by Therion on 2008-02-28
Go here and enable the extra repositories (the two without the check-marked boxes): 

System > Administration > Software Sources

Then install CCSM:```
sudo apt-get install compizconfig-settings-manager
```

You still need to get your driver issue fixed however.  I'll post back on that in a minute.

Okay, back now.  From reading your post's it sounds like you have the Restricted Driver* installed*, but not *activated*, since activating that driver hoses your display.  In order to use the really cool Compiz stuff the Restricted Driver MUST be activated, so we need to do that.  Do that now and just deal with the 600 x 480 for the time being, you'll fix the display now by manually configuring your xorg.conf file.  

Back-up your existing xorg.conf file:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Now open your xorg.conf file and change the default resolution```
  sudo dpkg-reconfigure xserver-xorg
```

Use the Tab button to move around and highlight in red, the defaults for everything until you come to the part about Monitor Resolutions.  Look closely here...  There will be a little window with all the screen resolutions you can choose from, even though you'll only see about six or eight in the window (you can scroll up for higher resolution choices).   

Choose three resolutions here by using the spacebar to put an "*" in the ones you want to be able to use -- *the HIGHEST RESOLUTION you choose here will be the new default screen resolution.*  

Use Ctrl+X to overwrite the file with your changes, Save and Exit.  

Cross your fingers for good luck.

Use Ctrl+Alt+Backspace to restart X.

You should now have a decent screen resolution, the Restricted Driver should be in use and you should be able to use all the cool effects that come with Compiz Fusion.

---


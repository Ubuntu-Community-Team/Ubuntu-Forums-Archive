---
title: "CompizFUSION not inititaing"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by mike_302 on 2007-10-18
I FINALLY installed compiz fusion (not very easy seeing as only ONE site was able to tell me i needed to change repositories because I have AMD64 Ubuntu...) Anyways, IT installed all fine as far as I can tell, but when I do Alt+F2 and type compiz --replace , nothing happens. the window closes and everything is ... normal. I can;t rotate an cube.. nothing. I go to System Preferences to open the compizconfig Settings manager and when I click it, nothing happens... The menu closes and still normal. No loading, no error.. I tried erestarting, but that did nothing for me either. Anyone know what is going on?

---

### Post by mike_302 on 2007-10-18
bump... Not to sound impatient :S I always fear getting flamed out of forums for this but... Am I making posts the wrong way or something because I was under the impression that linux forums made replies VERY quickly. I've had to bump all of my threds seeral times before I got an answer after a day or two. I DOOOO look for my problem before I post but I don't always find the answer I'm looking for. Anyways, I don't want to piss anyone off... Just wondering if I'm not making my threads interesting enough to get many reads or something...

So can anyone answer my ORIGINAL question?

---

### Post by mike_302 on 2007-10-20
bump... again... I must be missing SOMETHING. Please? Can someone help me?... Ummmm, I'm not sure what else to say. All I'm wondering is if omeone either KNOWS the problem that is going on or can troubleshoot this issue with me... Maybe i'm missing a file or something. Who knows, but here is the post again!

I FINALLY installed compiz fusion (not very easy seeing as only ONE site was able to tell me i needed to change repositories because I have AMD64 Ubuntu...) Anyways, IT installed all fine as far as I can tell, but when I do Alt+F2 and type compiz --replace , nothing happens. the window closes and everything is ... normal. I can;t rotate an cube.. nothing. I go to System Preferences to open the compizconfig Settings manager and when I click it, nothing happens... The menu closes and still normal. No loading, no error.. I tried erestarting, but that did nothing for me either. Anyone know what is going on?

---

### Post by Faud on 2007-10-20
Can you please post your system specs and try running compiz fusion in the terminal and post the output.
Please try and wait 24 hours before you bump a thread. All of us here want to help you out we just cant be signed on all the time and I know that people do go back and look for unanswered threads.
Dont worry though, we will get you up and running.
Also what site did you use to instal it ?

---

### Post by Doctoxic on 2007-10-20
if you try and run the config gui from the terminal do you get this?

doctoxic@linux:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'


there seems to be a lot of people with this problem

doc

---

### Post by mike_302 on 2007-10-20
Ok, I'll check that out once  get back to THAT computer. Thanks for the responses and.. Now I at least understand about the posting. I'll be sure to wait.

System specs: 64MB shared ATI Radeon XPRESS 200M , 1GB DDR RAM, 100GB Hard drive (20GB for Linux, 75 for XP, 5 GB shared FAT32), AMD Turion64 (ML-34) --- Laptop, Gateway MX6425 (googling that model will give you every spec you could ever want on the gateway computer profile page)

---

### Post by mike_302 on 2007-10-20
as for which repositories, I'm not AT the computer to confirm this but i BELIEVE it is this one: [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy-amd64 and... another very similar. I think I had followed the basic/common instructions that I found for installing compizfusion, but they kept failing, and eventually I found one that gave the correct repository and.. I THINK i had noticed that the only difference was that the NEw one had the amd64 at the end of the line. Since im running the amd64 ubuntu, it finally installed (seemingly without a problem)... But clicking on the app in the Preferences menu doesn't do a thing. I'll run it from terminal as soon as I can (probably tomorrow at earliest) and let you know what happens there. What exactly am I typing in to the terminal to make it run from terminal? I'm not familiar with the command line too much yet since I'm only recently converted from my former Micro$#!t religion... ;)

---

### Post by Faud on 2007-10-20
Are you running and XGL session ?

---

### Post by mike_302 on 2007-10-20
Haha, MIGHT be. Don't even know waht that is exactly. I recognize it as something to do with video.. the driver? I know I installed the prop. restricted driver for my video card... Wahtever that means... Some of this "Licencing" and proprietory and.. other stuff is confusing to me as a former windows user.

---

### Post by Faud on 2007-10-20
Ok bud, when you get home Just try and run compiz from the terminal and post the output and we can go from there.

---

### Post by mike_302 on 2007-10-20
All right, but .. What exactly am I typing into the terminal when I DO try to run this...

---

### Post by Zyphrexi on 2007-10-20
I had the same output, now I think this is because compizfusion from trevinhos repos are for feisty, and now gutsy doesn't appreciate. I'm sure there's a more complex reason why, but I don't feel like wasting time understanding the logic. 

I know this however:

My compiz fusion from there is still installed, meaning the official gutsy repo version is not installed.

During the upgrade process, external (non-gutsy) repos were disabled, this is fine.


I'll post a solution when I solve the problem.

EDIT:: apparently my assumption was incorrect, as the gutsy version is installed. annoying... 

YETANOTHEREDIT:However ccsm can be run by selecting

Package -> force version in synaptic and selecting the (gutsy) version instead of trevinho's repo version. after forcing the version, run in terminal ccsm, and it should work fine.
worked fine for me.

---

### Post by mike_302 on 2007-10-21
HMM... not looking good?  

mike@mike-laptop:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

BTW! This is a FEISTY ubuntu.

---

### Post by Doctoxic on 2007-10-21
> **Zyphrexi said:**
> .. 

YETANOTHEREDIT:However ccsm can be run by selecting

Package -> force version in synaptic and selecting the (gutsy) version instead of trevinho's repo version. after forcing the version, run in terminal ccsm, and it should work fine.
worked fine for me.

this worked for me :)
many thanks

when i looked at CCSM in synaptic there was 2 installed versions one Gutsy and one other (from my previous setup i assume) - so forcing the Gutsey versions seems to have fixed it as i can now open the custom preferences


doc

---

### Post by mike_302 on 2007-10-21
I found that I needed to install Xgl or whatever... I followed some instruction to have it start up (by user option) when I login. So once I did that, a DIFFERENT error message is showing up on the Terminal:

mike@mike-laptop:~$ compiz --replace
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libccp.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ccp'


What's up NOW?...

---

### Post by mike_302 on 2007-10-22
...maybe I should also note that upon trying "compiz --replace" again, certain aspects begin to appear/happen. The session windows in the bottom right of the screen merge and grow into one LONG one (for the cube I'm asuuming), and the window borders all disapear and suddenly my windows are screwed up until I do a system restart  (or until I log out and in which I can't do anymore --- See my OTHER forum that is not being answered in General Help about the log out problem)

---

### Post by mike_302 on 2007-10-22
ooo k,.. waited a day since I've last gotten a reply... bumping.

---

### Post by BungaMan on 2007-10-23
edit: didn't notice the second page... doh!

---

### Post by mike_302 on 2007-10-23
annnd another 24 hours (give or take a few minutes)

---


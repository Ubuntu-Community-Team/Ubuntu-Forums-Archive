---
title: "Trouble starting oscilloscope program"
date: 2008-10-06
forum: Desktop Environments
---

### Post by Fishead on 2008-10-06
Hey, I am having a hard time getting a program to execute.  I am pretty new at linux, so thanks for your patience.  I am also pretty determined to get past these stupid problems that have previously caused me to give up in frustration.

I am trying to use ll-scope, but when I click on the button in applications/sound & video/oscilloscope nothing happens.  What am I doing wrong?

Thanks,

Chris.

---

### Post by caljohnsmith on 2008-10-06
If you right-click the applications menu, select "edit menu" (or whatever it exactly is), select your oscilloscope program in the menu editor, and see what command is used to run it. Copy that into a terminal (applications > accessories > terminal) and see what happens when you try and run it from the terminal; probably it will output some errors. Please post the results so we can see.

---

### Post by Fishead on 2008-10-06
Thanks for replying.

The command: jack-dssi-host ll-scope.so

The results: 

jack-dssi-host: Warning: DSSI path not set
jack-dssi-host: Defaulting to "/usr/local/lib/dssi:/usr/lib/dssi:/home/fishead/.dssi"


jack-dssi-host: Error: Failed to connect to JACK server

---

### Post by Fishead on 2008-10-09
Hey.  Just wondering if someone can explain what this means.  I figure it is pretty obvious to someone with a bit more experience then me, but I still don't know what's going on.  

It isn't a huge issue as I found a REAL oscilloscope, but I would like to figure this out for the sake of knowing what's up.  I have tried linux several times over the years, and never gotten over the hump of getting everything working.  

Thanks for your patience.

Also if anyone knows of a good tone/signal generator program...

---

### Post by caljohnsmith on 2008-10-09
I've never used that oscilloscope program, nor do I use pulse audio (which is related to your jack error), so I can't be of much help there. But a good program for generating single tones (frequencies) is Audacity; you can even mix multiple tones together and things like that if you like. Just open up your Synaptic Package Manager and you can install Audacity from there.

---

### Post by viper3two on 2008-10-09
Hi
I am new to Linux as well, and loving Ubuntu!
I have a few audio programs and I know that you have to run Jack first before you launch your program. Judging by that error (Error: Failed to connect to JACK server), I would say to run Jack then the scope program after Jack loads up. I don't know if this will work or not as I dont have the scope program. 
Also it looks like if you are starting Jack first then it has something to do with Jack not starting up properly. I would look at Synaptic package manager to see if you have Jack, then remove/reinstall it. Hope this helps and good luck.

Tony

---


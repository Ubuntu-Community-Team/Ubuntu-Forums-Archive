---
title: "Compiz using up all video ram ( Black Windows )"
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by RAH66 on 2007-06-26
I ran into this problem when I installed Compiz Fusion.
I found that when I open allot of windows I start seeing allot of black windows and even menu items... 

Did some research and found on another post that this means that compiz or wateva has used up all of my video ram ( Nvidia GeForce 6600 GT 128 mg ) but thought that is strange :confused: coz isnt the card supposed to start using system ram when it runs out of its own ram like it does in windows? 

(BTW running 2gigs system ram and even with a ton of apps and windows open only 30% at most is ever used )

Anyway just wanted to know if there is any way to fix this or to enable that my card can start using system ram when it runs out of it's own ram...
:?:

---

### Post by AriciU on 2007-06-26
Start it up with:

compiz --replace --indirect-rendering

and see if it works better.

Beware though. I lost the abbility to CTRL+ALT+Backspace (restart GDM) when i started it that way... Everything froze and i had to do a hard reboot.

---

### Post by RAH66 on 2007-06-26
ok I'll check it out...

---

### Post by RAH66 on 2007-06-26
LOL sorta got better instead of total black windows I got semi empty windows meaning the spaces came up were the stuff should be but no content looks like it fixed the black menus though coz although the windows are "empty" the menus still worked fine.

I think you are on the right track... :D

thanx for the input gives a guy hope u know...

[IMG]http://www.optix.co.za/rahstuffdontdelete/Screenshot.png[/IMG]

---

### Post by AriciU on 2007-06-26
I have a 6800GT with 256mb and i just opened like 15 of those windows without a glitch. And i don't start with the command i just posted. Must be some setting somewhere i guess.

Hope someone else chimes in...

Does ctrl+alt+backspace work now btw or does your system freeze for good?

---

### Post by RAH66 on 2007-06-26
LOL yeah thats the funny thing no freezes nothing and my system was running smoothly with 25 windows which of 7 were empty spinning the cube playing music running windows xp in virtual box everything no lag nothing...

all I did was close them all and when I opened new windows they were fine...

very strange :confused::-k  lol well I needed a reason to go get that 8800 hey :-\"

---

### Post by eyelessfade on 2007-06-26
It's a nvidia driver bug. They have said they will fix it

---

### Post by RAH66 on 2007-06-26
Hectic do you know when they would have a fix ready for this BUG argh!!!
or lets put it this way when did you hear they are working on it?

---

### Post by diafanos on 2007-06-30
> **RAH66 said:**
> Hectic do you know when they would have a fix ready for this BUG argh!!!
or lets put it this way when did you hear they are working on it?

I came across with this:
> 
This driver does not fix the black window bug issue that some Beryl/Compiz users experience (still a few more months until it will likely be resolved).
 

 [here]("http://www.phoronix.com/scan.php?page=article&item=745&num=1")

I don't know the reliability of this site, but I hope it's true, cause black window bug is a really annoying one...:???:

---

### Post by RAH66 on 2007-06-30
Yeah it's very anoyin anyway when I booted my pc I checked new updates including a
nvidia-glx driver update so hopefully this fixes some issues. Let you know if I see any changes...:D

---

### Post by onero on 2007-06-30
Yup, it's an nvidia bug. I don't use compiz fusion, but in Beryl, I set the rendering platform to "Force AIGLX" (I was using the Nvidia rendering platform before). I figure compiz should have a similar setting. Anyway, that seems to work for me; I haven't been getting any black windows lately :D

---

### Post by RAH66 on 2007-07-01
That sucks so you are saying that you don't get these issues with beryl? and what card are you running?

oh yeah the driver update didn't do anything to the black windows opening google earth and 3 windows was enough to have them start going black... :(

---

### Post by TopasPV on 2007-07-05
> **onero said:**
> Yup, it's an nvidia bug. I don't use compiz fusion, but in Beryl, I set the rendering platform to "Force AIGLX" (I was using the Nvidia rendering platform before). I figure compiz should have a similar setting. Anyway, that seems to work for me; I haven't been getting any black windows lately :D

Thank you very much! I'm using Beryl and I had this black window bug, too. By using "Force AIGLX" this problem is gone. Good work, I was getting a bit upset.. :)

---

### Post by diafanos on 2007-07-06
I found a workaround for the black window problem (compiz-fusion).

1. Open compiz-manager file (in /usr/bin)
2. Find the line: ARGs=... and add option --indirect-rendering

in my file now it looks like this: 
> 
ARGS="--sm-disable --replace --indirect-rendering"
3. Save file and restart compiz (run compiz-manager)

I did it and now I don't have any black window, even if I open more the 20 windows....:):)
Also I did not spot any side-effect......

---

### Post by kansei on 2007-07-06
The only 'compiz-manager' on my computer is an icon.. /usr/bin/compiz and /usr/bin/compiz.real exists.. that's it though.

---

### Post by reacocard on 2007-07-06
> **kansei said:**
> The only 'compiz-manager' on my computer is an icon.. /usr/bin/compiz and /usr/bin/compiz.real exists.. that's it though.

Edit /usr/bin/compiz so that the line like this
```
COMPIZ_OPTIONS="--ignore-desktop-hints"
```
becomes this
```
COMPIZ_OPTIONS="--ignore-desktop-hints --indirect-rendering"
```

---

### Post by kansei on 2007-07-06
Thanks.. I quickly skimmed the file and searched for "ARGS" so didn't find that. I'd rather turn off desktop effects entirely than use indirect-rendering though.. still searching for a real solution :P thanks

---

### Post by diafanos on 2007-07-07
> **kansei said:**
> The only 'compiz-manager' on my computer is an icon.. /usr/bin/compiz and /usr/bin/compiz.real exists.. that's it though.

Sorry, I thought you use Compiz-fusion not Compiz...
I don't know about Compiz...

---

### Post by reacocard on 2007-07-07
> **diafanos said:**
> Sorry, I thought you use Compiz-fusion not Compiz...
I don't know about Compiz...

Well, I use compiz-fusion and I don't have a compiz-manager either.

---

### Post by diafanos on 2007-07-07
> **reacocard said:**
> Well, I use compiz-fusion and I don't have a compiz-manager either.

OK, then compiz-manager is probably just an additional  script to initiate compiz....
I didn't know it...
I just followed [_THIS_]("http://ubuntuforums.org/showthread.php?t=485284") howto which includes a compiz-manager script file....

---

### Post by kansei on 2007-07-07
yeah I am using fusion (I'm on gutsy gibbon).

I wish I could remember how I got it totally working in feisty (with beryl + aiglx + nvidia). I have a feeling it has something to do with 'force aiglx' or something like that in the beryl menu.

---

### Post by Alex&amp;Linux on 2007-07-08
Same here, I had beryl running perfectly, but no such luck with Compiz Fusion (on Feisty)
According to information regarding the error on the beryl bug tracker forum, this is attributed to a fault in the Nvidia GLX driver while handling texture from pixmap rendering (faster, but not supported widely yet)
The fix was to change rendering to "copy" which most adapters handle well
Does anyone know how to change this in Fusion?
Otherwise, looks like we'll be waiting for Nvidia to get their $#!+ together!

---

### Post by kansei on 2007-07-08
Isn't using 'copy' totally bypassing the nice hardware acceleration that nvidia supports for this? Is the performance as good using copy mode as using direct rendering (while direct rendering works for you).

---

### Post by phssthpok on 2007-07-09
the "copy" performance is not great, but acceptable for nvidia users whose only other option to avoid black windows is to take nvidia's advice and "not use compositing".

it seems that indirect rendering in compiz-fusion does not have the same behavior as "copy" in beryl when running on nvidia hardware -- in compiz-fusion, yes, the black windows go away, but when opening new windows, at the point where i *would have* got a black window, i get a normally painted window which appears and is totally unresponsive. closing other windows makes the unresponsive one come to life.

any idea how to get something closer to "copy" behavior until nvidia comes through with their fix?

---

### Post by Alex&amp;Linux on 2007-07-09
It has to be available somewhere in compiz.
The config manager doesnt seem to have it, so perhaps by altering the code?
I'll see if I can get a response from the team on that one.

---

### Post by RAH66 on 2007-07-09
why didn't they just use beryl as the platform and called it beryl fusion becuase compiz to me now seems more buggy than beryl. sometimes starting up compiz makes strange things happen like funny effects on desktop fonts and restarting compiz fixes this and in beryl i tested with a friend that you can open a shaiyt load of windows and no black windows appear ( he has the same card as I have NVidia GeForce 6600 gt ) an in compiz I open about 7 or 8 depending on what the windows contain they start showing up black???

but anyway all will be well just need to chill for now till they get this fixed...:(

oh yeah and the 3d window plug inn for compiz to make the windows lift off of the desktop is also crappy, like when you drag a window to the corner of the cube it gets cut in half a piece of window for each desktop 
( how nice )

---

### Post by kansei on 2007-07-09
well of course we should just 'chill'.. if you are using compiz fusion on gutsy gibbon, then you know full well what you were getting yourself into. It's another 3 months until it becomes the release version, and at that point who knows of compiz-fusion will make the cut in general (nvidia issues nonwithstanding).

---

### Post by Alex&amp;Linux on 2007-07-10
Hey guys, take a look at this:

[http://www.nvnews.net/vbulletin/showthread.php?t=77030](http://www.nvnews.net/vbulletin/showthread.php?t=77030)

Looks like the latest driver supports texture from pixmap, no need for indirect rendering as well.

Though, I'm having a bit of difficulty installing the driver, which comes before playing around with xorg.conf.

Any ideas?

---

### Post by RAH66 on 2007-07-11
Well Im back to using beryl gona wait till compiz can catch up aswell as the nvidia driver bug...
meez gona play some command & conquer 3....

---

### Post by nuktar on 2007-07-11
Yea, I agree.  Compiz sucks unless you have a powerful machine.

---

### Post by kansei on 2007-07-11
> **Alex&Linux said:**
> Hey guys, take a look at this:

[http://www.nvnews.net/vbulletin/showthread.php?t=77030](http://www.nvnews.net/vbulletin/showthread.php?t=77030)

Looks like the latest driver supports texture from pixmap, no need for indirect rendering as well.

Though, I'm having a bit of difficulty installing the driver, which comes before playing around with xorg.conf.

Any ideas?

Well those new drivers still have the black window bug. blah

---

### Post by mithion on 2007-07-13
I am using a Geforce 2 (32 megs of video ram) and I was experiencing the black windows after opening 3 or 4 windows.  Using the --replace --indirect-rendering argument, this solved my problem.  I opened a dozen windows none of which displayed black screens.  Performance was sluggish though due to the archaic hardware, but if I only use 2-3 applications (which is the case for me), performance is quite adequate.

---

### Post by RAH66 on 2007-10-10
well I will look into that:confused:

---

### Post by VictorR on 2007-10-11
I had the same problem recently on GeForce 4 MX440 with 64 MB of VRAM. My post in this forum was completely ignored, so I had to dig myself and found two options (I use both):
1. use --indirect-rendering
Instead of getting in troubles changing configuration files I just included it in the startup line , which launches Compiz-Fusion:
  ```
compiz --replace --indirect-rendering -c emerald
```
2. do NOT use any transparency for Cube, I mean the rotating Cube must be completely opaque. Other effects, like cube reflection and Skydome can be ON.

Since I applied those two to my CF settings I have never experienced the "black window" problem.

---

### Post by RAH66 on 2008-01-11
LOL Running the 8800 now no window border anything isseus...:)

---

### Post by mjamesd on 2008-02-18
I'm on Ubuntu Gutsy 7.10 with nVidia 6800 GT (I think) and compiz-fusion. I edited the /usr/bin/compiz file, line with COMPIZ_OPTIONS to be this:
```

COMPIZ_OPTIONS="--ignore-desktop-hints --indirect-rendering --replace"

```

and I stopped getting black windows. Good luck, everyone.

---


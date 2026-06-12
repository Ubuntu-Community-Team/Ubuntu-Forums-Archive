---
title: "Turning monitor off at night, awaken by itself in the morning?"
date: 2009-03-03
forum: General Help
---

### Post by provide on 2009-03-03
I'm almost done building a laptop "picture frame". You can get more information about such a project [here]("http://www.thesandersens.com/blog/linux-powered-digital-picture-frame"). I'm using Ubuntu Server 8.04.1.

I'd like to have the laptop turn its screen off at 8 P.M. every night and awaken itself at 6 A.M. 

I was having an issue whereas the screen would blank out every 20-30 minutes, so I added this to xorg.conf:

Added to Monitor section:

       Option          "DPMS"

And added to ServerLayout section:

        Option          "BlankTime"     "0"
        Option          "StandbyTime"   "0"
        Option          "SuspendTime"   "0"
        Option          "OffTime"       "0"

I imagined that DPMS could be turned on and off so I tried it at the command line and sure enough **xset dpms force off** turned the screen off. Pressing a key woke it back up. I tried to enter that command into cron by:

crontab -e

then adding:

00 20 * * * xset dpms force off
00 06 * * * xset dpms force off

saving, closing, etc...restarting cron and/or rebooting still doesn't help in turning the screen on or off. I've checked the laptop's time and it is accurate. 

Any advice? I really like the idea of turning an old laptop into a digital picture frame; I just don't need it to be on in the middle of the night. :)

Thanks in advance for any response.

---

### Post by rjmoerland on 2009-03-03
Guessing: possibly it's due to the fact that cron runs as root, in a desktop-less environment. xset hasn't got a clue then which X environment it's meant to run in. Actually, you might have a look at my 'balloon tips for dying drives' script ([http://ubuntuforums.org/showthread.php?t=1031244]("http://ubuntuforums.org/showthread.php?t=1031244")), since it tries to overcome some of the trouble you run into when a program is run as root and needs access to the local desktop environment. 

Good luck!

---

### Post by heindsight on 2009-03-03
> **provide said:**
> 

crontab -e

then adding:

00 20 * * * xset dpms force off
00 06 * * * xset dpms force off


Cron doesn't run a command with the same environment variables set as when you run it interactively. Chances are that when cron runs xset, the DISPLAY environment variable is not set, so xset doesn't know which display to act on.

Try changing your crontab to the following and see if that works
```
00 20 * * * xset -display ":0" dpms force off
00 06 * * * xset -display ":0" dpms force on
```

That seems to work for me, except that 
```
xset -display ":0" dpms force on
```
turns my screen on, but leaves it blank.

I would recommend you install the mailx package:
```
sudo apt-get install mailx
```
If you do that, then cron will send you email (to your local system mailbox) with any output or error messages from any command it tries to run for you. You can check your mail using the command:
```
mail
```

---

### Post by provide on 2009-03-03
Success, heindsight! It worked. Thank you so much! I just tried it out in a one minute interval. The screen blanked out and a minute later came back. Thanks again!

Thank you for your response as well, rjmoerland.

---


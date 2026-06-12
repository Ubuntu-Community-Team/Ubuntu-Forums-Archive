---
title: "Screen turns off after 5 minutes"
date: 2008-02-02
forum: Desktop Effects &amp; Customization
---

### Post by GodJunker on 2008-02-02
I'm having a problem with my screen turning off after 5 minutes or so. It only started happening since i installed Compiz-Fusion. My power settings have my screen set to never go off. This never happened before i installed compiz-fusion so i'm thinking it has something to do with it. I've got a screensaver set to come on after 45 minutes, but even when its off the screen still goes off after about 5 minutes of inactivity. 

Computer is a HP Pavilion ZV6100, with an AMD64 3200 and ATI Radeon Xpress 200M
OS is Ubuntu Gutsy.

I've only been using Ubuntu about 3 weeks, so keep it as simple as possible.

Thanks.

EDIT: Also i get a blank screen after booting but before the log-on screen that lasts 3 minutes or so. Been going on since i first used Ubuntu...is this normal?

---

### Post by GodJunker on 2008-02-03
Bumping this...still havent figured it out.

---

### Post by voodoowizard on 2008-02-04
Having the same problem also. It will interrupt videos being played and the screen will just go black, similar to a blank screensaver. This all started last night after I got my desktop effects going, Installed emerald theme manager and installed advanced desktop effects setting, Also I installed something else maybe xserver-xgl ? cant remember I installed the last because when i tried to use effect it said missing something.

Originally had an ati now have a gforce 6800. Might have affected what was originally installed.

I guess I turn every thing off and "effects wise" and see if it still does it.

---

### Post by voodoowizard on 2008-02-05
found out a possible fix: [http://ubuntuforums.org/showthread.php?t=341617](http://ubuntuforums.org/showthread.php?t=341617)

taken from : [http://tnlessone.wordpress.com/category/beryl/](http://tnlessone.wordpress.com/category/beryl/)   
In fact the problem appears when you run beryl with Xgl as a session on display :1. You’ll need to edit /etc/X11/xorg.conf and add at the end :

# To prevent Blank Screen from popping up every 10 minutes
# when xgl is run as a session on display :1,
# when all the power management settings
# you normally find only concerns display :0
Section “ServerFlags”
Option “blank time” “0&#8243;
Option “standby time” “0&#8243;
Option “suspend time” “0&#8243;
Option “off time” “0&#8243;
EndSection

---

### Post by voodoowizard on 2008-02-05
Ehh did not work for me. Just caused temporary problems.

---

### Post by GodJunker on 2008-02-06
Thanks...Sucks it didn't work for you. It messed me up at first, so I had to boot in recovery mode and fix the xorg.conf. Had some symbols around the text in place of the quotation marks. Changed em back to quotes and booted up normally.....No more blanking out after five minutes.

---

### Post by voodoowizard on 2008-02-16
After going back through everything it did work. Have to retype the quotes.

---

### Post by mattstakilla on 2008-02-21
> **voodoowizard said:**
> After going back through everything it did work. Have to retype the quotes.

I have been having this problem also, I will give it a try when I get home.

---

### Post by Kivech on 2008-03-03
Excellent fix!

It's true though that the quotation marks are in the wrong format. So the end result should look like this:

[PHP]# To prevent Blank Screen from popping up every 10 minutes
# when xgl is run as a session on display :1,
# when all the power management settings
# you normally find only concerns display :0
Section "ServerFlags"
	Option "blank time" "0"
	Option "standby time" "0"
	Option "suspend time" "0"
	Option "off time" "0"
EndSection[/PHP]

It's also properly aligned this way, so it looks a bit more neat from a programming perspective.

Cheers!

Kivech

---

### Post by erginemr on 2008-03-03
Agreed it is a great fix, but I believe you disable the suspend capability of the laptop altogether this way as a side effect.

---


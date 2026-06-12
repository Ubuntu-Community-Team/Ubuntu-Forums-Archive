---
title: "rollback to default fonts?"
date: 2008-01-23
forum: Desktop Effects &amp; Customization
---

### Post by aflog on 2008-01-23
So i installed this font thingy [here]("http://ubuntuforums.org/showthread.php?t=208396")... however it had some undesired effects! For some weird reson it has affected the system default fonts and they have completely changed. Example: Sans looks really grainy where before it wasnt. I also HAD msttcorefonts installed but removed them...

So what i want to know, is there a way to wipe all the changes made by these changes and go back to the default way the fonts were? Its not vital, but ive had to change all my default fonts because they all look different...

Thanks!
(no rush btw)

Jayden

---

### Post by erginemr on 2008-01-23
I have read that page and it seems you can restore your settings if you undo all those changes to your system. The page you refer to says:
```
sudo apt-get install msttcorefonts
```
which you already uninstalled. That was Step-1.

Step-2 is:
```
sudo tar xvjpf fontconfig.tbz -C /etc/fonts/
```

I have downloaded the file in question and saw that it includes the following 4 files:
alias.conf, msfonts-rules.conf, local.conf, misc.conf
all to be extracted into /etc/fonts/

Given the fact that Linux is all about text-only config files and does not deal with human-unreadable registry files as does Windows, and taking a peek into my attached /etc/fonts folder, I would just delete those 4 files from /etc/fonts:
```
sudo rm alias.conf msfonts-rules.conf local.conf misc.conf
```

Finally, you need to set back your fonts to the attached default ones by following:
Main Menu -> System -> Appearance -> Fonts Tab
and playing with antialiasing and other appearance-related settings there.

---

### Post by aflog on 2008-01-23
> Main Menu -> System -> Appearance -> Fonts Tab
That option doesnt exist in Xubuntu... the closest i have is the User Interface dialog... i can attach a screenie if you want...

---

### Post by erginemr on 2008-01-23
Shoot!.. I didn't notice your signature, wherein says Xubuntu, sorry...

However, there should be some tool in Xubuntu to manipulate the fonts. Does deleting the 4 config files and rebooting make any difference?

---

### Post by aflog on 2008-01-23
Dunno havent rebooted yet... ill give it a try now and get back to ya in a minute or two...

---

### Post by aflog on 2008-01-23
...or 15 :D

Ok well i rebooted, it looks much different... but now i have no idea what the default font was :S Any idea? (btw the windows fonts are still present but the Xubuntu originals seem to be restored to their original looks)

Thx

Jayden

---

### Post by erginemr on 2008-01-23
I believe the tool in question is  "xfce-mcs-manager" or "xfce-setting-show", whichever works. So, if you run it from "Run..." dialog (maybe with Alt+F2), or from the console, a tool should show up, allowing you to change the screen font.

---

### Post by aflog on 2008-01-23
Yes thanks... i found that :D
It seems to be ok, so im happy

Thanks for your help!

Jayden

---

### Post by erginemr on 2008-01-23
You are welcome. 

Take Care & Have Fun!

---


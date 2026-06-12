---
title: "Unreadable menu"
date: 2012-12-26
forum: Desktop Environments
---

### Post by tzeronone on 2012-12-26
Anyone know what happens to my ubuntu?

---

### Post by orb9220 on 2012-12-26
Not your Ubuntu but fonts selected for Firefox.
Check Preferences>Content Tab> 
Check default for Fonts&Colors. Also click on Advanced and check what fonts are being used as defaults.

As suspect using some symbol or uncommon font selections. Change them to more common fonts used.
.

---

### Post by tzeronone on 2012-12-26
It's not Firefox. My firefox has no problem...

---

### Post by Frogs Hair on 2012-12-27
Does this happen with all themes ?

---

### Post by iMac71 on 2012-12-27
Ubuntu Tweak might help you.
You can get it as follows:

[LIST]
[*]open a Terminal window and type:
[/LIST]
```
sudo apt-add-repository -y ppa: tualatrix/ppa
sudo apt-get update -y
sudo apt-get install -y ubuntu-tweak
```[INDENT](you have to press [ENTER] after you've typed each line).
[/INDENT]
[LIST]
[*]when you've installed it, close the Terminal window, press [ALT]+[F2] to open the HUD and type "ubuntu-tweak" without quotes;
[*]click on the "Tweaks" tab, then on the "Fonts" icon;
[*]near to each font category there's the icon of a curved arrow: click on each of these icons; this should solve your problem, since it restores the default font.
[/LIST]

---

### Post by tzeronone on 2013-01-01
@iMac71, I can't run the first line with error: "apt-add-repository: error: no such option: -y"

---

### Post by BlinkinCat on 2013-01-01
Hi,

It is quite possible that I am incorrect but it appears to me that there is a space before the -y in each of those three commands.
It is often better to copy and paste the commands into the terminal.

As for whether the commands are correct or not I just can't say - my knowledge is limited.

Cheers - :p

---


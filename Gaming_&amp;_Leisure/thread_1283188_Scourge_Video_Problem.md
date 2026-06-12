---
title: "Scourge Video Problem"
date: 2009-10-05
forum: Gaming &amp; Leisure
---

### Post by Stosskraft on 2009-10-05
Hello,

I installed "Scourge" RPG game from playdeb. However I reset the resolution and then the game would not open. Meaning, when I tired to start it, The screen goes black and then back to the desktop. I cannot get into the game to change the settings back.

I tried to remove it from the terminal and re-install it but I am having the same problem.

Here is what the terminal is saying:

> yanek@yanek-desktop:~$ scourge
Constructing root path:
	not using binreloc...
	temp rootDir=/usr/share/games/scourge
*** Can't find local version of data dir. You're running a distribution.
Looking for localized resources in: /usr/share/games/scourge/translations
Starting session. Final rootDir=/usr/share/games/scourge
Setting video mode: 1280x1024x32
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0xa2
  Serial number of failed request:  125
  Current serial number in output stream:  127

Any ideas how to fix this?

Thank you

---

### Post by myromance123 on 2009-10-05
What kind of monitor are you using?

 I could be wrong but it looks like you set the value to something the monitor can't handle.. but I could be wrong.

---

### Post by Stosskraft on 2009-10-05
I have a 21in HP 2009f.

I am sure I did what you said, as I changed the resolution and then it wouldn't start.

I have even un-installed it and then installed again, but same result.

I am wondering if there is a why to change the settings for the game in the terminal? 

I tried both these commands separately in the terminal:

sudo apt-get delete scourge
sudo apt-get purge scourge and then re-installed but its crashing on start, thought it did work fine the first time.

---

### Post by Stosskraft on 2009-10-11
*bump*

---


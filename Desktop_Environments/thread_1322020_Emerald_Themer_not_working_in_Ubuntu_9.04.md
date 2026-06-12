---
title: "Emerald Themer not working in Ubuntu 9.04?"
date: 2009-11-10
forum: Desktop Environments
---

### Post by Nightstrike2009 on 2009-11-10
Hiya Everyone,

I have got the .deb files below installed;

[COLOR="DarkGreen"]emerald_0.7.2-0ubuntu2_i386
libemeraldengine0_0.7.2-0ubuntu2_i386[/COLOR]

Emerald themer appears on top panel and detects themes but doesn't let me apply them, which files if any am I Missing?

Please Help

PS I have My ATI 3D Driver enabled, and compiz-config-manager installed.

---

### Post by Nightstrike2009 on 2009-11-10
Heard this maybe solution:

> Then, in your compiz settings, put emerald as your window decorator. You can then install the themes using the emerald theme manager.

How do I do this?

---

### Post by Nightstrike2009 on 2009-11-10
Got it, Select Theme in System>Preferences>Emerald Theme Manager>

Hold Alt + F2 Keys

Type:
emerald --replace

Click Run

Then it works is there a way to place emerald --replace in my start=up file so i don't have to keep typing it?

---

### Post by Nightstrike2009 on 2009-11-10
I Like this suggested by Bajun:

> Or better change following line in /usr/bin/compiz-decorator:
Code:

USE_EMERALD="no"

and set this to
Code:

USE_EMERALD="yes"

,
then there are fallback options, for example "Do not leave users without decoration if decorator fails".

It will not let me save as protected what is the way around this?

---

### Post by Nightstrike2009 on 2009-11-10
Got it now to set Emerald as default:

How to make Emerald default

Hold Alt + F2 keys down

Code:

gksudo gedit /usr/bin/compiz-decorator

Enter password, then alter line that says

# Default to gtk/kde(4)-window-decorator
#
USE_EMERALD="no"

and set it to
Code:

USE_EMERALD="yes"

Then, Save.

Thats It! Enjoy :)

PS Thanks to Bajun who told me how to alter start-up, pity everyone else left it to me to sort out :(

---


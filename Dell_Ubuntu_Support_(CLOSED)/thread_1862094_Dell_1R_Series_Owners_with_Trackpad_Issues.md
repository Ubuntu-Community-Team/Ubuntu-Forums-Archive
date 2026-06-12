---
title: "Dell 1*R Series Owners with Trackpad Issues"
date: 2011-10-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bobsageek on 2011-10-16
I have a recent Dell 17R (N7110) that features a newer Alps trackpad, and like many people have seen, 11.10 (and of course 11.04 and earlier), system prefs shows it as a mouse and not a trackpad and it will drive you nuts while you are typing. I read several dozen topics yesterday and had no luck, and the current version of touchpad-indicator is not (yet) working with 11.10.

So while perusing launchpad bug reports I found a patch from Seth Forshee and salvation is at hand. Not only does the device now show up as a trackpad but the FN-F3 combo disables and enables the device. 

[Find the patch here!]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/comments/492")

Should work for you if you xinput -list looks like this...

```
xxxxxx@torchwood:~$ xinput -list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=12	[slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                         	id=14	[slave  pointer  (2)]
&#9116;   [COLOR="Red"]&#8627; AlpsPS/2 ALPS DualPoint TouchPad[/COLOR]        	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]

```

---


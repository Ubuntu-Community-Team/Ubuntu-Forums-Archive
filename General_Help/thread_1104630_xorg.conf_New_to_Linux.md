---
title: "xorg.conf? New to Linux"
date: 2009-03-23
forum: General Help
---

### Post by dcretin on 2009-03-23
Ok, I'm extremely new to linux but learning quickly. Anyway the situation is as follows; Trying to do my part in getting a game to work using Wine (a game called Runes of Magic FYI) and someone who is helping me with a bug I've encountered asked me the following question. 

"Do you have all required resolutions configured in xorg.conf? Verify with
running 'xrandr'. It should list all available modes."

I have no idea what that sentence means. :) What is he asking? and how do I find the answer? I ran xrandr from the terminal and it listed a bunch of resolutions, but I'm stumped as to the xorg.conf.

The whole bug report with comments is here.
[http://bugs.winehq.org/show_bug.cgi?id=17818](http://bugs.winehq.org/show_bug.cgi?id=17818)

Any help would be greatly appriciated.

-Daniel

---

### Post by Xiong Chiamiov on 2009-03-23
xorg.conf is located at /etc/X11/xorg.conf.  You're looking for something like
```

    SubSection "Display"
        Depth        16
        Modes      "1024x768"
    EndSubSection

```
with indicates that X is supposed to be able to use the resolution 1024x768.

---

### Post by dcretin on 2009-03-23
Thanks for the help, looked at my xorg.conf and nothing really similar to what you posted, in fact it's rather short.

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Which leads me to think that maybe that person was onto something to ask me about it.

---


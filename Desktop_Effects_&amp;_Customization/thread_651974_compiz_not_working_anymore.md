---
title: "compiz not working anymore"
date: 2007-12-28
forum: Desktop Effects &amp; Customization
---

### Post by napsy on 2007-12-28
Hello.

I have a Fujitsu-Siemens AMILO Pi2515 laptop. When I had ubuntu 7.04 compiz worked like a charm with no problems. Now I've upgraded to gutsy. The card is still correctly installed  (Intel GMA X3100 with the intel xorg driver) and opengl and composite module works:

~$ glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
...

But now compiz doesn't seem to work. When I try to start compiz manually I get this error:
$ compiz --replace
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity

What's wrong and how can I fix this? Please help.

Greets,
Luka

---

### Post by Forlong on 2007-12-28
> **napsy said:**
> What's wrong and how can I fix this?
Your graphics chip has been blacklisted, because there may be troubles using it with Compiz.

Try running Compiz like this:
```
SKIP_CHECKS=yes compiz
```

Let me know if it worked.

---

### Post by napsy on 2007-12-28
It worked!
Thanks.

Is there a list of blacklisted chips and a reason why they've been blacklisted?

---

### Post by anubhavrocks on 2007-12-28
[HTML]http://ubuntuforums.org/showthread.php?t=612617[/HTML]

---

### Post by Forlong on 2007-12-28
> **napsy said:**
> It worked!
Great, now do this:
```
gedit ~/.config/compiz/compiz-manager
```
Put this in there:
```
SKIP_CHECKS=yes
```
And save.

Then you don't have to run that command yourself anymore.

Edit: [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

---

### Post by hasher on 2008-01-09
And then change  from xv to xgl so that video playback is enabled

Enable Video Playback 

From your terminal run the following command: 
gstreamer-properties

Click the Video tab. Change the Default Output Plugin: value to "X Window System (No Xv)".

check : [http://knowledge76.com/index.php/GutsyCompizIntelX3100](http://knowledge76.com/index.php/GutsyCompizIntelX3100)

---


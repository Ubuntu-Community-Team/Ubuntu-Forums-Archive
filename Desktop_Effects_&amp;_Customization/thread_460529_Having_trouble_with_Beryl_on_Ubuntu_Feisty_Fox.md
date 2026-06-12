---
title: "Having trouble with Beryl on Ubuntu Feisty Fox"
date: 2007-05-31
forum: Desktop Effects &amp; Customization
---

### Post by 213374U on 2007-05-31
Okay, I've gotten everything installed and all went well. But when I try to use Beryl, it seems as though nothing has happened. I try to apply Emerald Themes, they don't work. Try to get the Cube desktop to work, can't. I've followed several walk-throughs I've found on the intraweb, and the one part that I come to and can't complete is activating Desktop Effects. When I go to System -> Preferences -> Desktop Effects ,to activate them, I get an error message reading:

The Composite extension is not available.

What's the deal and what am I missing here to get this thing running?

---

### Post by dacookiemonn on 2007-05-31
try entering the command [COLOR="Red"]beryl[/COLOR] in the terminal.
Im trying to get it to auto start, but noit having any luck.  Let me know if this works for you.

---

### Post by 213374U on 2007-05-31
Typing "beryl" in the terminal does nothing. Typing either "beryl-settings" or "beryl-manager" pulls up the settings or manager windows... try that.

---

### Post by Kuranes on 2007-05-31
I'm having the very same problems, even with the desktop effects manager. I might add I'm using an ATI x1650, and get bad results on a prompt according to [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_ATI)

 Well. Could you please specify your graphics card? Maybe we can solve this together.

---

### Post by 213374U on 2007-05-31
It's an ATI Radeon X1600 Pro

---

### Post by 213374U on 2007-05-31
The link you provided above is how I installed mine. I used other guides across the internet to try and get it up and running but no luck

---

### Post by Kuranes on 2007-05-31
Quite cool coincidence, same cards, same problems, same forum, same time. Anyway. Are you getting the right results when doing as described in the link? Cause I am not. 

I just shot one version of Ubuntu with the wrong graphic drivers, btw. Seems like it's going to be a fun night.

cheers

---

### Post by Kuranes on 2007-05-31
Seems like the ATI x1600 pro is generally inclined to make trouble on Ubuntu, I found several threads about it. Have a look at this, the second to last post: [http://ubuntuforums.org/showthread.php?t=422319](http://ubuntuforums.org/showthread.php?t=422319)

I'm currently working on that.

---

### Post by Kuranes on 2007-06-01
I got it. Solved the problem. I havent got the time or the nerve to document it atm, however; if somebody really wants to know, post it.

---

### Post by 213374U on 2007-06-01
It's ALIVE!!!1111!!11!!! Finally got it working after following several links. Gotta get back to work but if anyone wants the links, let me know.

---

### Post by linuxswords on 2007-06-02
Yes, I'd like to know hot to do it.

I have a Radeon 9600 and got the same error message:
```

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
```

But when I add 
```

Section "Extensions"
        Option      "Composite" "Disable"
EndSection
```

to my /etc/X11/xorg.conf it disables DRI... Was it the same for you both??

---


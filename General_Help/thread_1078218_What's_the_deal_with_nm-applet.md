---
title: "What's the deal with nm-applet?"
date: 2009-02-23
forum: General Help
---

### Post by detroit/zero on 2009-02-23
My nm-applet is all stupid. It's constantly giving me readings and signal strengths that simply can't be true. Networks appear and disappear from the list of available APs even though the computer doesn't move, and a network that is barely available will show a full signal bar while my own router in the next room says 64% strength.

Is there a network manager applet with similar functionality to the default nm-applet found in hardy that provides more reliable readings?

---

### Post by binbash on 2009-02-23
wicd or sudo iwlist scan : )

---

### Post by detroit/zero on 2009-02-23
OK... wicd looks promising, as long as it's more accurate than nm-applet.

Anybody know of any others?

---

### Post by 3rdalbum on 2009-02-23
Network Manager (nm-applet) tends to just use whatever data is being given to it by the driver. It's possible that there is a regression in the driver that is causing strange signal strength readings.

If the command "sudo iwlist scan" also shows 60-odd percent signal strength or signal quality, then you'll know it's a driver issue.

---

### Post by mb_webguy on 2009-02-23
Wow, thanks for the suggestion of wicd, binbash.  I'd dropped in to see if I could help, and ended up getting help for a problem I didn't know I had!

The Network Manager applet has been pretty slow recently, especially in initially connecting to my router after a logout or reboot.  I didn't think much about it, considering I'm using a pre-n card that was temperamental in Vista and by all rights shouldn't run in Linux at all, even with ndiswrapper.

But I tried wicd on a lark based on your recommendation, and it connected almost instantly, where nm-applet has been taking a few minutes!  The interface will take some getting used to but otherwise, I'm certainly sticking with wicd.

---

### Post by detroit/zero on 2009-02-23
> **3rdalbum said:**
> Network Manager (nm-applet) tends to just use whatever data is being given to it by the driver. It's possible that there is a regression in the driver that is causing strange signal strength readings.

If the command "sudo iwlist scan" also shows 60-odd percent signal strength or signal quality, then you'll know it's a driver issue.
I knew about the *iwlist scan* command, but never thought to compare the two - I figured one got its info from the other or vice versa or whatever.

Turns out iwlist is giving me a third value that's different than nm-applet's value, different than what I get when I'm running inside backtrack linux (on madwifi drivers), and different than what I get inside either my Vista or XP installs. nm-applet will show, for example, three-quarters of a bar of signal stregth (so let's call it 75%...) while iwlist scan says 46/70 (which figures to about 65%), but inside backtrack I see close to 100%.

I wonder if I should switch to madwifi drivers for wireless in Ubuntu?

I don't know, though.. I mean my wifi does work, and everything.. I'd just rather get more reliable info from the applet.

Gah! Why can't I just stop tinkering with this computer and just use it??

---


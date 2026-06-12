---
title: "Broke unity and HUD with Compiz on 12.04"
date: 2012-04-29
forum: Desktop Environments
---

### Post by kkrishnan on 2012-04-29
Hi folks

I just installed Ubuntu 12.04, and I was trying to create a terminal embedded in my desktop following instructions for Ubuntu 11.10 from here - [http://maketecheasier.com/terminal-as-transparent-wallpaper-in-ubuntu/2008/05/21](http://maketecheasier.com/terminal-as-transparent-wallpaper-in-ubuntu/2008/05/21)

Needless to say, the steps didn't work and the HUD immediately started behaving funny. So in an ill conceived act of desperation, I did ```
sudo apt-get remove compizconfig-settings-manager
``` and restarted my machine. Now, Unity and HUD have disappeared all together. I no longer have the left hand side menu bar, the top menu, or access to HUD or even Alt-F2 type stuff. In fact, even Alt-Tab does not work now.

I've attached a screenshot to give you a sense of what my desktop looks like now. Is there any way I can revert to the default settings that Ubuntu 12.04 came with (which worked fine)? Luckily, gnome-terminal is on my list of startup applications, so I still have access to a terminal window.

Any help is appreciated.

Thanks

---

### Post by goldshirt9 on 2012-04-29
[http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)
beware of the command though, read the warning

---

### Post by stinkeye on 2012-04-29
Sometimes when changing settings in ccsm, compiz doesn't reload properly
and you just need to reload with(in terminal)
```
compiz --replace & disown
```

If that doesn't work, set compiz back to defaults...
```
unity --reset & disown
```

PS: Removing compizconfig-settings-manager won't affect anything except your ability to configure compiz.

---

### Post by kkrishnan on 2012-04-29
Perfect. I think that did it! Thanks very much.

---

### Post by nipunshakya on 2012-07-02
> **kkrishnan said:**
> Perfect. I think that did it! Thanks very much.

Would you tell me what worked for you? the first suggestion by goldshirt or the last thread by stinkeye ??? Im having the same problem located at following thread too...

[http://ubuntuforums.org/showthread.php?t=2014641](http://ubuntuforums.org/showthread.php?t=2014641)

---


---
title: "Can not see the whole screen on laptop (after installation)"
date: 2015-07-17
forum: Desktop Environments
---

### Post by zmau1962 on 2015-07-17
[COLOR=#111111][FONT=Ubuntu]Just installed Ubuntu 14.04 on an HP laptop
I can not see the whole screen, because the resolution is too Low.
On the other hand, I can not change screen resolution because I can not see the whole screen (so, it' like catch 22)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any advice ?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks

[/FONT][/COLOR]

---

### Post by grahammechanical on 2015-07-17
Tap the super (windows) key to reveal the Dash and search for additional drivers. That will open System Settings>Software & Updates>Additional Drivers tab and select another video driver to use. 

You will need to reboot, so open the terminal - again search for it in the Dash or Cntl+Alt+T and type

```
sudo shutdown -r now
```

to shutdown the command would be

```
sudo shutdown -h now
```

Also, if you are already using a proprietary video driver then there will be a proprietary settings manager for it. Search for it in the Dash. It will have a Detect Displays option.

If we search the Dash for screen, then we can load Screen Displays which is the settings utility for open source video drivers. It also has a Detect Displays option.

Regards.

---

### Post by v3.xx on 2015-07-17
You can also try recovery mode.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=recovery+mode&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=recovery+mode&sa=Search&cof=FORID:9)

---

### Post by zmau1962 on 2015-07-17
Hi all,


Amazingly, the problem was solved simply by reboot....  


Thanks

---

### Post by v3.xx on 2015-07-17
> **zmau1962 said:**
> Hi all,


Amazingly, the problem was solved simply by reboot....  


Thanks
And I got my morning smile out of this.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


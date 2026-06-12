---
title: "Settings daemon hotplug command no longer working - what'm I doing wrong?"
date: 2013-12-08
forum: Desktop Environments
---

### Post by Copper Bezel on 2013-12-08
Hey all. Does this dconf key no longer function?

[[IMG]https://dl.dropboxusercontent.com/u/17749392/Image%20Hosting/Discussion%20Boards/UF/Threads/2013-12-08/Screenshot%20from%202013-12-08%2011%3A05%3A44t.png[/IMG]]("https://dl.dropboxusercontent.com/u/17749392/Image%20Hosting/Discussion%20Boards/UF/Threads/2013-12-08/Screenshot%20from%202013-12-08%2011%3A05%3A44.png")

I have a script that sets my setxkbmap and miscellaneous input tweaks on login and resume. It's stopped working since the upgrade to 13.10. Do I need to put this somewhere else now? I really appreciated having a simple, intended place to keep the trigger for this script, and I don't want to have to do some awkward-*** workaround with cron. Crazy thing is, I know it's getting triggered, because it's responsible for my natural scrolling settings (the xinput lines), but the xkbmap and synclient settings aren't sticking when I resume from suspend. 

```
#!/bin/bash
synclient ClickFinger1=1
synclient TapButton1=1
synclient ClickFinger2=3
synclient TapButton2=3
synclient ClickFinger3=0
synclient TapButton3=0
synclient HorizTwoFingerScroll=1
synclient VertTwoFingerScroll=1
synclient VertEdgeScroll
synclient ClickPad=0 
xinput set-prop 12 297 -74 -74
xinput set-prop 13 297 -74 -74
xinput set-prop 14 300 -74 -74
xmodmap -e "keycode 248 = VoidSymbol"
setxkbmap -option caps:backspace
setxkbmap -option terminate:ctrl_alt_bkspc
```

Is all. 

- Copper

Edit: Correction: only natural scrolling engages on cold boot (which means the script is run but preempted somewhere.) xkbmap settings persist over suspend (or are engaged *on *suspend - but I think they're just persistent) while synclient settings are lost every time I close the lid.

---

### Post by Copper Bezel on 2013-12-09
Bump with a better question: If not the hotplug command, how do *you *all manage peripheral configuration? All the GUIs are insufficient, and they're still *removing* features! (Not a complaint, exactly - the GUIs need to be simple, but I want my hacks to stick.)

---


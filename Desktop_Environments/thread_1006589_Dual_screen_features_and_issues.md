---
title: "Dual screen features and issues"
date: 2008-12-09
forum: Desktop Environments
---

### Post by sturreal on 2008-12-09
I have some ideas for Dual screen improvements in Gnome/X I'm not sure where to write this so I thought I'd see what people think of my ideas, my short background rant follows ;)

I've recently and to be honest with no success been trying to play some games through wine in fact I've even tried native games too, all failed miserably (That's why we have windows in dual boot right?). The one thing that's been annoying more than games not working (I know why this is, its the experimental 3D support for my RadeonX1900), is what happens to my desktop as a result of the crashed game:

[LIST=1]
[*]Secondary screen is disabled when the games full screen on screen 1 and when the game crashes screens isn't enabled again. I have to say I like the fact the second screen is disabled, but not that fact I have to go and restore it to working order again. :mad:
[*]The screen resolution never reverts to its original state and I have to kill X to get the resolution back and the secondary screen working again. If I just simply enable it via Preferences->screen resolution I find the second screen doesn't function properly i.e. it displays what it should it just never refreshes, its like the secondary screen hard locks. This might be down to compiz as I can still rotate my whole desktop on a cube and that animates just fine, however none of the applications windows update. 
[*]The Gnome panels on the second screen get pushed onto the primary screen, which I'm sure is a feature (an ill advised one at that)
[/LIST]

Now I class point 1 & 2 as basic OS functionality, things I expect to be working (by the way to get dual screen I have to edit the X config which is out of order, in this day and age I guess Xrandr still doesn't as yet get the idea that some people have two screens and we don't just want cloned output! this could be drivers issues too though as my 2x19" dell screens are reported to have a maximum resolution of 1600x1024 which is completely wrong.) I guess this will be improved over time as driver support improves, but as long as I get driver updates in the interim and don't have to wait for the next version of Ubuntu to get them.

Point 3 firstly let me say I love the fact I can have a panel on each screen and stick a window selector applet on it which shows the apps on each screen for example I have Openoffice open on screen 1 and Firefox say on screen 2 and they are in each screens respective windows selector. (M$ could do with learning a thing or two here, I shouldn't need to buy Ultramon to get that functionality for example.) I also love the fact that when I do something on say screen 2 all the dialogue boxes appear on the screen I'm working on (that's just awesome)

Now the panels being pushed from screen 2 to screen 1 and being stacked is a problem and here's how I reckon it could be fixed. Either you have 1 panel and you have an option to span screens and gnome detects the number of screens in use and just simply stretches them across the active screens so when one is disabled it doesn't mess up you desktop when you disable a screen it just simply scales, it would need to work out which part of it was on which screen so that the windows selector works as it currently does. 

The other idea is you could simply just disable the panels on the screen which has been disabled and enable them again when the disabled screen becomes active again, however if you have your clock on say screen2 as I do and then disable screen 2 then I'd loose my clock so perhaps this isn't the best way after all but its an idea.

I'd love to hear other peoples ideas / experiences with dual screen support in Ubuntu.

---

### Post by sturreal on 2008-12-09
sorry for double post for some reason I kept getting server errors

---


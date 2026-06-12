---
title: "Remove unnecessary lefthand taskbar in Unity"
date: 2011-05-03
forum: Desktop Environments
---

### Post by satanselbow on 2011-05-03
I have taken the largest chill pill I could find and have reinstalled nutty into a spare partition with a view to taking a more forgiving approach... i'll mostly stand by the rants for the time being... ;)

Has anyone found a simple (or complex for that matter - I just want it gone!) way to disable the randomly activated lefthand vertical taskbar in unity?

It really is an unnecessary irritation when I can put my essential apps down the bottom where they belong with docky (thus reducing mouse mileage on my widescreen) and have everything else a WinKey+App away.

Interesting that typing "Configuration" into the search box returns 0 results on a default natty install :P

**** Additional ****

Tweaking the Unity Plugin through Advanced Compiz Manager (and gconf-editor) leads me believe that I am after a "feature" that is not available:

in gconf-editor:

/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode

is the key I would like to have an additional option of "Always" added :( the currently available options being "0 = Never, 1 = Autohide, 2 = Dodge Windows, 3 = Dodge Active Window"

I can feel an unfeature request coming on ;)

---

### Post by mc4man on 2011-05-03
simple - at login choose "Classic"

---

### Post by satanselbow on 2011-05-03
Ahhh - but I want the dash but not the launcher - classic would kill them both. 

It is superfluous to my needs and does just get in the way regardless of current level of hiding :( Fortunately the Alt+L keyboard shortcut is still in place for firefox as moving the mouse too rapidly towards the browser back button causes the "Tower Of Pointlessness" to appear and get in the way.

I am trying hard to to have some love for nutty but sometimes it is the little things that irk the most :confused:

---

### Post by keithmcneill on 2011-05-03
Related to this issue, I have a problem with Unity. On tabbed applications, e.g. Firefox, I now cannot drag a tab all the way to the left, as the launcher appears and stops me dropping the tab. I don't mind the launcher, but this is the kind of minor annoyance that could put some people off. 
 Is there somewhere I could report this as a 'bug'? Thanks

---

### Post by ankspo71 on 2011-05-03
> **keithmcneill said:**
> Related to this issue, I have a problem with Unity. On tabbed applications, e.g. Firefox, I now cannot drag a tab all the way to the left, as the launcher appears and stops me dropping the tab. I don't mind the launcher, but this is the kind of minor annoyance that could put some people off. 
 Is there somewhere I could report this as a 'bug'? Thanks

Hi,
Here are some bugs that describe what your saying:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/728841](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/728841)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/758353](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/758353)

If you create an account at launchpad you will be able comment on bug reports, or be able to create your own. [https://launchpad.net/](https://launchpad.net/)

Here is Ubuntu's own page:
[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

To create your own bug report, you can open up your terminal and use the following command:
```
ubuntu-bug packagename
```
Replace packagename with the name of the package (or application) you would like to report.

More info:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by satanselbow on 2011-05-03
Cheers ankspo71,

I'll be doing just that :popcorn:

---

### Post by stinkeye on 2011-05-03
In ccsm > ubuntu unity plugin 
Change the reveal mode to top left.
This also allows you to use the firefox side bar switch when unity launcher is hidden.

---

### Post by satanselbow on 2011-05-03
And thank you StinkEye.

Done that one already but still find it (the launcher) makes an unwelcome appearance - I must have a particularly vicious mouse flourish :D

Hey - the tweak tools will come in time; official or ney... probably ney ;)

Thanks for the input Stink - restricting the hit zone does indeed dull the annoyance down a notch :popcorn:

---

### Post by stinkeye on 2011-05-03
When I do it the launcher appears but then disappears after a little bit when I drag the tab to the left if reveal mode is top left.

---

### Post by bowens44 on 2011-05-03
> **mc4man said:**
> simple - at login choose "Classic"

Not that simple. For many of us "classic" is broken. It's very unstable.

---

### Post by mc4man on 2011-05-03
> **satanselbow said:**
> And thank you StinkEye.

Done that one already but still find it (the launcher) makes an unwelcome appearance - I must have a particularly vicious mouse flourish 
That may be from the drag & drop into launcher feature which unhides the launcher when grabbing and moving objects

At times I find it an annoyance or worse, appears to be coded in with no config possible to enable/disable

---


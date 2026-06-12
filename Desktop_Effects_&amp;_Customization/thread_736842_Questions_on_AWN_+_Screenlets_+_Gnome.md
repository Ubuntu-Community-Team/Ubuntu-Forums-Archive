---
title: "Questions on AWN + Screenlets + Gnome"
date: 2008-03-27
forum: Desktop Effects &amp; Customization
---

### Post by werg on 2008-03-27
Hi, 

I have a few questions regarding AWN, Screenlets and Gnome.

AWN: How to prevent AWN (dock) showing opened applications? I just want to use it for my launchers, not for task management.

Screenlets: Is there anyway to make Screenlets stay on the Desktop, even when I click on 'Show Desktop'? Using Devil's Pie, maybe... but I am not aware of a Devil's Pie command which prevents this.

Gnome: Is there an option somewhere to make a panel appear below all windows?

Thanks.

---

### Post by rune0077 on 2008-03-27
Hi.

Regarding the screenlets, try right-clicking the screenlet, then go to Window and select "Widget". I think that should help.

---

### Post by werg on 2008-03-27
Thanks for the answer. I tried what you suggested but it didn't work... strangely enough, though, when I check then uncheck 'widget layer' in the CompizConfig Settings Manager, I get exactly what I want.. until next log off or reboot.

---

### Post by rune0077 on 2008-03-28
> **werg said:**
> Thanks for the answer. I tried what you suggested but it didn't work... strangely enough, though, when I check then uncheck 'widget layer' in the CompizConfig Settings Manager, I get exactly what I want.. until next log off or reboot.

This is weird. I have my screenlets set as widgets and they don't go away when I issue the show desktop command. I know that wasn't much help to you, but I'll try to fiddle around with the settings later today, then come back to you (just a thought, are your screenlets also set to "Sticky" - mine are, that may be what's doing it).

---

### Post by werg on 2008-03-28
Thanks. I've set them to sticky, but no change...

About the other questions, anyone's got an idea?

---

### Post by moonbeam on 2008-03-28
> **werg said:**
> Hi, 

I have a few questions regarding AWN, Screenlets and Gnome.

AWN: How to prevent AWN (dock) showing opened applications? I just want to use it for my launchers, not for task management.

Thanks.

1) Install from the awn testing PPA   [https://launchpad.net/~awn-testing/+archive](https://launchpad.net/~awn-testing/+archive)

2) Remove the Launcher/taskmanager applet.  (chances are awn will crash when you do this)

3) Restart AWN.

4) Add simple-launcher applets.  One per launcher that you would like to use.  Do not use standalone-launcher (that's designed to support tasks management).

5) Drag and drop the desktop files you want to use into the simple-launchers in question.

6) Done.

---

### Post by werg on 2008-03-29
Many thanks moonbeam. rune0077, anything yet?

---

### Post by rune0077 on 2008-03-29
> **werg said:**
> Many thanks moonbeam. rune0077, anything yet?

Hey, sorry for the wait. I have been unable to replicate your situation. One thing I noted, was that I had actually not set my screenlets as Widgets, instead under the Widget > Behaviour I have set "Widget Windows" to screenlets", which treats all screenlets as widgets.

---

### Post by werg on 2008-03-29
Hummm, thanks anyway.

---

### Post by apothecaryaaron on 2008-03-30
When I set my Screenlets as "Widgets", it allows me to use the keybinding in Compiz Widget Layer to show them.  My keybinding was F9 by default.  It sort of works the opposite of what you were going for, instead of moving windows and showing the screenlets, it just moves the screenlets on top of the windows.
 
I place a double of each screenlet, one as sticky, one as widget in the same spot when I am showing off Ubuntu for my friends.  This way the screenlets show all the time on the desktop and come up by keystroke as well.  My friends don't need to know it's actually two copies.....

---

### Post by werg on 2008-03-30
I think I found to make this work. First, set the screenlets to **widget**, and then, in the **CompizConfig Setting Manager**, enable** Widget Layer** then under the Widget Layer options, in the** Appearance** tab, set both **Background Saturation** and **Background Brightness** to 100. Then in the** Behaviour** tab make sure that 'End Widget Mode on Click' is unticked. This should give the desired result whenever pressing F9. 

Now, is there a shell command that says "press (specified key)"??? Then, I could just write a shell script and run it as a start-up program so that I don't have press F9 whenever log in.

---

### Post by werg on 2008-04-02
> **moonbeam said:**
> 1) Install from the awn testing PPA   [https://launchpad.net/~awn-testing/+archive](https://launchpad.net/~awn-testing/+archive)

2) Remove the Launcher/taskmanager applet.  (chances are awn will crash when you do this)

3) Restart AWN.

4) Add simple-launcher applets.  One per launcher that you would like to use.  Do not use standalone-launcher (that's designed to support tasks management).

5) Drag and drop the desktop files you want to use into the simple-launchers in question.

6) Done.

moonbeam, I've sent you a PM, but you haven't answered yet... maybe you overlooked it? In any case, I installed AWN-test, but there isn't any simple-launcher applet. I have the standalone-launcher applet, yes, but not the simple-launcher one. What am I missing/doing wrong?

---

### Post by moonbeam on 2008-04-02
> **werg said:**
> moonbeam, I've sent you a PM, but you haven't answered yet... maybe you overlooked it? In any case, I installed AWN-test, but there isn't any simple-launcher applet. I have the standalone-launcher applet, yes, but not the simple-launcher one. What am I missing/doing wrong?

Just noticed the PM a few minutes ago...  I did reply :-)

Umm, I've asked gilir (the ppa maintatiner).   He's in the midst of getting a new build ready and simple launcher _should_ appear with the new build.  (it seems the new webapplet has been causing some ppa build issues (bad me)... so there's been a delay)

---


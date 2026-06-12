---
title: "Windows focus and raise behaviour don't stick, Ubuntu 12.10"
date: 2012-11-01
forum: Desktop Environments
---

### Post by -Sparx- on 2012-11-01
After upgrading to 12.10 the focus and raise behaviour accessed through ccsm does not stick through a reboot. I've noticed this on several of my machines. I un-check the "raise on click" box but it resets after reboot.

I've been searching the forums but could not find any posts about this. Is there something I am missing? Is this not done through compiz any more?

Help appreciated!
Thanks

---

### Post by crozierm on 2012-11-19
I'm having the exact same issue. Have you had any luck finding a solution?

---

### Post by -Sparx- on 2012-11-20
No unfortunately not.
I found this post on askubuntu:
[http://askubuntu.com/questions/64605/how-do-i-set-focus-follows-mouse](http://askubuntu.com/questions/64605/how-do-i-set-focus-follows-mouse)
however it only deals with the focus behaviour of the mouse. But for the raise behaviour of windows non of the solutions work.
I installed gconf-editor but the options shown in the post is no longer there for windows.
Gnome-tweak-tools does not have options for raising windows.

It is annoying. I will keep looking but it just seems gone for some reason.

EDIT:
I looked around a bit more on askubuntu and found this post:
[http://askubuntu.com/questions/149576/auto-raise-broken-in-gnome-3-4-1](http://askubuntu.com/questions/149576/auto-raise-broken-in-gnome-3-4-1)
and the solution worked for me.
The tool to use was dconf-editor (seemed installed by default on my machine) and go to 
org>gnome>desktop>wm>preferences
There I could pick edit raise on click. 
(Weird note. The check-box, after a reboot, is reset but the behaviour I want is still ok.)

---

### Post by dapfy on 2012-11-21
> **-Sparx- said:**
> After upgrading to 12.10 the focus and raise behaviour accessed through ccsm does not stick through a reboot.

Actually most of my ccsm settings don't stick after a few reboots.  I have exported them all, and need to reimport them up to 4 times in a row (yes, multiply import!!!) to get them back.  In the file I have among many others

```
[core]

s0_click_to_focus = false
s0_raise_on_click = false
```

This resolves my #1 hate-feature on Windows, and for years it's been a must-have on Linux!  Just now I did a few reimports until it finally worked, and after just 5 minutes it stopped working again.  The funny thing is, various settings break at different times.  E.g. I configured many keybindings, usually the ones in Command dissappear first, whereas viewport navigation lasts a few days, and moving windows among viewports doesn't seem to have been broken before I decided to reimport my settings.

I first adopted Unity in 12/04, and being able to set these things was the minimum that made me accept this environment.  Now it's so broken, I don't know where to go next...

---

### Post by -Sparx- on 2012-11-22
Hmmm... You are right. My solution have reset itself.
I have been toying with the idea to install a Mint desktop environment just to try it out. However I kinda like Unity and have a bit of patience so I will hold on for a while and see if the solution presents itself, or if I could find anything else to try out. I am curious if we are a minority. I would have guessed that there would be a lot of affected users that got annoyed about this to get a quick fix.

PS: What "file" are you talking about?

---

### Post by parminides on 2012-12-06
I have the same problem, but I've been setting/resetting the focus and window raise behavior with dconf-editor (although ccsm is installed on my machine). I'm running 12.10 Unity.

---

### Post by nferris on 2012-12-09
I've been having this problem on a new installation of 12.10

The good news, assuming that it's the same thing, is that there is a bug filed for it and a fix released for 12.04.  The bug says that they are working on a release for 12.10 as well

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1071950](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1071950)

---

### Post by parminides on 2012-12-09
I never had the problem in 12.04.

---

### Post by -Sparx- on 2012-12-19
> **parminides said:**
> I never had the problem in 12.04.

Me neither. I am running 12.04 at work and don't see the same issues. My two Ubuntu machines at home run 12.10 and both have the same issue. The reason I haven't updated at work is this issue as I need less disturbed work-flow there. 

About the filed bug. I didn't have gconf installed on my 12.10 machines at all (I think) before trying to solve the issue so I don't know why gconf settings would be involved at all.

---

### Post by -Sparx- on 2013-03-24
Hi again,
Just looked over the bug report on launchpad and it seems that this should be fixed. However, I still have this problem and was wondering why this may be. Any input on fixing it would be great. 

Thanks

---

### Post by parminides on 2013-05-11
It's still broken for me as well. I put the following command in .bashrc to easily fix it (in 12.10) when it tears up.

```

alias sloppyfocus='gsettings set org.gnome.desktop.wm.preferences auto-raise false && gsettings set org.gnome.desktop.wm.preferences focus-mode sloppy && gsettings set org.gnome.desktop.wm.preferences raise-on-click false'

```

---


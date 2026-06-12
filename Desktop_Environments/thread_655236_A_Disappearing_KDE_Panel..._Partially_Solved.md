---
title: "A Disappearing KDE Panel... Partially Solved"
date: 2008-01-01
forum: Desktop Environments
---

### Post by ytene on 2008-01-01
I may have stumbled across a combination of applications that can at least partially break KDE. In the last 2 days I've observed my KDE Panel [the menu bar at the bottom of the screen that contains the KMenu icon and your running apps] has completely disappeared on at least 2 completely separate occasions.

After 6 weeks + of 100% stable running, my 7.10 [AMD64] system lost it's KPanel on 2 successive days and it's fairly obvious that this is either due to a recent change [none made] or my doing something silly [highly likely]. On each occasion I had the following apps running:

konsole
konqueror [ in file manager mode]
Firefox [2.0.0.11]
gThumb
Quanta
Bluefish
KompoZer

Yes, I'll grant you that **three** HTML editors might seem a little excessive, but I've found that they are each good for different things, and when working with a mix of HTML, PHP and CSS they *can* be more productive. 

However, twice now my KDE KPanel has disappeared with this combination of applications up and running. I suspect there is a toxic combination going on here. Fortunately I found a quick and simple fix that seems to cure the problem.

1. Save all data and close all existing, running applications. [This hasn't been a problem so far].

2. Get to a command prompt. There are various ways to do this, but by far the simplest is to use the key combination ALT+F2 and then ask for konsole by typing that into the command prompt box and hitting enter.

3. By default, you should have been given shell access in your home directory. You can "pwd" to confirm if you like.

4. Now you need to change directories to ./.kde/share/config/

Note that the first level down, the "kde" directory, has a name that begins with a full stop [to make it a hidden file by default]. 

5. In the /home/~your~name/.kde/share/config directory, you should see two files,

[INDENT]kicker_menubarpanelrc
kickeerrc[/INDENT]

that have file names indicating they are associated with the KDE "kicker". Rename this 2 files. In my case I just appended '_suspect' to each file name. 

6. Log out and back in again. You can CTRL-ALT-Backspace to restart X if you like. Anything like that should work. Because Linux and KDE both have a robust design, they detect the absence of these two files from your home directory and automatigically [sic] re-create them for you. 

7. Log in as per normal and you should see your KDE Panel restored. Except that it will have lost any customisation settings that you specified [I always change my KPanel to "Tiny" to maximise desktop space, for example] and any shortcuts that you have added will similarly be gone.

From this moment on your KDE Panel should be back and working as per normal. I have not found the need to restore the 2 suspect files [at least so far] but nor have I completed my investigations to see what, if anything, has been changed in these files. When I have more data I'll post it here in the hope that it might help someone else.

**Important Caveat**
In case you didn't notice, I'm not a KDE developer, just a user who hates being defeated by technology. It's quite possible that the work-around I've suggested here is actually dangerous, causes other problems, is only a temporary solution at best. There is ***nothing*** out there that beats taking lots of regular backups.

If anyone can help me understand the possible root cause of this problem, then I'm definitely interested to learn more...

I hope this helps.

---

### Post by rltw on 2008-04-22
Same problem. Xubuntu 7.10, KDE 3.5> **ytene said:**
> 5. In the /home/~your~name/.kde/share/config directory, you should see two files,

[INDENT]kicker_menubarpanelrc
kickeerrc[/INDENT]The second I have. The first is not to be found on this drive. Tried uninstalling/reinstalling kicker and the associated kde stuff through synaptic, but no dice.

---


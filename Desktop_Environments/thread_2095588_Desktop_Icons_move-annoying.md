---
title: "Desktop Icons move-annoying"
date: 2012-12-17
forum: Desktop Environments
---

### Post by goodbye-windows(tm) on 2012-12-17
Hi everyone.

My desktop icons move around the desktop as if they had a mind of their own. I prefer to keep everything on my desktop, so it has many icons until I clean it up and archive old projects.

But, the icons never stay where I put them!! So, I constantly find myself searching through the files on the desktop to locate the ones I need to open because they aren't where I left them.

I checked Desktop Properties and Desktop Settings, nothing in the setup seems to address this issue.

I also looked through the Settings Manager in various categories that might hold desktop related options, but found nothing.

See attached screenshots, one is the 'before' desktop, after I arranged the icons the way I'd like to have them arranged. The 'next Morning' screenshot shows what the desktop looks like after a boot up the following morning.

Am using 12.04 Xubuntu.

Is there anyway to lock the desktop or make it so the icons don't move unless I move them??

TIA

Art

---

### Post by Elfy on 2012-12-17
As far as I know it's not possible easily.

[You could follow post #2 here - but you need to make file writeable if you want to make changes.]("http://forum.xfce.org/viewtopic.php?id=7597")

---

### Post by goodbye-windows(tm) on 2012-12-17
> **Elfy said:**
> As far as I know it's not possible easily.

[You could follow post #2 here - but you need to make file writeable if you want to make changes.]("http://forum.xfce.org/viewtopic.php?id=7597")

Aaaarrrggghhhhhh.......it sounds like I can't add additional icons once the changes in post #2 are completed. Does it also mean I can't open a file, make changes and then save the updated file back to the desktop?? 

Is this a 12.04 Xubuntu problem only??? Or, do all the Xubuntu versions have this problem???

Surely the developers must know this is an issue::>

Can I lock certain items permanently (such as trash, home, other file systems etc) and then force the remaining files to remain grouped according to their file extension?? Almost any sort of file organization scheme would make the problem much more tolerable.

I have a late model mobo with lots of ram, so Xubuntu is lightning fast-I love the speed. Does Gnome or Unity have the same issue as well? I would not look forward to changing to Gnome though........

TY.

Art

---

### Post by Elfy on 2012-12-17
You could try the script there as well. Might be what you want.

As I said you have to make the file writeable again. I think this is xfce not xubuntu, from what I can see - yes people know. 

I'd have no idea what ubuntu is like in this regard anymore.

---

### Post by LewisTM on 2012-12-17
This is not a normal behavior but something similar has been reported recently. Not sure if this applies to you.
[http://ubuntuforums.org/showthread.php?t=2091787](http://ubuntuforums.org/showthread.php?t=2091787)

Another cause for icon shuffling would be changes in resolution, which force Xfce to rearrange the desktop. Games tend to do that and mess things up.

Locking the icon placement file with chattr +i is a quick and dirty way to prevent that. Press F5 on the desktop to restore your saved placement. It does mean you have to unlock the file every time you make a change to the icon arrangement. Any new item not found in the icon placement file will be placed at the next available upper left slot. This does NOT mean the files on the desktop are locked. The directory ~/Desktop is still fully writable.

I hope you can find the cause of your problem or at least make it less annoying.

Cheers!

---

### Post by goodbye-windows(tm) on 2012-12-17
Hi Lewis,

I do play criticalmass, a shoot 'em space critter game. It does do something to the graphics setting, I can't record video of the game play, can't access the file menu, the upper or lower panel or the desktop and I can't use the Print Screen key to save a capture to the clipboard. Even if I do not play the game in full screen mode, I still can't use the computer for any other purpose unless I quit the game. 

I'll try to evaluate whether the video game play makes the problem.

I don't change the screen resolution often, but I have done some customization of the system to facilitate my less than optimum vision. Maybe one of the changes I made induces this behaviour.

My nephew administers 5 linux systems for his immediate/local family members. All of them use Xubuntu 12.04 also. I asked him if he ever noticed this issue, and he said he'd never had any sort of similar issue. His workspace saves the latest file to the end of the icons on the desktop, and none of his icons move unless he moves them.

TY so much for the info-I appreciate it very much.

Art

---

### Post by goodbye-windows(tm) on 2012-12-18
Ran some tests yesterday and today.

It looks like the criticalmass game is the culprit!!!!! Every time I play criticalmass, the icons on the desktop change. 

I can't make the icons move/change by logging in or out, or by shutting down and restarting or by just rebooting.

I'll mark this one as solved and move my criticalmass game playing to another users account which will be dedicated for playing criticalmass only.

TY to Lewis and to Elfy.

Art

---

### Post by Elfy on 2012-12-18
Glad you got to the bottom of it :)

---

### Post by rnerwein on 2012-12-18
> **goodbye-windows(tm) said:**
> Ran some tests yesterday and today.

It looks like the criticalmass game is the culprit!!!!! Every time I play criticalmass, the icons on the desktop change. 

I can't make the icons move/change by logging in or out, or by shutting down and restarting or by just rebooting.

I'll mark this one as solved and move my criticalmass game playing to another users account which will be dedicated for playing criticalmass only.

TY to Lewis and to Elfy.

Art
hi
what does the red exclamation mark on the upper right corner of your screen in the second screen shot will tell you ( what's the error text ? ). post this message.
cheers

---

### Post by Elfy on 2012-12-18
It's probably not an error but a notification that there are updates available.

---

### Post by goodbye-windows(tm) on 2012-12-18
> what does the red exclamation mark on the upper right corner of your screen in the second screen shot will tell you

It's a notice that I have updates ready to install-I don't have the updates set up to install automatically. So, the update icon stays there until I tell the update manager to install the updates.

---


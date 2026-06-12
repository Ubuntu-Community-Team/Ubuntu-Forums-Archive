---
title: "Screen Saver freezing"
date: 2008-01-13
forum: Desktop Effects &amp; Customization
---

### Post by drew630 on 2008-01-13
Last night I was messing around with the screen saver choices, deciding which one I liked best. I clicked on one called "Braid" and my computer completely freezed up. I restarted it and went back to screen saver window and as soon as it opened back up it froze again (since it was still on Braid). I don't know how the change it and every time the screen saver comes up when my system is idle my computer freezes.

---

### Post by muddymind on 2008-01-13
> **drew630 said:**
> Last night I was messing around with the screen saver choices, deciding which one I liked best. I clicked on one called "Braid" and my computer completely freezed up. I restarted it and went back to screen saver window and as soon as it opened back up it froze again (since it was still on Braid). I don't know how the change it and every time the screen saver comes up when my system is idle my computer freezes.

The same happened to me... 

To solve the problem go to your console and type gconf-editor

There go to apps->gnome-screensaver and edit the field called themes to 'blank-only' (without the '').

That way the screensaver is set to blank screen and doesn't freeze your pc :)

---

### Post by drew630 on 2008-01-13
Sweet.... Thanks!!!

---

### Post by Rodander on 2008-01-13
Thanks for solving a similar problem for me
:)

---

### Post by FuturePilot on 2008-01-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/101943](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/101943) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have the same problem with the Braid screensaver. It only happens with Compiz running so it seems to be a Compiz bug. If it happens and I have to restart X I do
```
metacity --replace
```
before opening the Screensaver Preferences and then change it. Afterwards
```
compiz
```
to start Compiz again.

---

### Post by muddymind on 2008-01-14
> **FuturePilot said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/101943](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/101943) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have the same problem with the Braid screensaver. It only happens with Compiz running so it seems to be a Compiz bug. If it happens and I have to restart X I do
```
metacity --replace
```
before opening the Screensaver Preferences and then change it. Afterwards
```
compiz
```
to start Compiz again.

I tried that but it didn't worked for me... It continued crashing... :( 

The method I mentioned was the only way I could find to change it without crashing... annoying bug indeed...

[]

---

### Post by defenestratos on 2008-01-15
I'm always crashing on the screensavers when I am listening to tunes...I don't have Compiz running or anything. it has crashed in both Xubuntu and Ubuntu.
Any ideas?

---

### Post by FuturePilot on 2008-01-15
> **defenestratos said:**
> I'm always crashing on the screensavers when I am listening to tunes...I don't have Compiz running or anything. it has crashed in both Xubuntu and Ubuntu.
Any ideas?

I'd have to suspect something is wrong with your graphics drivers

---

### Post by defenestratos on 2008-01-16
> **FuturePilot said:**
> I'd have to suspect something is wrong with your graphics drivers

Hmmm. How can I check that and what are my options if they are indeed incompatible? It'd be sweet to have a stable system!

---

### Post by jerrykenny on 2008-01-16
I reckon the screen savers are fairly processor intensive anyway.

Usually i disable the things, . . . . try this, load your cpu monitor (with graphical history), let your pc sit a while to let the screensaver come on . . . . . move the mouse and see what the load on the cpu was.

I'll bet it was pretty busy :)

---

### Post by Robvdl on 2008-01-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/101943](https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/101943) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The problem appears to be a memory leak in Compiz in Gutsy rather than in the Braid screensaver, and a nasty one too. Although the Braid screensaver does trigger it, but only when Compiz is enabled.

If you have your screensaver set to random (the default), and the Braid screensaver kicks in, within minutes, compiz.real will chew up ALL your memory and swap, for me that was 1GB memory, and 1GB swap occupied by just compiz.real within minutes.

This won't crash the computer fully, but it will make it terribly slow. The computer will become practically unusable and appear to have frozen (but not quite). I would have hoped Linux would be able to recover from a crashed program a lot better, but it doesn't seem to cope very well when a program uses up all your RAM, I have experienced this before, Linux just becomes so slow, it's unusable when it runs out of RAM.

Moving the mouse or pressing a key, doesn't seem to be able to get you out of the screensaver either, now matter how much you try to move the mouse, however pressing CTRL+ALT+F1 and logging into a terminal, OR logging in over the LAN via SSH, and typing:

sudo reboot

Should get you out of there. I tried sudo /etc/init.d/gdm restart which will restart Gnome, but the hung compiz remains in RAM and your Gnome session will be terribly slow anyway. I have found rebooting the machine to be the best solutions.

Then, take it OFF random screensaver, so Braid won't kick in again like that!

---

### Post by noremac on 2008-01-28
I ran into this problem as well the other night as I was messing around with the screen savers. I noticed exactly what you mentioned, Rob. It wasn't entirely frozen, just going...ridiculously...slow. Ctrl-Alt-F1 wouldn't even do anything for me though. I had no choice but to reset the computer. Or maybe I just didn't wait long enough. When it came back up, I went back into the Screensaver menu which was still on Braid. I was able to switch it to something else before it froze again though. But it was starting to do so, no doubt. 

-Cameron

---

### Post by erwall on 2008-01-28
I had the same problem, replacing w/xscreensaver solved it for me, no more lockups.

[http://ubuntuforums.org/showthread.php?t=195557](http://ubuntuforums.org/showthread.php?t=195557)

---


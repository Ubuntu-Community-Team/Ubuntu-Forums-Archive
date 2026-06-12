---
title: "Keyboard/typing issues after updating to Ubuntu 18.04.2"
date: 2019-05-28
forum: Desktop Environments
---

### Post by steven43 on 2019-05-28
I recently had a hard drive crash, I was using Ubuntu 16.04.6 - so I reinstalled Ubuntu 18.04.2. Finally got everything mostly restored to the way it was before.

But I'm encountering a really weird and annoying problem.  Sometimes when typing - like when typing up this post - the spacebar seem to stick and when I hit the spacebar it doesn't actually space.  This appears to be preceded by the text that I am typing being underlined as I type. It's really annoying because I can type and be 6 or 7 words after before I notice that the spacebar didn't actually put a space between the words.

I suppose it could be a mechanical keyboard issue... but this keyboard was working fine before 18.04.2 - seems to be an issue with something that Ubuntu 18.04.2 installed or didn't install.

Is this perhaps a known issue with an easy fix?  I haven't found anything in my search that resolves this.

I'm using IceWM as my windows manager (I like simplicity) so I'd really need to know what configuration files to edit rather than through some GUI specific instructions.  I only seem to notice the issue in applications like pluma, Thunderbird, and FireFox. xterm does not appear to be affected by this, but maybe that's because it doesn't have a textarea?

I'm just looking for any possible solutions. It's just really annoying because I never know when the spacebar is going to take and when it is not.

---

### Post by Autodave on 2019-05-28
The first thing that I would do would be took connect another keyboard and see what happens.

---

### Post by steven43 on 2019-05-28
Same thing with a different keyboard.

It doesn't happen all the time. It's just anybody's guess as to when it will happen. But the text being underlined as Itype it is usually a sign that it is going to happen relatively soon.

Perhaps I'm typing too fast for the system to recognize the keys?  I really don't know.

---

### Post by #&amp;thj^% on 2019-05-28
Try this:
```
sudo apt-get install xserver-xorg-input-all
```
You will need to reboot.
And if that still dose not work, go to setting -> **Universal Access -> Typing Assist -> Slow Keys**
>>>And turn off Slow Keys

---

### Post by steven43 on 2019-05-28
Already done the xserver-xorg-input-all and rebooted. That didn't seem to help.

I don't have a "Settings ->Universal Access ..." I'm using IceWM.  What actual binary is that calling?I can run the binary from an xterm. That's typically what I do. That's why I like Icewm.It's just a basic windows manager, and I can run whatever Ineed to by using an xterm or gmrun.

---

### Post by #&amp;thj^% on 2019-05-28
If your not running Gnome, that would have been a good thing to mention right off the get go. ;)
```
sudo apt remove --purge autoremove xserver-xorg-input-all && sudo apt install xserver-xorg-input-all
```
EDIT: I forgot to add:
Fortunately, it&#8217;s quite easy to do.
```

# Install xkbset for managing keyboard options
sudo apt-get install xkbset
# Disable slow-keys
xkbset -sl
# Disable accessibility so slow-keys won't turn back on
xkbset -a
```
Good Luck

---

### Post by steven43 on 2019-05-28
Hmm.

Did all of that.  Issue still appears to be present.  Must be something that Ihave installed that is conflicting with something else. But I do not know what that something might be. Are there any X.org logs stored any where?  Iguess Icould stop lightdm and run X straight from the console, that way errors might be reported on the console.

Issue is just annoying as ****.  Because Inever know when it's going to happen.

---

### Post by #&amp;thj^% on 2019-05-28
This is just a poke in the dark:
```
inxi -G
```
Return the output please.

---

### Post by steven43 on 2019-05-28
[FONT=courier new]Graphics:  Card: Intel 82Q35 Express Integrated Graphics Controller
           Display Server: x11 (X.Org 1.20.1 ) drivers: intel (unloaded: modesetting,fbdev,vesa)
           Resolution: 1280x1024@60.02hz
           OpenGL: renderer: Mesa DRI Intel Q35 version: 1.4 Mesa 18.2.8
[/FONT]
Anything important there?

---

### Post by steven43 on 2019-05-28
Ah. I think I may have had a break through!

Seems to be happening when I'm typing a capital letter. Holding shift + the spacebar doesn't create a space.  Is that a setting or something you are aware of?  Apparently my pinking finger has a slower reaction time than the rest of my fingers and seems to want to stick on the shift key when I'm hitting the space bar. I'm sure my typing method hasn't changed between Ubuntu 16 and Ubuntu 18.  So it's probably a setting some where that needs to be enabled or disabled.

---

### Post by #&amp;thj^% on 2019-05-28
Nope nothing there that will help here, I can't help, but to offer this, Hold the "Left Shift Key" down for about 20 to 30 seconds to see if that helps.

---

### Post by steven43 on 2019-05-28
I'm almost certain now that the issue is the shift key and the space bar.  I had not really made the connection until just now.

I did test this on an Ubuntu 16 box I have here.  Start pluma.  Hold Left Shift + Spacebar and it gives a space.  But here on Ubuntu 18 it does not.  I don't think it's necessarily Ubuntu 18, but maybe a different version of X.org used between Ubuntu 16 and Ubuntu 18 that changed a default setting.

---

### Post by #&amp;thj^% on 2019-05-28
I seem to be fixated on this little problem of yours, can you show me this also please:
```
gsettings list-recursively | grep input-source

```
Example of mine:
```
org.gnome.desktop.input-sources xkb-options @as []
org.gnome.desktop.input-sources mru-sources @a(ss) []
org.gnome.desktop.input-sources show-all-sources false
org.gnome.desktop.input-sources current uint32 0
org.gnome.desktop.input-sources per-window false
org.gnome.desktop.input-sources sources [('xkb', 'us+dvorak')]
org.gnome.desktop.wm.keybindings switch-input-source ['<Super>space', 'XF86Keyboard']
org.gnome.desktop.wm.keybindings switch-input-source-backward ['<Shift><Super>space', '<Shift>XF86Keyboard']
org.cinnamon.desktop.input-sources show-all-sources false
org.cinnamon.desktop.input-sources current uint32 0
org.cinnamon.desktop.input-sources sources @a(ss) []
org.cinnamon.desktop.input-sources xkb-options @as []
org.cinnamon.settings-daemon.peripherals.keyboard input-sources-switcher 'off'

```
Please use code tags for the return back. (See my sig if you don't know how)

---

### Post by steven43 on 2019-05-28
I think I fixed it!

Run [FONT=courier new]uim-pref-gtk[/FONT]

Then under **Global key bindings 1** - there's a **[Global] on** and **[Global] off** ... I have no idea what this is referring to.  Both have "zenkaku-hankaku" listed, I also have no idea what that is.  But they both have Shift Space listed.  Click Edit and remove Shift Space from both.  Now Shift + Space will work in pluma and else where that uses gtk.

I'm not sure if this is actually the issue, or just something I stumbled across that seems to resolve it.  Although I may be still experiencing issues with something else still in Firefox.  Maybe I just need to reboot.

---

### Post by steven43 on 2019-05-28
Problem with Firefox was that I'm running this particular FireFox as another "user" on this system.  You have to run uim-pref-gtk for each of those users that I'm running applications as

[FONT=courier new]sudo -H -u <theuser> uim-pref-gtk[/FONT]

And make the same changes.

The changes appear to be referenced in the file

[FONT=courier new]/home/<thuser>/.uim.d/customs/custom-global-keys1.scm[/FONT]

---

### Post by #&amp;thj^% on 2019-05-28
Well done!

---

### Post by steven43 on 2019-05-28
I figured I might as well detail this as much as possible.  I've got quite a few Ubuntu systems running Ubuntu 16 and those are going to have to eventually be upgraded to Ubuntu 18.  And when that happens, I'll probably run into these same issues.  Maybe I'll find this post and say to myself "that guy is having the exact same issue I'm having" only to realize, that guy is me.

---


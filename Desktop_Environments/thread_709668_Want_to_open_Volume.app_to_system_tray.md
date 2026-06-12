---
title: "Want to open Volume.app to system tray"
date: 2008-02-27
forum: Desktop Environments
---

### Post by jis on 2008-02-27
Hello, can you start volume.app in system tray? I tried it in Xfce using command
```
kstart --tosystray volume.app &
```
but it shows no more than half of its interface there.

---

### Post by jis on 2008-02-27
XChat 2.8.4 gets its tray icon fully shown even if it is about same size. I wonder, whether there is something wrong with kstart or volume.app or Xfce's system tray.

---

### Post by kerry_s on 2008-02-27
huh, why are you trying to run other volume controls in xfce4?
xfce4 has its own> xfce4-mixer

look in synaptics for the xfce4 equivalents you need.

---

### Post by jis on 2008-02-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/xfce4-mixer/+bug/90261](https://bugs.launchpad.net/xfce4-mixer/+bug/90261) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The Xfce's Volume control panel item does not work in my PC: It does not show up after installing. After installinf the item:
```
$ ps -A | grep xfce4-mixer
12094 ?        00:00:00 xfce4-mixer-plu <defunct>
12095 ?        00:00:00 xfce4-mixer-plu <defunct>
```

Additionally Volume.app has quick mute/unmute function.

---

### Post by kerry_s on 2008-02-27
sorry, didn't know that. i do know of a program, i've used on some lite install's, might give that a go.

try this, 
grab this-> [http://www.pcbypaul.com/software/dl/absvolume_1.0-getdeb1_i386.deb](http://www.pcbypaul.com/software/dl/absvolume_1.0-getdeb1_i386.deb)

add a launcher, for the command put> absvolume

---

### Post by jis on 2008-02-28
Thanks, but, it is not as handy as volume.app and GNOME's volume control that I introduce in the launcpad.net thread. I know no other volume control that has as easy mute-unmute as Volume.app.

---

### Post by kerry_s on 2008-02-28
> **jis said:**
> Thanks, but, it is not as handy as volume.app and GNOME's volume control that I introduce in the launcpad.net thread. I know no other volume control that has as easy mute-unmute as Volume.app.

volume.app is a dock app, made for wm's that support docking(ie: fluxbox,openbox,gnustep,etc..) i don't think xfce4 supports dock app's, you can still use it just not docked.

you could skip an app altogether and just make some keyboard short cuts or icons.

example commands:
amixer set PCM toggle  <-mute/unmute
amixer set PCM 3%- unmute  <-volume down
amixer set PCM 3%+ unmute  <-volume up

you can even add a mute toggle and absvolume instead.

i haven't looked for a icon for my mute button yet, so i just got the letter "M"
added with icon pic
anyways here's what mine looks like->

---

### Post by jis on 2008-02-29
The toggle command works fine. I use Master instead of PCM, though. I also tried the volume adjust commands, but I have to press over and over again, one long keypress does not work. Additionally, I couldn't make my laptop's volume up and volume down keys work. They work in GNOME by default. Xfce has bind aumix command to some multimedia keys, but I guess I don't have them. And aumix tells me in terminal: " aumix: SOUND_MIXER_READ_DEVMASK" and does nothing else apparently.

---

### Post by kerry_s on 2008-02-29
you can put those commands in place of the aumix ones. i guess you haven't figured out how to do the keyboard short cuts in xfce4.

if i remember correctly:
press the add
make a name, i used "mine" when i used xfce4, then select it
now you should be able to change the keyboard short cuts to what ever you want.
for instance, for the volume keys just click on the command side, to just change the command.

short cuts are very easy in xfce4, cause it asks you to press the keys you want, no need to look up key codes.
or
you can also just install aumix instead.(sudo apt-get install aumix)

---

### Post by jis on 2008-03-01
Thanks, I already figured out how to add keyboard shortcuts in Xfce, but now I can also edit added ones. I have already installed aumix, but it does not work, like I tried to tell in my previous message. There are aumix shortcuts for XF86AudioMute, XF86AudioLowerVolume and XF86AudioRaiseVolume, but I suppose I don't have such keys. I have toggle mute, raise volume and lower volume key combinations in my laptop's keyboard, but in Xfce's settings it gives empty string when I press such a key combination.

BTW Why did you switch to JWM?

---

### Post by kerry_s on 2008-03-01
i love jwm, it's lighter than anything else, i don't have to add other applications to get simple things like a background or desktop icons, all the settings are in 1 file.

my laptop is only 450mhz 256ram, so i want as low a resource use as i can get. i'm using a debian custom install, built from the base up, i only install what i need and nothing else.
with this setup i can work within 256ram and barely ever go into swap, i have to be doing alot for it to use swap. 

as you can tell i'm still in the process of setting it up, i just did a clean install 3 days ago, still haven't made up my mind on the final look yet.

pic of my current so far->

---

### Post by jis on 2008-03-01
Your project reminds me of [Stem Debian]("http://debian.cante.net/stem/").

I have used JWM in conjunction with Puppy Linux. For Ubuntu I have used e.g. [IceWM]("https://help.ubuntu.com/community/IceWM") which is close to JWM, I think.

There are even lighter WM:s than JWM: [http://debian.cante.net/stem/faq/index.html#can_i_use_different_window_manager](http://debian.cante.net/stem/faq/index.html#can_i_use_different_window_manager)

---

### Post by keteflips on 2008-03-01
In the last XFCE version the systray mixer disapears :confused: bad evolution

---

### Post by jis on 2008-03-01
I suppose it is a panel item rather than a systray item, but maybe there is not big difference. It is almost a year since the bug was reported.

---

### Post by kerry_s on 2008-03-01
> **jis said:**
> Your project reminds me of [Stem Debian]("http://debian.cante.net/stem/").

I have used JWM in conjunction with Puppy Linux. For Ubuntu I have used e.g. [IceWM]("https://help.ubuntu.com/community/IceWM") which is close to JWM, I think.

There are even lighter WM:s than JWM: [http://debian.cante.net/stem/faq/index.html#can_i_use_different_window_manager](http://debian.cante.net/stem/faq/index.html#can_i_use_different_window_manager)


hey, that's pretty good, sounds like i went down the same path. only i made compromises for ease of use.

yeah there are lighter than jwm, but they don't have the features of jwm. with those you have to add other app's to get features equal to a standard desktop, which tends to bloat that lighter wm, with jwm there included, no bloat, no extra applications.

---


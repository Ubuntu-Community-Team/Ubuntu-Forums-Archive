---
title: "Gnome top bar has shrunk"
date: 2020-09-05
forum: Desktop Environments
---

### Post by laserburn2 on 2020-09-05
There was an update a couple weeks ago, I didn't pay attention what was installed back then, but after that I've noticed that Gnome panel on top of the screen has gotten a bit smaller. It's not much, only for about 20% maybe, but all the indicators are a bit smaller now, which is annoying for me, as I wear glasses. I generally like my interface elements a bit bigger, not to strain my eyes. First I wasn't sure if the change was real of I'm just tripping, then I though I'll get used to it, but finally I've decided to consult with others.I think this might have been done to resolve some sort of conflict, in the past it would sometimes happen that indicator does not show the whole text, showing ... on the end, but it no longer does that. 

1. Have you noticed that the Gnome panel has gotten a bit smaller on your Ubuntu 20.04 in a last month or so?

2. Do you know some way to enlarge the panel and it's content? Some gnome extension perhaps?

---

### Post by tea for one on 2020-09-05
[https://extensions.gnome.org/extension/1160/dash-to-panel/](https://extensions.gnome.org/extension/1160/dash-to-panel/) has a field to adjust the height of the top panel.

Plus a plethora of other options.

---

### Post by laserburn2 on 2020-09-05
> **tea for one said:**
> [https://extensions.gnome.org/extension/1160/dash-to-panel/](https://extensions.gnome.org/extension/1160/dash-to-panel/) has a field to adjust the height of the top panel.

Plus a plethora of other options.

I'm using Dash to Dock, I don't think they can coexist.

---

### Post by tea for one on 2020-09-05
Yes, I think that they can co-exist.

For example, if you use Dash to Dock to launch your applications, you ignore the equivalent setting in Dash to Panel.

You'll have to play around a bit with the myriad of settings in both extensions.

However, it's a bit clumsy and I would suggest you temporarily disable Dash to Dock and see if Dash to Panel can fulfil your requirements.

I'm pretty sure this one [https://extensions.gnome.org/extension/2506/taskbar-updated/](https://extensions.gnome.org/extension/2506/taskbar-updated/) can also resize the panels.

A variety of extensions performing similar tasks can lead to conflict but, luckily, the extensions are easy to disable/remove.

Your thread is tagged with **lubuntu**, have you installed more than one Desktop Environment?

---

### Post by kurt18947 on 2020-09-05
Here is an extension that will definitely change the size and color of the top panel plus a bunch of other things like adding a second bottom panel.

'Taskbar 2020'. There is a predecessor called just 'Taskbar' by zpyder on which development has stopped. Taskbar 2020 is I'm pretty sure required for Ubuntu 20.04. Taskbar may work on 18.xx, I don't know if Taskbar 2020 will work on versions earlier then 20.xx or not.

---

### Post by vanadium on 2020-09-06
You are experiencing a current bug in Mutter. See [https://askubuntu.com/questions/1269090/ubuntu-20-04-interface-font-too-small-after-restart-even-with-high-scaling-fact](https://askubuntu.com/questions/1269090/ubuntu-20-04-interface-font-too-small-after-restart-even-with-high-scaling-fact), where you will also find temporary work arounds.

---

### Post by laserburn2 on 2020-09-06
Thank you vanadium, you are right, it's exactly that. Well, since they are trying to fix it, I'll give them time, I mean it's hardly a system breaking bug, just a small but persistent annoyance. Thanks everyone!

---


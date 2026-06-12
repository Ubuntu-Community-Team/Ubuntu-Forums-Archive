---
title: "Disabling Emerald Startup"
date: 2007-12-01
forum: Desktop Effects &amp; Customization
---

### Post by Arlanthir on 2007-12-01
Solution: [Grab this fusion-icon.]("http://gitweb.opencompositing.org/?p=users/crdlb/fusion-icon;a=snapshot;h=HEAD")

I'm in Gutsy Gibbon and I've installed emerald from the repos (with desktop effects active).
Now every time I login I get emerald decorating all my windows.

"Ok" - I thought - "lets find fusion-icon and do what I used to do with beryl."

Sure, I installed fusion-icon and selected Metacity, all worked well. I decided to put fusion-icon in my autostart Sessions list.
Once I restarted, BANG, emerald. Right-click fusion-icon, select window decorator.... and to my amazement, Gtk Window Decorator was on! I clicked emerald, clicked gtk and it finally changed. Reboot, same thing.

I re-checked the Sessions startup in the hope of finding emerald there, nothing.
I re-checked the Advanced Desktop Effects Settings>Window Decorator>command and it was gtk-window-decorator --replace.

It seems that every time I change a setting, it runs the decorator command and emerald goes away, but I don't want to change a setting every time I login.

I searched in the forum and tried the USE_EMERALD="no" method or such, didn't work.

I DON'T want to uninstall Emerald, I just want it to not startup, and let me choose through fusion-icon when I want it to do it's decorating goodness.

---

### Post by santiagoward2000 on 2007-12-01
> **Arlanthir said:**
> I'm in Gutsy Gibbon and I've installed emerald from the repos (with desktop effects active).
Now every time I login I get emerald decorating all my windows.

"Ok" - I thought - "lets find fusion-icon and do what I used to do with beryl."

Sure, I installed fusion-icon and selected Metacity, all worked well. I decided to put fusion-icon in my autostart Sessions list.
Once I restarted, BANG, emerald. Right-click fusion-icon, select window decorator.... and to my amazement, Gtk Window Decorator was on! I clicked emerald, clicked gtk and it finally changed. Reboot, same thing.

I re-checked the Sessions startup in the hope of finding emerald there, nothing.
I re-checked the Advanced Desktop Effects Settings>Window Decorator>command and it was gtk-window-decorator --replace.

It seems that every time I change a setting, it runs the decorator command and emerald goes away, but I don't want to change a setting every time I login.

I searched in the forum and tried the USE_EMERALD="no" method or such, didn't work.

I DON'T want to uninstall Emerald, I just want it to not startup, and let me choose through fusion-icon when I want it to do it's decorating goodness.

Hmm... I don't think this can help, but in my case, all I have to do is select **GTK Window Decorator** from fusion-icon before I turn my computer off. I don't know why this doesn't work for you :confused:

---

### Post by Arlanthir on 2007-12-01
I'll try a newer version of fusion-icon, maybe!
Do you know where I can get that? I can't seem to find the homepage :S

---

### Post by santiagoward2000 on 2007-12-01
> **Arlanthir said:**
> I'll try a newer version of fusion-icon, maybe!
Do you know where I can get that? I can't seem to find the homepage :S

Well, you can download one from here:
[http://ubuntuforums.org/showthread.php?t=502613]("http://ubuntuforums.org/showthread.php?t=502613")
But I'm not sure if it's the lastest version....

---

### Post by Arlanthir on 2007-12-01
I found a good one, I think it works.. I had to compile from source but no problem :P

I'll change this to SOLVED if it does.

---

### Post by santiagoward2000 on 2007-12-01
> **Arlanthir said:**
> I found a good one, I think it works.. I had to compile from source but no problem :P

I'll change this to SOLVED if it does.

That's good to hear!
Could you post the link where you find it?

---

### Post by Arlanthir on 2007-12-01
Sure thing, here you go: [Fusion Icon from Opencompositing.org]("http://gitweb.opencompositing.org/?p=users/crdlb/fusion-icon;a=snapshot;h=HEAD")

I still don't know if it works, I haven't rebooted yet. :P

---

### Post by Arlanthir on 2007-12-01
Yep, all appears to be working now :D

---

### Post by santiagoward2000 on 2007-12-01
> **Arlanthir said:**
> Yep, all appears to be working now :D

THAT'S GOOD! :lolflag:

---

### Post by atomkarinca on 2007-12-01
You could've just typed
```
gtk-window-decorator --replace
```
in "run application". And when you want to switch back to emerald just type
```
emerald --replace
```
it saves the preference and you don't need to install fusion-icon.

---

### Post by Arlanthir on 2007-12-02
I'm not sure it does, but I'll keep it in mind and one of these days I'll try :P
Thanks for the tip!

---


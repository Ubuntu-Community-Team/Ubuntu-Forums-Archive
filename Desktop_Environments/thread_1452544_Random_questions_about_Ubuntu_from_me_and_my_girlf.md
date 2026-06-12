---
title: "Random questions about Ubuntu from me and my girlfriend"
date: 2010-04-12
forum: Desktop Environments
---

### Post by mothergoose729 on 2010-04-12
I just made the permanent switch from windows 7 to Kubuntu, and I forced my girlfriend to change over on her laptop too :P . We are both really happy with it and I don't foresee either of us switching back. I have tried linux many times before and this feels like the right fit... feels good!

Anyway, there a few random question that both of us have that I am sure have simple answers. Flash, video, audio, and everything is working, but I want to fiddle with the power management settings on her laptop and I can't find the setting. I want to do the same on my desktop as well, mostly enabling a time out to sleep mode (suspend to RAM), power management setting on and off power, ect. I have noticed manually causing sleep causes her track pad to stop working... so a fix to that would be nice. 

My girlfriend likes to highlight stuff a lot, and she keeps accidentally clicking into directories. I want to break her of the habit, but she wants to know if there is a way to enable double clicking like in windows. Also, is it possible to change the look of the mouse pointer? 

Lastly I want to configure each desktops environment to act like a seperate computer, meaning that all minimized windows for that desktop and that one only will show, as well widgets and icon and such. This was possible in slackware when I tried it a while ago but I haven't figured it out yet in Kubuntu.

I am probably forgetting some stuff so I may ask more. If anybody has answers to one or more of these please post them :). Thanks a lot!

---

### Post by TheSqueak on 2010-04-12
> **mothergoose729 said:**
> My girlfriend likes to highlight stuff a lot, and she keeps accidentally clicking into directories. I want to break her of the habit, but she wants to know if there is a way to enable double clicking like in windows. Also, is it possible to change the look of the mouse pointer? 

1. System Settings -> Mouse -> General -> Select "Double click to open files and folders"

2. System Settings -> Mouse -> Cursor Theme

(You can find new themes [here](http://kde-look.org/index.php?xcontentmode=36))

---

### Post by TheSqueak on 2010-04-12
> **mothergoose729 said:**
> Lastly I want to configure each desktops environment to act like a seperate computer, meaning that all minimized windows for that desktop and that one only will show, as well widgets and icon and such. This was possible in slackware when I tried it a while ago but I haven't figured it out yet in Kubuntu.

System Settings -> Desktop -> Multiple Desktops -> Check "Different Activity for each desktop"

That should let you have different widgets on each desktop.


Then right click on the task manager and select "task manager settings", and then select "Only show tasks from the current desktop"

---

### Post by rogerpittman on 2010-04-12
Power management settings can be found under **System** --> **Preferences** --> **Power Management**.

---

### Post by mothergoose729 on 2010-04-12
> **TheSqueak said:**
> 1. System Settings -> Mouse -> General -> Select "Double click to open files and folders"

2. System Settings -> Mouse -> Cursor Theme

(You can find new themes [here](http://kde-look.org/index.php?xcontentmode=36))

Thanks, that worked just fine :)

> **TheSqueak said:**
> System Settings -> Desktop -> Multiple Desktops -> Check "Different Activity for each desktop"

That should let you have different widgets on each desktop.


Then right click on the task manager and select "task manager settings", and then select "Only show tasks from the current desktop"

That options doesn't seem to be available in my window. I upgraded from kubuntu 9.04... my terminal says that I am using 9.1 though. Did I forget to upgrade some other part of my core system? 

> **rogerpittman said:**
> Power management settings can be found under **System** --> **Preferences** --> **Power Management**.

The option is not available in the equivalent window in Kubuntu :(.

---

### Post by Dayofswords on 2010-04-12
> My girlfriend likes to highlight stuff a lot, and she keeps accidentally clicking into directories. I want to break her of the habit, but she wants to know if there is a way to enable double clicking like in windows. Also, is it possible to change the look of the mouse pointer?
i don't remember single click?
is this an kubuntu-only feature? since i use normal ubuntu

---

### Post by Untitled_No4 on 2010-04-12
> **Dayofswords said:**
> i don't remember single click?
is this an kubuntu-only feature? since i use normal ubuntu

One click is the KDE default and Kubuntu sticks to them.

---

### Post by Untitled_No4 on 2010-04-12
mothergoose729, I think you're using KDE 4.3 (which is the default for Karmic, 9.10) while TheSqueak seems to be using KDE 4.4. Some options have moved around in 4.4 and if I remember correctly Desktop Activities is one of those things. I suggest you wait for KDE 4.4 (coming up in Lucid at the end of this month) and try again.

In the meantime, if you right click on an empty space on your task manager in the panel, and then choose Task Manager Settings you will be able to select "Only show tasks from the current desktop" and "Only show tasks from the current screen" and you will only see the windows open on each desktop. It doesn't affect the widgets though, which I think is better managed in KDE 4.4

Power Management should be found in System Settings -> Advanced tab -> Power Management or by pressing Alt + F2 and tying power management.

---

### Post by TheSqueak on 2010-04-12
> **Untitled_No4 said:**
> mothergoose729, I think you're using KDE 4.3 (which is the default for Karmic, 9.10) while TheSqueak seems to be using KDE 4.4. Some options have moved around in 4.4 and if I remember correctly Desktop Activities is one of those things. I suggest you wait for KDE 4.4 (coming up in Lucid at the end of this month) and try again.

Yeah, that would explain it :)

/is indeed running 4.4

---

### Post by mothergoose729 on 2010-04-14
> **Untitled_No4 said:**
> mothergoose729, I think you're using KDE 4.3 (which is the default for Karmic, 9.10) while TheSqueak seems to be using KDE 4.4. Some options have moved around in 4.4 and if I remember correctly Desktop Activities is one of those things. I suggest you wait for KDE 4.4 (coming up in Lucid at the end of this month) and try again.

In the meantime, if you right click on an empty space on your task manager in the panel, and then choose Task Manager Settings you will be able to select "Only show tasks from the current desktop" and "Only show tasks from the current screen" and you will only see the windows open on each desktop. It doesn't affect the widgets though, which I think is better managed in KDE 4.4

Power Management should be found in System Settings -> Advanced tab -> Power Management or by pressing Alt + F2 and tying power management.

Thanks a lot that just about fixed everything for me.

---

### Post by sunnykillz on 2010-04-14
i was having same pro but some how i fixed it but now i have a problem that my old desktop is gone.i didnt find my old files.is there any solution for that?.but some of the files are there like i installed some games from repositories and a software of gnuradio grc.it is working but my desktop files are not there.....can anyone help me.or u can guide me where are the old files saved in ubuntu.if they were on desktop.plz help me cuz those were imp files of my project....

---

### Post by Untitled_No4 on 2010-04-14
sunnykillz, you'd be better off starting a new thread with your own description as the subject since your problem is different than that of the original poster and people who know the answer to your problem may not go into this thread.

---


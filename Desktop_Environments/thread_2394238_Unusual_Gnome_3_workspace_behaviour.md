---
title: "Unusual Gnome 3 workspace behaviour"
date: 2018-06-14
forum: Desktop Environments
---

### Post by Drone4four on 2018-06-14
I am experiencing 2 issues with Gnome 3:  

**1.** I cannot create / add workspaces by dragging app windows south (down). I can only create workspaces north-wards. Even in expo mode, I can’t even drag a new terminal window to create a workspaces south.  Previously it’s the reverse, where you can only create workspaces south and not north.  How do I restore this functionality to the way it was before?
**2.** Say I have 5 workspaces. If I close all the windows on workspace 3 , it doesn’t disappear and consolidate like it usually would. Previously workspace 3 would be removed automatically but now the workspace is permanently sitting there empty.  So at the end of my work session, I’ve got 10 empty workspaces.  How do I restore the way Gnome would eliminate workspaces which become empty of app windows?

These two issues kinda throw off my workflow alittle because it disrupts how my brain has come to organize information over the past 8 years of using Gnome 3. Not sure if this is a bug or if there is an obscure  setting somewhere I don't remember changing.

I have a few extensions running but none which affect workspace organization.

Is there any other information I can provide to help you help me?

---

### Post by PaulW2U on 2018-06-14
> **Drone4four said:**
> **2.** Say I have 5 workspaces. If I close all the windows on workspace 3 , it doesn’t disappear and consolidate like it usually would. Previously workspace 3 would be removed automatically but now the workspace is permanently sitting there empty.  So at the end of my work session, I’ve got 10 empty workspaces.
I'm seeing something very similar on my laptop with a second monitor attached. I have a terminal window permanently open on the laptop which acts as the second monitor. If I drag the terminal to the main monitor then the workspace counter resets to show the correct number of open workspaces, previously it would show up to seven without me creating any new ones.

I've yet to track down a bug report and until now haven't come across anyone else seeing the same issue. I'm assuming that you're not running a second monitor as you didn't mention one. Something is different to releases of GNOME Shell prior to 3.28. I don't think it is a setting but more likely a bug for which the cause of new workspaces being created needs to be found.

By the way, intentionally creating new workspaces is not a problem here.

---

### Post by Drone4four on 2018-06-14
> **PaulW2U said:**
> I'm assuming that you're not running a second monitor as you didn't mention one. Something is different to releases of GNOME Shell prior to 3.28. I don't think it is a setting but more likely a bug for which the cause of new workspaces being created needs to be found.I am only have one monitor. No multi-monitor setup here.

> By the way, intentionally creating new workspaces is not a problem here. I can intentionally create new workspaces too however only upwards. Can you create a workspace by moving downwards? I can't.

By the way: In keeping with a discussion I am having on irc, perhaps this information would be helpful:

I am running Ubuntu 18.04 and Gnome 3.28.1. I have Gnome-Tweaks installed and the Dynamic Workspace option is set with a checkmark. It's also worth noting that 3.28 has been running fine since I started using it in April. The issue I describe above began about a week ago. Not sure if it is an issue/bug with the 3.28.1 point release upgrade that came through. Gnome 3.28.2 was released back in May with security and other fixes but Ubuntu downstream official repo maintainers have yet to make it available for download.

---

### Post by PaulW2U on 2018-06-14
> **Drone4four said:**
> I am running Ubuntu 18.04 and Gnome 3.28.1. I have Gnome-Tweaks installed and the Dynamic Workspace option is set with a checkmark. It's also worth noting that 3.28 has been running fine since I Started using it in April. The issue I describe above began about a week ago. Not sure if it an issue/bug with the point release upgrade that came through.
I've been seeing the issue for a while now but mainly on my other installation which is slowly becoming Ubuntu 18.10.

However, this installation which is the same as you have quoted doesn't see the issue as much. Just now while reading your reply I checked a few things out and found that I couldn't create new workspaces at all. I was stuck on just two. I restarted the shell with **Alt+F2, r and enter** and workspace creation returned to normal. Strange.

It seems that having **Terminator** set to "Always on Visible Workspace" may be causing some of the issues here but I'm not convinced it is the sole cause as I can't work out why the number of workspaces seems to increase without me opening any new applications on either monitor.

---


---
title: "how to keep awn above the gnome panel?"
date: 2008-12-01
forum: Desktop Environments
---

### Post by artursm on 2008-12-01
This might sound odd, but I want avant-window-navigator to stay above the gnome default panel (not the taskbar, the panel itself).

The reason is that I want awn, but I also want a couple of functionalities from the gnome panel. Currently the panel is on the left, and the dock is on the bottom. But if I could get both on the bottom, with awn constantly on top, that would be great :)

thanks

---

### Post by Izek on 2008-12-01
What do you need from the panel that AWN doesn't have?

---

### Post by artursm on 2008-12-01
Well, there are a couple of buttons, like the force quit and the disk mounter, and there is the systray and the network monitor. 
And some stuff I just ratter have it tiny in the corner than large and centered (like the trashcan).

---

### Post by realgt on 2008-12-01
i tried doing this but eventually got rid of the panel when i figured out how to get applets to work in awn. i added this to my software sources:

**deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) intrepid main**

you can also add that stuff to the top gnome-panel or double up your gnome-panels on top and have two. (took over way too much real estate for me doing that)

hth

---

### Post by hobo89 on 2008-12-10
In case you may still want it, I found a way to actually keep AWN on top of the panel, a program called Devil's Pie.
> Devil's Pie can be configured to detect windows as they are created, and match the window to a set of rules. If the window matches the rules, it can perform a series of actions on that window. For example, I can make all windows created by X-Chat appear on all workspaces, and the main Gkrellm1 window does not appear in the pager or task list.
It is similar to Compiz's Window Rules, but that would not work for me when trying to get AWN to stay on top of the panel.

So here's how to do it:
Open a terminal.

Install devilspie package:
```
sudo aptitude install devilspie
```

Create a directory to store Devil's Pie scripts:
```
mkdir ~/.devilspie
```

In your file browser go to your home directory (home > [username]) and press "CTRL+h" to view hidden folders and file, go into the ".devilspie" directory.

Create a new file and name it something like "awn.ds".

In this file put in the line:
```
(if (is (application_name) "avant-window-navigator") (above))
```
and save and close.

Run Devil's Pie from the terminal:
> devilspie

To make Devil's Pie run on start up, add it to your Startup Programs in Sessions:
System > Preferences > Sessions, under the Startup Programs tab click Add, give it a name (e.g. Devil's Pie) and in command type "devilspie". Click Add and Close.

When Devil's Pie is running it will check for any windows mentioned in the .ds files and apply the properties to any of those windows already open, and any opened whilst it is running.

If you want to use Devil's Pie for creating rules for other windows, here is a guide for getting started:
[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)
And this guide is a lot more in depth about the expressions and syntax used in the scripts:
[http://live.gnome.org/DevilsPie](http://live.gnome.org/DevilsPie)

Hope this helps.

---

### Post by v1nsai on 2009-09-02
This thread is a little old, but I'm having the same problem in Ubuntu 9.04.  I've used compiz-config settings manager to add awn to the 'Above' category in 'Place Windows' but that didn't work, and I tried using the Devilspie trick as mentioned in this thread, and still awn is covered by the gnome panel.  I still use the gnome panel for a lot of things and I like the way it looks with the rest of my desktop, I just want awn to sit on top darnit >.<

---

### Post by v_ladla on 2011-02-22
> **v1nsai said:**
> This thread is a little old, but I'm having the same problem in Ubuntu 9.04.  I've used compiz-config settings manager to add awn to the 'Above' category in 'Place Windows' but that didn't work, and I tried using the Devilspie trick as mentioned in this thread, and still awn is covered by the gnome panel.  I still use the gnome panel for a lot of things and I like the way it looks with the rest of my desktop, I just want awn to sit on top darnit >.<

I just enabled the window rules in CCSM and entry in Above box as "class=Avant-window-navigator" and that worked.. good luck.

---

### Post by Copper Bezel on 2011-02-22
Out of curiosity, what do you use the Gnome panel for? I'm not trying to talk you out of it, I'm just curious - I mean, this thread was started before AWN got indicator applets and a systray.

Edit: And I just realized that the post I was responding to was as old as the other thing. N/M. = )

---

### Post by Krytarik on 2011-02-23
> **Copper Bezel said:**
> Out of curiosity, what do you use the Gnome panel for? I'm not trying to talk you out of it, I'm just curious - I mean, this thread was started before AWN got indicator applets and a systray.

Edit: And I just realized that the post I was responding to was as old as the other thing. N/M. = )
:lolflag:
I just love it when users resurrect such old threads, this one even twice, and reply to issues which most certainly have been solved long ago!

---

### Post by angel6539 on 2011-02-24
Well, there are a couple of buttons, like the force quit and the disk  mounter, and there is the systray and the network monitor.

---

### Post by Krytarik on 2011-02-24
> **angel6539 said:**
> Well, there are a couple of buttons, like the force quit and the disk  mounter, and there is the systray and the network monitor.
I also need the usual system-monitor applet to monitor the memory usage. But since my machine is apparently to old to run AWN without a considerable increase in response time when switching apps, I can't use AWN anyways.

---

### Post by overdrank on 2011-02-24
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182255&stc=1&d=1296333044[/IMG]

---


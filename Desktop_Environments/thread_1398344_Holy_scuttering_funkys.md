---
title: "Holy scuttering funkys"
date: 2010-02-04
forum: Desktop Environments
---

### Post by ojmc on 2010-02-04
Hi all

Please any help very much appreciated.

Very bad two days. Euphoric about windows finally screwing totally yesterday and did fresh install of Karmic.
Set-up every thing, moved all my files, and then finished with a few aesthetic tweaks.
the final thing i was doing was adding a few extra auto-hide panels and here is where it has all gone haywire.
I set two shrunk auto hide panels on the left of the screen with some short cuts on them and mistakenly put the third on the left too. 
This has led to all panels being frozen and the three new ones mostly hidden.
I have not a clue about using the terminal but have being trying desperately none the less, refering to various threads along the way.

Tried this to no avail
$ ps ax | grep gnome-panel
$ kill -9 (id for gnome panel that shows up)
$ gnome-panel&

and have tried a lot of other things too(not listed because i am running off a live usb right now and am under a lot of pressure to get up and running again for work).

So i am locked out and have not been able to find a way to fix it. Therea few with simular problems on launchpad and here but none of the solutions have fixed this for me.

Is there a way to delete these extra panels from the filesystem now while i am using this liveusb or can someone please tell me how to kill them from in side my desktop.

I don't remember exactly now the wording of it but that "kill panels" command doesn't work.

And one last thing. the last time i logged on i noticed a xterm option for logon. 
I selected this and now every time i reboot it enters xterm AAAAAAHHHHHHHHH.
Does anyone know what i can do.
Please

---

### Post by e.m.fields on 2010-02-16
hey oj - 
Sounds like a bad day.  

I'm in a similar situation, I recently upgraded to Karmic on a new drive since my last one was failing.  Everything dandy, but I managed to kill Gnome by screwing up gnome-panel.  Now every time I log in from GDM, gnome immediately crashes back out to GDM login screen.

I' m in the process of researching solutions right now, aside from a complete reinstall of Karmic, which would mean hours of exhaustive backup, and... but anyways, you don't need to hear all this.

So far, the most promising solution I have read is here: 
[http://ubuntuforums.org/showthread.php?t=1342478&highlight=help%2C+I+ruined+gnome+how+to+reinstall]("http://ubuntuforums.org/showthread.php?t=1342478&highlight=help%2C+I+ruined+gnome+how+to+reinstall")

Basically, 
> **wojox said:**
> CTRL + ALT + F1

```
sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

```
sudo reboot
```

Log back in.

This sounds like it will nuke **ALL** gnome settings. I am going to attempt this now.  

**If it solves your problem, please mark this thread as solved, and go help someone else who is having the same problem.**


Peace,

---


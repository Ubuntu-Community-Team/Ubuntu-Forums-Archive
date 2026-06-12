---
title: "savage 2 how to update"
date: 2010-10-16
forum: Gaming &amp; Leisure
---

### Post by arkbuntu on 2010-10-16
i downloaded savage 2 installed fine ubuntu 32 bit, start game all works fine run practice tutural fine

problem is when i login it updates then close game auto restarts back to menu so i click login again and it downloads same patch must i install patch my self or did i install game wrong  

thx for any help

---

### Post by arkbuntu on 2010-10-16
on savage forum shows a way to by pass the updates but that does not help my problem any.
also does all linux games/ programs have this same problem updating 
 i mean non ubuntu files just basic linux programs
nvr had any problem with ubuntu files

---

### Post by Shazzner on 2010-10-16
I'm having this same problem too. Let me see if I can't find out anything more.

---

### Post by arkbuntu on 2010-10-16
i found solution to problem i am new to linux is probly why
when i go to home user folder i hit ctrl h to show hiddin folder
.savage2 is the folder i needed i was doing all the bypass in savage2 folder
still learning linux but this is confusing using 2 folder and difference is a .
hopefully any one with this problem can learn from my mistakes

---

### Post by Shazzner on 2010-10-24
Just in case it isn't clear the solution is to edit this line in your ~/.savage2/startup.cfg file:
```
SetSave upd_checkForUpdates "True"
```
Change that to "False", save, and restart.

If you're having trouble find the .savage2 folder, remember that if it is a .folder, then it'll remain hidden. Hit Ctrl+H while in your home folder to make all hidden folders appear.

---

### Post by DirtyPC on 2010-10-27
Right.. i'm having the exact same problem, but in the savage2 folder i cant find that file anywhere?!?!?!

---

### Post by Ferrat on 2010-10-27
Have yopu tried running the dedicated server? I know there is some versions that have issues with update on the game client but if you run the dedicated server it should update just fine then just kill it and start the client if I remember correctly :)(

---

### Post by Shazzner on 2010-10-28
> **harrylucas1 said:**
> Right.. i'm having the exact same problem, but in the savage2 folder i cant find that file anywhere?!?!?!

That file is in the **.**savage2 folder. There will be two folders, the savage2 folder and the hidden .savage2 folder.

Go to Places -> Home Folder, then on the keyboard hit Control + H. This makes all hidden folders appear in Nautilus. You should be able to locate the .savage2 folder.

> **Ferrat said:**
> Have yopu tried running the dedicated server? I know there is some versions that have issues with update on the game client but if you run the dedicated server it should update just fine then just kill it and start the client if I remember correctly :)( Good idea! I'll try that later.

I emailed S2Games about this bug, but haven't heard a reply back. Really makes me wish every site had a launchpad-style public bug-tracker.

---

### Post by Rim3nX on 2011-03-06
> **harrylucas1 said:**
> Right.. i'm having the exact same problem, but in the savage2 folder i cant find that file anywhere?!?!?!

Its not in ~/.savage2 folder its in ~/.savage2/game folder

---

### Post by Shazzner on 2011-03-07
I take it from the 6th-month-old bump, this issue still hasn't been fixed? :(

---

### Post by Cookie_monsta on 2011-11-16
I'm gonna necro this thread just to say the issue has finally been taken care off, update now works under linux, the game is still alive and we need more players, and also this thread can be closed now :D

---

### Post by Perfect Storm on 2011-11-16
> **Cookie_monsta said:**
> ...also this thread can be closed now :D

Aye.

---


---
title: "[SOLVED] Need help with assault cube."
date: 2008-10-09
forum: Gaming &amp; Leisure
---

### Post by corrupt_reverend on 2008-10-09
So, I installed assault cube and attempted to play, however, my mouse does not work. SOme times it will work for like 1-10 seconds, but it always stops working. I'm new to linux and have never played this game before. 

Any clue as to what is wrong?


Thanks in advance,
~Rev.

---

### Post by Perfect Storm on 2008-10-09
Try disable Compiz. You can do it with fusion-icon (in the repo). Or by commands;

```
metacity --replace
```

To switch back

```
compiz --replace
```

See if it helps.

---

### Post by corrupt_reverend on 2008-10-09
Um, how exactly do I do that?   

Sorry, I told you I was totally new to all of this. :)

---

### Post by Perfect Storm on 2008-10-09
Fusion Icon;

Open Synaptic Package Manager (System tab ---> Administration ---> Synaptic Package Manager). Search for fusion icon. 
Select it with a right click and mark it "install". Choose "Apply".

Or install it by command -
Open the terminal (Applications tab ---> Accessories ---> terminal)

type (copy/paste)
```
sudo apt-get install fusion-icon
```
Remember to have Synaptic Package Manger and add/remove closed as only one of these apps can run at the time. Also note that Linux is case sensitive when you type commands.


You can now launch Fusion Icon by Application tab ---> System Tools ---> Fusion Icon.
or by this command **fusion-icon**

Now you'll see a notify icon appear. You can right click on it.
You can enable/disable the diffrent engines and decorations.

To disable Compiz you simple choose Metacity. and when you want to enable it choose compiz.


To make Fusion Icon to start at every startup go to System tab ---> Preferences ---> Sessions
or by typing **gnome-session-properties** in the terminal.
Click the "Add" Button.

Name: Fusion Icon
Command: fusion-icon
Comment: whaever you want

---

### Post by corrupt_reverend on 2008-10-10
Thanks AI, that did the trick. :D

---


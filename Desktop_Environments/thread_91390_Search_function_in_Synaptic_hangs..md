---
title: "Search function in Synaptic hangs."
date: 2005-11-17
forum: Desktop Environments
---

### Post by kagashe on 2005-11-17
Hi,

I received Breezy CDs yesterday and installed. I have noticed one probelm.
When I click on Search in Synaptic it hangs and I have to kill the application.
This is preventing me in chosing the required package to download quickly. I have to go through the list and select the package.

kagashe

---

### Post by adwait on 2005-11-17
Maybe quite a useless solution.........but try installing adept, which is a package manager for KDE. It is as good as synaptic, if not better.
```
sudo apt-get install adept
```

ps: do you participate in the rimweb forums?

---

### Post by kagashe on 2005-11-17
[QUOTE=adwait]Maybe quite a useless solution.........but try installing adept, which is a package manager for KDE. It is as good as synaptic, if not better.
```
sudo apt-get install adept
```[/quote]Sorry. I will wait for proper solution.
> 
ps: do you participate in the rimweb forums?Yes. But I visit that forum may be once in fortnight.

kagashe

---

### Post by adwait on 2005-11-17
Hmm.....well try running it from the terminal and then post the errors here. That might help give a clue of the problem.

---

### Post by kagashe on 2005-11-18
[QUOTE=adwait]Hmm.....well try running it from the terminal and then post the errors here. That might help give a clue of the problem.[/QUOTE]Ok. Here it is:> kagashe@mybox:~$ sudo synaptic
Password:

(synaptic:8046): Gdk-WARNING **: locale not supported by Xlib

(synaptic:8046): Gdk-WARNING **: cannot set locale modifiers


(synaptic:8046): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:8046): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

kagashe@mybox:~$I think there is some clue in Gtk-CRITICAL. Please tell me what it is.

kagashe

---

### Post by kagashe on 2005-11-20
Hi,

Well I could not solve the problem but I know the reason now. This is what I did.

I created a "test" user with administrative priviledges. Then I opened Synaptic and typed a package name in the search box and it worked.

The previous user which was giving "Gtk-CRITICAL" error was created in Hoary on separate /home partition which I mounted during Breezy install.

kagashe

---

### Post by kperkins on 2005-11-20
Here's something that I've found that may help.
In your home folder there may be a hidden folder called .aptitude owned by root--mine had an empty cofig file in it.  I changed the name (sudo mv .aptitude .aptitude.bak) and synaptic speeded up dramatically. You can, probably, safely remove this folder, since changing it's name didin't screw anything up for me.

---

### Post by kagashe on 2005-11-20
[QUOTE=kperkins]Here's something that I've found that may help.
In your home folder there may be a hidden folder called .aptitude owned by root--mine had an empty cofig file in it.  I changed the name (sudo mv .aptitude .aptitude.bak) and synaptic speeded up dramatically. You can, probably, safely remove this folder, since changing it's name didin't screw anything up for me.[/QUOTE]Apart from Synaptic I was facing minor problems with other packages as well so I did a fresh install of Breezy after deleting all hidden files (except .evolution .gaim etc which are harmless). I deleted .mozilla also after saving the bookmarks.

Now it is much better.

kagashe

---


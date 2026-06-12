---
title: "[SOLVED] I'm so stupid."
date: 2008-12-15
forum: Desktop Environments
---

### Post by Cadeyrn on 2008-12-15
Using Ubuntu 8.10b with gnome, I've accidentally used the Screen Resolution preferences to make the resolution only on my personal admin account to be 320xsomething, making it too small for absolutely everything. I'm unable to change it back because it's so small, and for some reason I can't resize windows at all.

I'm posting this from /root saying I desperately need help, because I've googled everywhere on how to change it back through the low resolution, through the terminal, through recovery, and even looking on the internet and my hard drive for some kind of file that has all of my preferences on it, editable and saveable. Nothing can be found.

---

### Post by gettinoriginal on 2008-12-15
You should be able to edit your graphics here:  :p

sudo gedit /etc/X11/xorg.conf

---

### Post by RFGunslinger on 2008-12-15
Try switching to tty1 by pressing ctrl+alt+F1.  Login and edit xorg.conf

sudo vi /etc/X11/xorg.conf

Add these lines to your "Screen" section:

> 
SubSection "Display"
		Depth     24
		Modes    "1024x768"
EndSubSection


Then switch back to tty7 (ctrl+alt+F7) and restart X.  Hopefully that will get you back to a point where you can change the resolution from Gnome, and then delete the lines you've just added.

---

### Post by Cadeyrn on 2008-12-15
Well, I had already looked at that file and thought it was for all of the users, but if what you say is true, I'll give it a try. An edit will tell my results.

EDIT: I saw for the first time and decided to try RF's fix first. I just used the whole thing and am about to restart. Man, this is yet another example of Linux's awesomeness: it is ALWAYS easy to solve a problem. That is, unless it involves drivers or entirely destroying your system... XD

---

### Post by Cadeyrn on 2008-12-15
So, I tried what you said, but I can't figure out how to save it and overwrite the old file...

---

### Post by yogo on 2008-12-15
> **Cadeyrn said:**
> So, I tried what you said, but I can't figure out how to save it and overwrite the old file...


You have to use sudo when editing, otherwise you will not be able to save.

---

### Post by Cadeyrn on 2008-12-15
Uhh, I tried using sudo and pressing other letters but it got all messed up and I accidentally exited the editing. I have no idea if it was saved. It said:

```
[1]+ Stopped               sudo vi /etc/X11/.conf
```

And went back to the command prompt, logged into the same account.

ARGH, after further meddling I've made a THIRD swap file. Well, I'm in it and all I have to do is have the changes I've made overwrite the original .conf. How do I do that???

---

### Post by sisco311 on 2008-12-15
1.) try to edit the file with nano:
```
sudo nano /etc/X11/xorg.conf
```
Ctrl+o, Enter to save and Ctrl+x to exit.
(or Ctrl+x, y, Enter to save the file and exit)

or
2.) open the Screen Resolution Preferences

hold down the Alt key, left click anywehre on the window and drag ...

---

### Post by yogo on 2008-12-15
> **Cadeyrn said:**
> Uhh, I tried using sudo and pressing other letters but it got all messed up and I accidentally exited the editing. I have no idea if it was saved. It said:

```
[1]+ Stopped               sudo vi /etc/X11/.conf
```And went back to the command prompt, logged into the same account.

ARGH, after further meddling I've made a THIRD swap file. Well, I'm in it and all I have to do is have the changes I've made overwrite the original .conf. How do I do that???

try 
 sudo gedit /etc/X11/xorg.conf It is a little easier than using vi

---

### Post by elvinatom on 2008-12-15
Do you know how to use the vi text editor?  Is that the problem?

Don't use gedit, that's for graphic output ... do that:

sudo nano /etc/X11/.conf

when done editing, hit <ctl> + o, enter, <ctr> + x

---

### Post by Cadeyrn on 2008-12-15
XD Another thing I love about Linux--multiple ways to solve problems.

I also learned the hard way that nano is way better tha gedit and vi, at least it is in the console.

I'm extremely sure sisco's first suggestion worked, though we won't know for sure until I restart and log into my account...

---

### Post by Cadeyrn on 2008-12-15
AGH! I still don't know for sure if the problem's fixed because suddenly Ubuntu won't start.

More details on the problem + the topic we'll use to discuss it is [here]("http://ubuntuforums.org/showthread.php?p=6376448#post6376448").

EDIT: So, once my startup problem is fixed, I'll start up and simply mark this thread as solved if my resolution problem is fixed. If not, I'll say it didnt work in a new post.

---


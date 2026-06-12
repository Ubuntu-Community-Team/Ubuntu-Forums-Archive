---
title: "Panel does not start at login"
date: 2010-04-15
forum: Desktop Environments
---

### Post by jvbn on 2010-04-15
Hi, I have read that some other users have had this same problem, but the answers given to them were of no help to me at all. 

For some strange reason, my gnome panel does not start up when I log in. I have created a thingy following some instructions that I found in another thread, on which I have to click twice every time I log in in order for the panel to appear. This seems to be related to configuration issue in my user account, because if I create a guest user account, the panel will appear normally. Now if I move my home folder to that account, the panel will not start. 

I believe this has to do with the fact that I installed and then uninstalled compiz, but I am so new to Ubuntu that I have no idea if I may be right or wrong in believing so. 

Does anybody have any idea of why this could be happening and, most importantly, can anybody suggest any solution? 

Many thanks in advance

---

### Post by micio on 2010-04-15
If you don't have a lot of customization in your profile you can try to delete you home (and user) and recreate from the beginning

However try to open a terminal and run 
```
gnome-panel
```
if it starts, then insert that command on session startup :P

---

### Post by jvbn on 2010-04-15
Hi again! Thank you very much for your quick reply. Yes, the panel runs when I enter gnome-pane in a terminal. I will try and find out how to insert that in what you said. Sorry, I am still a beginner, but I am loving Ubuntu and all these little challenges, etc. I do have lots of stuff in my home section, so I will leave deleting it and recreating it as the last resource. 

Again, many thanks. Let's hope your solution works for me.

---

### Post by jvbn on 2010-04-15
Hello, micio. I have followed your advice and it HAS worked. Such a simple solution! Thank you for teaching me something so useful as adding stuff to the session startup applications.

---

### Post by SaintDanBert on 2010-07-05
> **micio said:**
> If you don't have a lot of customization in your profile you can try to delete you home (and user) and recreate from the beginning

However try to open a terminal and run 
```
gnome-panel
```
if it starts, then insert that command on session startup :P


I have items checked in System==>Preferences==>StartupApplications that do not start at login and all attempts to get them to start at login are not successful. These same things will start and run either foreground or background from the command line. They will not start and run automatically at login.

[highlight]QUESTION: Can someone explain (pointer to reading is great) all that happens from the time I press enter for GDM login until my desktop is ready for something useful?[/highlight]

~~~ 0;-Dan

---

### Post by SaintDanBert on 2010-07-05
> **jvbn said:**
> 
...
This seems to be related to configuration issue in my user account, because if I create a guest user account, the panel will appear normally. Now if I move my home folder to that account...


I have user=XXXX who is having troubles.  $HOME=/home/XXXX
I create user=NNNN as a fresh new user.  $HOME=/home/NNNN

I do the following:
```

sudo -i
cd /home
mv  XXXX  TTTT
mv  NNNN  XXXX
mv  TTTT  NNNN
chown -Rv  XXXX:XXXX  XXXX
chown -Rv  NNNN:NNNN  NNNN

```

This should be a swap of $HOME contents such that the new user=NNNN
now has all of the configuration and context that was having troubles
and the existing user=XXXX should have a fresh, new-user desktop without
troubles.

GOTCHA -- user=XXXX still has troubles and user=NNNN does too.

JVBN, does this sound familiar?  Does anyone have a clue?

Stumped,
~~~ 0;-/

---


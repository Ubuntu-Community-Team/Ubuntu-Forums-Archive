---
title: "Completely lost desktop"
date: 2008-10-26
forum: Desktop Environments
---

### Post by JesseMat on 2008-10-26
I am running Xubuntu.

I was messing around with the panel settings. I made a new panel, then right-clicked and selected "move." Then all panels disappeared. I decided to reboot, and, like an idiot, did not unselect "save session." Now everytime I log in, it comes up almost completely blank. I have no panels, no background, no icons, the one thing that pops up is that orange (or whatever its called - it's a calendar). I tried some tips on other forums, the problem is they all want me to press <alt><F2>. This doesn't work.

I was able to run in xfce-safe mode, open a terminal and run

```
xfce4-panel
```

This got it up, but the terminal was in the way (and I'm not sure if accessing settings will do much good), and the only way to reboot (that I know of) is <ctrl><alt><backspace> and when I log back on normally, I'm back to where I started.

Any suggestions? (I'm on a different computer so I'll be able to respond quickly)

---

### Post by JesseMat on 2008-10-26
Completely lost desktop
I am running Xubuntu.

I was messing around with the panel settings. I made a new panel, then right-clicked and selected "move." Then all panels disappeared. I decided to reboot, and, like an idiot, did not unselect "save session." Now everytime I log in, it comes up almost completely blank. I have no panels, no background, no icons, the one thing that pops up is that orange (or whatever its called - it's a calendar). I tried some tips on other forums, the problem is they all want me to press <alt><F2>. This doesn't work.

I was able to run in xfce-safe mode, open a terminal and run

```
xfce4-panel
```

This got it up, but the terminal was in the way (and I'm not sure if accessing settings will do much good), and the only way to reboot (that I know of) is <ctrl><alt><backspace> and when I log back on normally, I'm back to where I started.

Any suggestions? (I'm on a different computer so I'll be able to respond quickly)

---

### Post by ABCC on 2008-10-27
You could start xfce-panel with nohup. From the man page:
     nohup - run a command immune to hangups, with output to a non-tty

In other words you can start a program from a terminal and, when you shut the terminal, it'll keep running.Heres how it works:

```
abcc@ubuntu-desktop:~$ nohup xfce-panel
```

Once you've got it up you may need to tweak your xfce sessions settings to make it restart on login. Alternatively, if you're not hooked on your settings in xfce you can probably solve this by renaming the ~/.xfce4 directory and logging out then in again. 

ABCC

---

### Post by x1a4 on 2008-10-27
Hi,

Log out, remove the following directories: 

~/.config/xfce4/
~/.config/xfce4-session/

then log back in.  This will reset Xfce to default settings, allowing you reconfigure Xfce.

---

### Post by JesseMat on 2008-10-27
The ```
nohup xfce4-panel
```does bring up xfce4. I went to the option to allow xfce4 to manage the desktop and that brought everything together. The problem I have is that when I log out of that session, and back in as normal, nothing has changed. I don't know how to make it stick.

I then attempted to delete those directories, this caused the orange thing to come up in default coloring, but I'm still in the same predicament.

I'm thinking I need some trick to make xfce4 permanent (maybe I'm not logging out correctly).

When I log in under Xscript or xfce session I get nothing but the autostart orange and I have no shortcut functionality that I'm aware of (atleast <alt><F2> does nothing). I can log in under safe terminal, but it appears that any changes I make is not permanent.

---

### Post by JesseMat on 2008-10-27
Woo hoo!! I fixed it! I went to autostart apps and added the panel:

Applications->Settings->Autostarted Applications->Add
Name: Panel / Command: xfce4-panel

All better! I thought it might be something stupid like that... I think this is just Ubuntu's way of trying to teach me this stuff ;)

---

### Post by x1a4 on 2008-10-28
Once you have setup everything to your liking, logout making sure you check the 'Save session for future logins' checkbox in the logout applet.

---

### Post by Bruce M. on 2008-12-28
> **JesseMat said:**
> I am running Xubuntu.

I was messing around with the panel settings. I made a new panel, then right-clicked and selected "move." Then all panels disappeared. I decided to reboot, and, like an idiot, did not unselect "save session." Now everytime I log in, it comes up almost completely blank. I have no panels, no background, no icons, the one thing that pops up is that orange (or whatever its called - it's a calendar). I tried some tips on other forums, the problem is they all want me to press <alt><F2>. This doesn't work.


Strange that [Alt]+[F2] doesn't work
try:
```
xfce4-panel &
```
That should keep it running.

Bruce

---


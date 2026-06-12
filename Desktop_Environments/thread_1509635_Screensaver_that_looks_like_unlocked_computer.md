---
title: "Screensaver that looks like unlocked computer"
date: 2010-06-14
forum: Desktop Environments
---

### Post by madiyaan on 2010-06-14
Hello,

I am currently using gnome-screensaver but can switch over to xscreensaver if that can help me achieve this.

First, my setup: I am using dual monitors with Ubuntu 8.04 with some new packages. 

What I want to achieve: I want pick between one of two things: 
1) I save a screenshot of my screen, and the lock screen should look exactly like that screenshot. No zoom/pan/blur or other effects. It should look like my desktop is unlocked.

2) I want to lock my screen but display my screen's current contents (note this is different from (1) where I use a pre-generated screenshot).

I used gnome-screensaver and used the "pictures folder" screensaver, but it displays the same screenshot on both my monitors (after scaling). So it doesn't look like my desktop at all. Any suggestions on how to achieve (1) or (2). I'd really like to achieve (1).

---

### Post by stinkeye on 2010-06-16
You can use xtrlock.

From man xtrlock....
DESCRIPTION
       xtrlock locks the X server till the user enters their  password
       at the keyboard.

       While  xtrlock  is  running, the mouse and keyboard are grabbed
       and the mouse cursor becomes a padlock.  Output displayed by  X
       programs,  and  windows put up by new X clients, continue to be
       visible, and any new output is displayed normally.

       The mouse and keyboard are returned when the user  types  their
       password,  followed by Enter

---


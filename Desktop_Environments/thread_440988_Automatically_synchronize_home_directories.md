---
title: "Automatically synchronize home directories"
date: 2007-05-12
forum: Desktop Environments
---

### Post by hardrock on 2007-05-12
Hello!

I'm currently working on both a desktop computer and a laptop. I do all synchronization with unison, which works quite fine. Until now, I only kept some specific directories in sync, but now I want to port over my whole home directory to keep gnome settings etc. synchronized.

I have set up a profile for unison which works fine when I run it manually. The only problem is that synchronizing the different .gnome* directories sometimes messes up my current gnome session on the laptop. I thought that the solution would be to synchronize the home directories before login or even before X starts.

And this is where I'm stuck.

I tried writing a shell script in /etc/init.d and adding it via update-rc.d, but as it seems it doesn't work. Unfortunately I don't know much about the boot process, when network is available etc.

Can anyone help me? Any tips how to achieve this or something similar?

---

### Post by SoggyCornflake on 2007-05-12
> **hardrock said:**
> Hello!

I'm currently working on both a desktop computer and a laptop. I do all synchronization with unison, which works quite fine. Until now, I only kept some specific directories in sync, but now I want to port over my whole home directory to keep gnome settings etc. synchronized.

I have set up a profile for unison which works fine when I run it manually. The only problem is that synchronizing the different .gnome* directories sometimes messes up my current gnome session on the laptop. I thought that the solution would be to synchronize the home directories before login or even before X starts.

And this is where I'm stuck.

I tried writing a shell script in /etc/init.d and adding it via update-rc.d, but as it seems it doesn't work. Unfortunately I don't know much about the boot process, when network is available etc.

Can anyone help me? Any tips how to achieve this or something similar?

Would this be a job for **cron?**

Cron is a job scheduler that will run programs specific times.  (It's already doing that on your systems now if they're both Linux OS.  Why not add a script to synchronize your files daily at say 6:00 AM? 

If working with cron sounds intimidating, try one of the GUI apps designed to work with it like Kcron (KDE) or Scheduler (Gnome).

---


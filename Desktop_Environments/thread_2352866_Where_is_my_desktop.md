---
title: "Where is my desktop"
date: 2017-02-16
forum: Desktop Environments
---

### Post by angelo16 on 2017-02-16
Back from vacations, I turn on the computer. 
Xubuntu 16.10 starts, I log in, and there is nothing on the desktop, ? Only the wallpaper is  there.

What the hell have happened ?

I read some posts around, but no success as this one

[http://askubuntu.com/questions/820323/xubuntu-16-04-default-desktop-icons-suddenly-disappeared](http://askubuntu.com/questions/820323/xubuntu-16-04-default-desktop-icons-suddenly-disappeared)


Can someone help me before I shot Ubuntu ?

---

### Post by angelo16 on 2017-02-16
Weird .....
if I go to another machine and log with teamviewer in my own computer I can see my desktop ....

---

### Post by ajgreeny on 2017-02-16
What happens if you use the guest account; do you see a full GUI desktop in that?
Are you also using another file-manager as the poster in your linked post was?

I have in the past added nautilus to my system (Xubuntu) and if I started nautilus my desktop would also no longer show; solved by making nautilus always start with command **nautilus --no-desktop**, if I remember correctly.  I edited the nautilus.desktop file in /usr/share/applications to make that the default launcher for nautilus and the problem disappeared.

---

### Post by angelo16 on 2017-02-16
Hi, I will try to use the guest account and see what happens.

About the Nautilus, no I don't think so. I am a newbie to Xubuntu, and I did not install anything to change the system that was installed in a fresh Install. I tried that command to run Nautilus and it was not detected in my system, so it seems that it is not default for a fresh Xubuntu Install.

---

### Post by Keith_Helms on 2017-02-16
> **angelo16 said:**
> Hi, I will try to use the guest account and see what happens.

About the Nautilus, no I don't think so. I am a newbie to Xubuntu, and I did not install anything to change the system that was installed in a fresh Install. I tried that command to run Nautilus and it was not detected in my system, so it seems that it is not default for a fresh Xubuntu Install.

Nautilus comes with Ubuntu installs, not Xubuntu.  Unless you manually installed it, you would not have it on your Xubuntu system.

Any desktop launchers you created should be in your home directory under a folder named Desktop.  You might also have icons for Trash, home, and any partitions that were mounted unless you turned off displaying those in system settings.

The first thing to check would therefore be does the Desktop folder exist, is anything in it, and does your userid own that folder and its contents.

---


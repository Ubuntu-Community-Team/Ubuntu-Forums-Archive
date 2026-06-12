---
title: "Can't login to my xfce session."
date: 2011-10-31
forum: Desktop Environments
---

### Post by Psycho Game on 2011-10-31
Hello everybody,

I'm working with xfce now because I am a little bit unhappy with the new gnome.
The problem is that I'm not able yet to find my way around a problem I have with xfce.
I did something apparently which broke my xfce session, in which I'm now unable to login.
When I try to login my x-server resets, and then returns to my login screen.
My current version is Xubuntu 11.10.
What I already tried was to reset my xfce session by removing the .xfce folder in .config, but unlike in Gnome this doesn't seem to work in xfce. 
Can anybody help me with this please?

Greetings Jasper

---

### Post by nnn= on 2011-10-31
Hi, I have a similar problem with gnome ([http://ubuntuforums.org/showthread.php?t=1871895](http://ubuntuforums.org/showthread.php?t=1871895)). It happened after fs became corrupted. Would you suggest I try removing some folder? If so, which one?

---

### Post by Psycho Game on 2011-11-01
> **nnn= said:**
> Hi, I have a similar problem with gnome ([http://ubuntuforums.org/showthread.php?t=1871895](http://ubuntuforums.org/showthread.php?t=1871895)). It happened after fs became corrupted. Would you suggest I try removing some folder? If so, which one?

In Gnome what always worked for me was to execute the following command:
[B]rm -rf .gnome .gnome2 .gconf .gconfd .metacity

[/B]This removes all of gnomes settings for you're user account, and when  you try to re-login into you're account Gnome can't find you're settings  anymore and creates new configuration files with default settings. You  can compare it with restoring everything to the settings you had when  you just installed ubuntu. Hopefolly this will work for you. Please let  me know, otherwise I will try to help you in finding a solution.

---

### Post by Psycho Game on 2011-11-01
As for my problem, this has been solved now.
What I did was: enabling the root account on Xubuntu as following.
First I pressed Ctrl - Alt - F1, to get into tty1.
In there I logged in to my user account by login in with my login credentials.
After this I was able to enable the system root account with sudo passwd root.
This command asks you to once fill in you're administrator password, and then lets you enter a password which you will use for you're root account.
After this I logged out in this tty by using the command exit, and went back to tty7 by using Ctrl - Alt - F7. This brings you back to the login screen of xubuntu.
In this screen you can choose to login to another account, in which you have to fill in the username root, and give the password you chose earlier.
This lets you login to a graphical environment again, in which you browse to the folder /home/<username>, and unhide all hidden files by using Ctrl - H.
Next I deleted everything which a dot in front of the file or folder name. Example: <.filename>. **(!!!Please make a backup first, by copying all those files which you are about to delete to a folder, which you call backup for example!!!)**
After this you can restart you're computer, and I was able to log back in again in my own user-account.
**Another thing I want to say at last is: Never use you're root account unless you really don't have another solution, because the root is allowed to do everything on you're computer and can even break you're whole distribution!**

---

### Post by nnn= on 2011-11-01
I moved everything in my home folder, but the error persists as before. It still says usr/lib/config failed sanity check with code 256 and gnome power box is in upper right. I haven't tried to login as root.
There seems to be a file created called .xsession-errors with: ```
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 6: [[: not found
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
mkdtemp: private socket dir: Permission denied
```Tried ```
chmod a+rwx /tmp 
```[http://forums.fedoraforum.org/showthread.php?t=208427](http://forums.fedoraforum.org/showthread.php?t=208427) it worked, but now my nautilus, terminal, and other preferences are gone, gnome top bar icons too. This is after I moved back all the folders into home. I first tried chmod from live cd than rebooted, logged in without moving back folders into home, so it probably created new preferences. But then I used a live cd to move them back and chose replace everything when it asked but my preferences didn't win. How do I restore my settings?

Thanks for helping me.

---

### Post by Psycho Game on 2011-11-02
The settings of you're gnome settings are stored in the folders **.gnome .gnome2 .gconf .gconfd .metacity.** So if you made a backup of these folders, then you have to copy these folders back to you're home folder.
But if one of those configurations broke you're gnome session in the first place, then it will be broken again.
But if I look at you're log output this doesn't seem to be any problem.

Greetings Jasper

---

### Post by nnn= on 2011-11-02
I already moved everything back, without keeping any additional backups, so I can't try and overwrite the folders with backups. But it seems to interpret it like my settings aren't there. I start evolution and it asks me to setup my folders. But if I view ~/.evolution, everything seems to be in order there.

---

### Post by brotherz on 2011-11-02
"[I][QUOTE=Psycho Game;11414453]As for my problem, this has been solved now.
What I did was: enabling the root account on Xubuntu as following.
First I pressed Ctrl - Alt - F1, to get into tty1.
In there I logged in to my user account by login in with my login credentials.
After this I was able to enable the system root account with sudo passwd root.
This command asks you to once fill in you're administrator password, and then lets you enter a password which you will use for you're root account.
After this I logged out in this tty by using the command exit, and went back to tty7 by using Ctrl - Alt - F7. This brings you back to the login screen of xubuntu.
In this screen you can choose to login to another account, in which you have to fill in the username root, and give the password you chose earlier.
This lets you login to a graphical environment again, in which you browse to the folder /home/<username>"[/I]

Thank you so much. I followed this procedure and in my user's home directory consulted the x-session error file, where I learned what file I had broken (it was .profile). I repaired it as root, and after reboot was able to log in as normal.

---


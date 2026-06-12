---
title: "Can't get past login sceen"
date: 2006-08-24
forum: Desktop Environments
---

### Post by Lingyis on 2006-08-24
Hi,
 
  Linux newbie here.  My installation was working perfectly until the recent ill-fated xorg-related update. I updated to the new working xorg as recommended by this forum.  Now for some reason when it boots up it complains of something wrong with the root file system, and asks me to manually run fdsk (is that right?) and fix problems with inodes and what-nots.  So I went ahead and hit "Y" whenever it recommended me so.  Good, I can see the GUI ubuntu login screen after that.

  Unfortunately, when I enter my user name and password, the screen reverts to text screen for a couple seconds, and goes back to the ubuntu welcome screen.  I've googled this but none of the responses helped me.

  I tried to failsafe GNOME and that works, for the most most part, except that when starting up it's got this message about "dbus session service" not started.

  Does anybody know how I can login in to normal GNOME again?  Thanks in advance.

- Victor

---

### Post by soutSA on 2006-08-24
FYI,

I read a thread this morning saying that the there is a problem with the xserver update. I do not know what the sollution for it is, could not find the thread again.

---

### Post by soutSA on 2006-08-24
I think this might help

[http://www.ubuntuforums.org/showthread.php?t=241254&highlight=xserver+update](http://www.ubuntuforums.org/showthread.php?t=241254&highlight=xserver+update)

---

### Post by hraposo on 2006-08-24
When you are in ubuntu you can do:
sudo /usr/sbin/gdmsetup
Then you go to user tab and you active the autologin with your name. Then you don't need do login any more.

---

### Post by ajlar999 on 2006-08-27
I rebooted after doing the update to the xorg-core, then I reloaded nvidia drivers, then rebooted again and got stuck at the login screen as well.

to get around the stuck at login screen, i reloaded the nvidia drivers again and now the login problem is gone. 

The problem i have now is the power management dbus system service is not being started automatically.

But i can log in now so thats cool...

---

### Post by erdalronahi on 2006-08-30
I seem to have a similar problem since the crash. I can also not log into GNOME, it says "dbus session not started". How did you solve that?

---

### Post by harty83 on 2006-08-30
Same deal here.  I actually didn't udpate my xorg-server because of the known issue.  But today, my computer locked up so I had to hard reset.  Now it will not allow me to log in.  It takes the username and password, shows my background for a second, then goes back to the welcome screen.  I've tried logging into the console and updating which I did successfully.  But it still will not allow me to get past the login screen.  I have it set up where it is suppose to automatically log in also but it is not working now.

Help??!!

---

### Post by ajlar999 on 2006-08-30
I reloaded the NVIDIA drivers by pressing "esc" and going to the GRUB menu and selecting the terminal recovery mode which gave me the CLI screen. 

Then I typed startx and it pulled up xserver and from there I could update my NVIDIA drivers I rebooted and then my system was able to get past the login screen.

I was reading somewhere there was an update for the login screen, thats why they were thinking it got messed up...not sure how accurate that is but something happened.

Then to get around the error message that said the dbus system wasn't coming up, 

I went to synaptic and reinstalled the d-bus package...rebooted and everything was back to normal.

---

